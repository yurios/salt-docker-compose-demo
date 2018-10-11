# Get started with SaltStack

This is demo SaltStack cluster set up by `docker-copmose` and consist of
a single master node and two minion nodes.


**How to spin up**

First, build docker images for master and minions:

```bash
$ docker-build
```

Then start containers:

```bash
$ docker-compose up
```

That is it. But let's verify that minions are enrolled into the salt master:

1. Login into salt master container:
    ```bash
    $ docker-compose exec master-container bash
    ```
1. And then ping each minion:
    ```bash
    $ salt '*' test.ping
    ```
    You should see the output where both minions responded with `True`.


**How to generate keys**

The keys for demo purpose are already generated and committed to this repository.
But if you want to generate new one, here is a short guide how to do that:

Generate key pair:

```bash
$ openssl genrsa -out key.pem 2048
```

Extract public key into the separate file

```bash
$ openssl rsa -in key.pem -outform PEM -pubout -out key.pub
```
