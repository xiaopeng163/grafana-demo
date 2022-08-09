# Telegraf + Prometheus + Grafana


### Installation

Install ``Docker`` and ``docker-compose``

```
$ docker version
Client: Docker Engine - Community
 Version:           20.10.14
 API version:       1.41
 Go version:        go1.16.15
 Git commit:        a224086
 Built:             Thu Mar 24 01:48:02 2022
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.14
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.16.15
  Git commit:       87a90dc
  Built:            Thu Mar 24 01:45:53 2022
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.5.11
  GitCommit:        3df54a852345ae127d1fa3092b95168e4a88e2f8
 runc:
  Version:          1.0.3
  GitCommit:        v1.0.3-0-gf46b6ba
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

```
$ docker-compose --version
docker-compose version 1.29.2, build 5becea4c
```
### Start 

```
$ docker-compose up -d
Creating telegraf   ... done
Creating grafana    ... done
Creating prometheus ... done
Creating host1      ... done
$ docker-compose ps
   Name                 Command               State                                   Ports                                 
----------------------------------------------------------------------------------------------------------------------------
grafana      /run.sh                          Up      0.0.0.0:3000->3000/tcp,:::3000->3000/tcp                              
host1        sh -c while true; do sleep ...   Up                                                                            
prometheus   /bin/prometheus --config.f ...   Up      0.0.0.0:9090->9090/tcp,:::9090->9090/tcp                              
telegraf     /entrypoint.sh telegraf -- ...   Up      8092/udp, 8094/tcp, 8125/udp, 0.0.0.0:9273->9273/tcp,:::9273->9273/tcp

```

### Play


Grafana: http://127.0.0.1:3000/dashboards   (username/password, admin/admin)

Prometheus:  http://127.0.0.1:9090/ 

### Stop and clear


```
$ docker-compose stop 
Stopping prometheus ... done
Stopping host1      ... done
Stopping grafana    ... done
Stopping telegraf   ... done

$ docker-compose rm -f
Going to remove prometheus, grafana, host1, telegraf
Removing prometheus ... done
Removing grafana    ... done
Removing host1      ... done
Removing telegraf   ... done
```