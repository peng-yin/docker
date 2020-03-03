## 安装 nginx

```sh

# or nginx:stable-alpine(轻量级的镜像) or nginx:latest(含bin/bash)
docker pull nginx:alpine

# 查看版本
docker -v
docker-compose --version
```

## 运行镜像

```sh
# start
docker run -d -p 80:80 --name nginx nginx:alpine

# or 在docker-compose.yml当前目录
docker-compose up -d

# 查看容器运行状态
docker ps
docker-compose ps
```

- **-p 80:80**: 将容器的 80 端口映射到宿主机的 80 端口上；
- -**d**: 以后台方式运行镜像；
- **--name**: 指定容器的名称为 nginx;

## 配置

复制运行中 nginx 相关配置文件到宿主机的指定路径下：

```sh
# 复制名称为 nginx 容器中 /etc/nginx/nginx.conf 文件夹到宿主机的 /docker/nginx 路径下
docker cp nginx:/etc/nginx/nginx.conf /docker/nginx

# 复制名称为 nginx 容器中 /etc/nginx/conf.d 文件到宿主机的 /docker/nginx 路径下
docker cp nginx:/etc/nginx/conf.d /docker/nginx
```

## 镜像常用命令

```sh

# [镜像名称:版本] 拉取镜像
docker pull

# 镜像列表
docker images

# 删除镜像
docker rmi -f[镜像名称:版本]

# [关键字] 搜索镜像
docker search

# 镜像登陆
docker login

# [镜像名称] 镜像操作记录
docker history

# [镜像名称:版本][新镜像名称:新版本]
docker tag

# [镜像名称:版本] 查看镜像详细
docker inspect

```

## 容器常用命令

```sh

# 停止
docker-compose stop

# 重启
docker-compose restart

# 容器列表(所有容器) 无-a => 运行的
docker ps -a

# 以 bash 命令进入容器内
docker exec -i containerId /bin/bash
docker exec -i containerId /bin/sh
docker-compose exec containerId /bin/sh

# <container_id> 删除容器
docker rm
docker-compose rm nginx

# <container_id> 停止容器
docker stop

#  <container_id> 开启容器
docker start

#  <container_id> 重启容器
docker restart

# <container_id> 查看容器详情
docker inspect

# [容器名称] my_image:v1.0  容器提交为新的镜像
docker commit

# 查看容器日志
docker logs
```

## 简单总结

- dockerfile: 构建镜像

- docker run: 启动容器

- docker-compose: 启动服务