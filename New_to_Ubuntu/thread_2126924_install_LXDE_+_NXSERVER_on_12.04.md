---
title: "install LXDE + NXSERVER on 12.04"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by garycooper on 2013-03-18
[FONT=Helvetica Neue]Hi,[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]I'm trying to install LXDE + NXSERVER on my dedicated server (ubuntu 64 bit 12.04)

[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]I found a way to install NXSERVER[/FONT]

> 
wget [http://64.34.173.142/download/3.5.0/Linux/nxclient_3.5.0-7_amd64.deb](http://64.34.173.142/download/3.5.0/Linux/nxclient_3.5.0-7_amd64.deb) 
wget [http://64.34.173.142/download/3.5.0/Linux/nxnode_3.5.0-9_amd64.deb](http://64.34.173.142/download/3.5.0/Linux/nxnode_3.5.0-9_amd64.deb) 
wget [URL="http://64.34.173.142/download/3.5.0/Linux/AS/nxserver_3.5.0-11_amd64.debdpkg"]http://64.34.173.142/download/3.5.0/Linux/AS/nxserver_3.5.0-11_amd64.deb
dpkg[/URL] -i nxclient_3.5.0-7_amd64.deb 
dpkg -i nxnode_3.5.0-9_amd64.deb 
dpkg -i nxserver_3.5.0-11_amd64.deb[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]found a way too, to install lxde : [/FONT]

> apt-get install lxde[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]but it sounds, both are not linked, i means i'm not sure NXSERVER knows how to start LXDE, cause when i try to start a session through NoMachine, i could only start gnome session (which is not install on my server)[/FONT]
[FONT=Helvetica Neue]Anyway i feel i'm not doing the right thing...

thanks for your help[/FONT]
[FONT=Helvetica Neue]
[/FONT]

---

### Post by sandyd on 2013-03-18
**Moved to Absolute Beginners Section**

---

### Post by garycooper on 2013-03-18
bump

---

### Post by zSeries on 2013-04-13
Desktop Unix & Custom, In Settings "Run the command" /usr/bin/startlubuntu. I also select "New Virtual Desktop" as floating windows are confusing. That works OK with Ubuntu 10.04 LTS connecting to Lubuntu 12.10.

---

