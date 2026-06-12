---
title: "vnc server questions"
date: 2019-11-03
forum: New to Ubuntu
---

### Post by dave219 on 2019-11-03
hello guys:

newbie to linux is asking help here. i am using older release:

user@host:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:            16.04
Codename:    xenial


i have some questions for VNC server on ubuntu:

1) what is the default vncserver?

user@host:$ which vncserver
/usr/bin/vncserver

2) i tried to install tigervnc but i can't find latest tigervnc server. per info [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers), it is only for 14.0.4 LTS:

wget [https://bintray.com/artifact/download/tigervnc/stable/ubuntu-14.04LTS/amd64/tigervncserver_1.6.0-3ubuntu1_amd64.deb](https://bintray.com/artifact/download/tigervnc/stable/ubuntu-14.04LTS/amd64/tigervncserver_1.6.0-3ubuntu1_amd64.deb)
sudo dpkg -i tigervncserver_1.6.0-3ubuntu1_amd64.deb
sudo apt-get -f install

3) cli cmds "sudo apt install tigervnc-standalone-server tigervnc-viewer" doesn't work for 16.04 LTS:

user@host~:$ sudo apt install tigervnc-standalone-server tigervnc-viewer
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tigervnc-standalone-server
E: Unable to locate package tigervnc-viewer

thanks

_dave

---

### Post by The Cog on 2019-11-03
You can see which vncserver is installed (probably tightvnc) with this command:
```
apt search 'vnc.*server' | grep installed
```

I hadn't heard of tigervnc before - I guess your release is too old to include it. I think it was in 18.04 inwards.

---

