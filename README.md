# ReqiireSearch

ReqiireSearch is customized ElasticSearch 2.2.1 which has token-based protected web access.

## Install ReqiireSearch on fresh Ubuntu Server 14.04

First, install Java 8

```

sudo apt-get install python-software-properties -y

sudo add-apt-repository ppa:webupd8team/java -y

sudo apt-get update

sudo apt-get install oracle-java8-installer -y

```

Second, prepare a normal Linux user, for example 'dthoai'

Third, copy ReqiireSearch-binary-2016.02.25-15.28.zip to server, for example, at /home/dthoai/tmp/

Fourth, unzip and copy contents to correct folder

```

cd /home/dthoai/tmp

sudo unzip /home/dthoai/tmp/ReqiireSearch-binary-2016.02.25-15.28.zip

sudo mv /home/dthoai/tmp/opt/reqiiresearch /opt/

```

Fifth, make ReqiireSearch running at startup

```

sudo cp /opt/reqiiresearch/init/reqiiresearch /etc/init.d/

sudo update-rc.d reqiiresearch defaults

```

Sixth, modify configuration file '/opt/reqiiresearch/home/config/reqiiresearch.yml' to set host IP, for example, 10.0.0.211

```

network.host: 10.0.0.211

```

Seventh, reboot server

```

sudo reboot

```

Last, check ReqiireSearch available

```

curl -XGET "http://10.0.0.211:9200/?magic=c3d4756407ea407396883e69f860e3ea8839be2f2d024316b825033d55a67e57"

```

## Manage tokens

Generate random string which can be used as token

```

curl -XGET "http://10.0.0.211:9200/_magic/random

```

Create new token

```

curl -XGET "http://10.0.0.211:9200/_magic/create?magic=c3d4756407ea407396883e69f860e3ea8839be2f2d024316b825033d55a67e57"

```

Delete token, for example, 'abcdefgh'

```

curl -XGET "http://10.0.0.211:9200/_magic/delete/abcdefgh?magic=c3d4756407ea407396883e69f860e3ea8839be2f2d024316b825033d55a67e57"

```

List dynamic added tokens

```

curl -XGET "http://10.0.0.211:9200/_magic/list?magic=c3d4756407ea407396883e69f860e3ea8839be2f2d024316b825033d55a67e57"

```
