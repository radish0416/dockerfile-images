# Dockerfile 安装 Oracle Java 

> 方式一：通过 yum 的方式进行安装
> 
> 注意的是，这种方式等待时间会比较长，因为要从远程进行下载安装。

```bash
FROM centos:7
MAINTAINER LiangGzone "lianggzone@163.com"

RUN yum update -y && \
    curl --insecure --junk-session-cookies --location --remote-name --silent --header "Cookie: oraclelicense=accept-securebackup-cookie"    \ 
    https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.rpm && \
    yum localinstall -y jdk-8u201-linux-x64.rpm && \
    rm jdk-8u201-linux-x64.rpm && \
    yum clean all

ENV JAVA_HOME=/usr/java/jdk1.8.0_201/ \
    LANG=en_US.UTF-8 \
    LC_ALL=en_US.UTF-8
```