---
title: "No free space only 12GB, docker save image failed, size 20GB"
date: 2019-04-19
forum: New to Ubuntu
---

### Post by eurusd on 2019-04-19
docker image size 20 GB
vps size max 38GB
free space max 12GB


on the fly compression also fails


# docker save vnc | gzip > vnc.tgz
Error response from daemon: write /var/lib/docker/tmp/docker-export-202940347/5b2282c8ef7f8d3267c06a639e88e66eaeeffa0e9a5705ba883b047f276c92ed/layer.tar: no space left on device
root@vnc ~ # df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           386M   40M  347M  11% /run
/dev/sda1        38G   25G   12G  69% /
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           386M     0  386M   0% /run/user/0
root@vnc ~ # docker save vnc | 7z > vnc.tgz
Error response from daemon: write /var/lib/docker/tmp/docker-export-160199134/5b2282c8ef7f8d3267c06a639e88e66eaeeffa0e9a5705ba883b047f276c92ed/layer.tar: no space left on device


bzip to another server via ssh fails


docker save vnc | bzip2 | pv | ssh root@xxxxx -p xxxx 'bunzip2 | docker load'


what to do? :/

---

