# docker-cmd
Common Docker's command

#### stop all containers (brute force method):
```shell
$ docker kill $(docker ps -q)
```

#### stop all containers (smooth method):
```shell
$ docker stop $(docker ps -a -q)
```

#### remove all containers:
```shell
$ docker rm $(docker ps -a -q)
```

#### remove all docker images:
```shell
$ docker rmi $(docker images -q)
```

#### remove all docker volumes:
```shell
$ docker volume ls -qf dangling=true | xargs -r docker volume rm
```

#### clear everything unused: 
```shell
$ docker ps -q | xargs -r docker stop ; docker system purge -a
```
###### Note : on macOS using `docker ps -q | xargs docker stop ; docker system prune -a`

#### Remove image of repo/tag is “none”:
```shell
$ docker rmi $(docker image ls | grep "<none>" | awk '{print $3}')
```

#### Remove all containers by image:
```shell
$ docker rm (docker ps -a |grep [IMAGE_NAME] |awk '{print $1}')
```

#### Stop docker compose with special config file:
```shell
$ docker-compose -f [CONFIG_FILE_NAME].yml down -v
```

#### Rebuild and start docker compose with special config file after that detach it:
```shell
docker-compose -f [CONFIG_FILE_NAME].yml up —-build -d
```
