---
layout: post
title: Ubuntu 安装常用软件
---

[Docker](https://docker.com) 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的镜像中，然后发布到任何流行的 Linux或Windows操作系统的机器上。使用 Docker，可以非常容易得实现环境一致性。

[Nginx](http://nginx.org) 是一个高性能的HTTP和反向代理web服务器，同时也提供了IMAP/POP3/SMTP服务。Nignx 非常适合用作静态文件服务器。

[Git](git-scm.com) 是广泛使用的版本控制工具。

Docker，Nginx，Git 都是开发人员必备的工具。以下总结了在 Ubuntu 中安装这些工具的命令。

### 安装 Docker

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor \
    | sudo tee /usr/share/keyrings/docker-archive-keyring.gpg > /dev/null

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```


### 安装 Nginx

```bash
curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor \
    | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list

apt update
apt install nginx
```

### 安装 Git

``` bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```