# docker-rabbitmq-cluster

## Container #1
```
docker run --log-driver=json-file --log-opt max-size=1g --log-opt max-file=3 -v /etc/localtime:/etc/localtime -d -e RABBITMQ_HIPE_COMPILE=1 -e RABBITMQ_VERIFY=1 -e RABBITMQ_FAIL_IF_NO_PEER_CERT=1 -e RABBITMQ_ERLANG_COOKIE='SomeSecretString' -e RABBITMQ_USE_LONGNAME=true -e RABBITMQ_CLUSTER_NODES="{['rabbit@<hostname1>', 'rabbit@hostname2', 'rabbit@<hostnameN>', disc}" --hostname hostname1.some.domain --name hostname1 -p 15672 stachdude/docker-rabbitmq-cluster
```

## Container #2

```
docker run --log-driver=json-file --log-opt max-size=1g --log-opt max-file=3 -v /etc/localtime:/etc/localtime -d -e RABBITMQ_HIPE_COMPILE=1 -e RABBITMQ_VERIFY=1 -e RABBITMQ_FAIL_IF_NO_PEER_CERT=1 -e RABBITMQ_ERLANG_COOKIE='SomeSecretString' -e RABBITMQ_USE_LONGNAME=true -e RABBITMQ_CLUSTER_NODES="{['rabbit@<hostname1.some.domain>', 'rabbit@<hostname2.some.domain>', 'rabbit@<hostnameN.some.domain>', disc}" --hostname hostname2.some.domain --name hostname2 --lik hostname1 stachdude/docker-rabbitmq-cluster
```

##Container #N

```
docker run --log-driver=json-file --log-opt max-size=1g --log-opt max-file=3 -v /etc/localtime:/etc/localtime -d -e RABBITMQ_HIPE_COMPILE=1 -e RABBITMQ_VERIFY=1 -e RABBITMQ_FAIL_IF_NO_PEER_CERT=1 -e RABBITMQ_ERLANG_COOKIE='SomeSecretString' -e RABBITMQ_USE_LONGNAME=true -e RABBITMQ_CLUSTER_NODES="{['rabbit@<hostname1.some.domain>', 'rabbit@<hostname2.some.domain>', 'rabbit@<hostnameN.some.domain>', ram}" --hostname hostnameN.some.domain --name hostnameN --link hostname1 ---link hostname2 stachdude/docker-rabbitmq-cluster
```
