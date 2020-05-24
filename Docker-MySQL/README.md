

[安装MySQL](https://www.jianshu.com/p/75698093defb)

### 首先查看镜像

```shell
docker search mysql
```

### 然后拉去官方镜像

```
docker pull mysql
```

这里可以选择mysql版本 ，在mysql后加--[版本号就可以了]

### 装好后运行对应容器

```
docker run -p 3306:3306 --name mysql \
-v /usr/local/docker/mysql/conf:/etc/mysql \
-v /usr/local/docker/mysql/logs:/var/log/mysql \
-v /usr/local/docker/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=123456 \
-d mysql:5.7.22
```

命令参数：

- `-p 3306:3306`：将容器的3306端口映射到主机的3306端口
- `-v /usr/local/docker/mysql/conf:/etc/mysql`：将主机当前目录下的 conf 挂载到容器的 /etc/mysql
- `-v /usr/local/docker/mysql/logs:/var/log/mysql`：将主机当前目录下的 logs 目录挂载到容器的 /var/log/mysql
- `-v /usr/local/docker/mysql/data:/var/lib/mysql`：将主机当前目录下的 data 目录挂载到容器的 /var/lib/mysql
- `-e MYSQL\_ROOT\_PASSWORD=123456`：初始化root用户的密码
- `-d mysql`：守护态运行

### 查看容器对应状况

```
docker ps
```

## 这里注意，如果第一次安装不成功要删除mysql下的三个文件夹，然后再次安装别的版本。