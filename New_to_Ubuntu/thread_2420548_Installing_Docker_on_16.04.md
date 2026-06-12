---
title: "Installing Docker on 16.04"
date: 2019-06-06
forum: New to Ubuntu
---

### Post by tichman12 on 2019-06-06
I need help installing docker, I get this error message

```
 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
Last login: Tue Jun  4 15:21:21 2019 from 102.164.212.227
root@vps51801:~# sudo apt-get purge docker lxc-docker docker-engine docker.io
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'lxc-docker' is not installed, so not removed
Package 'docker-engine' is not installed, so not removed
Package 'docker' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 185 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up docker-ce (5:18.09.6~3-0~ubuntu-xenial) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/dockerd-ce because link group dockerd is broken
Job for docker.service failed because the control process exited with error code. See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
dpkg: error processing package docker-ce (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@vps51801:~# sudo apt-get install  curl  apt-transport-https ca-certificates software-properties-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
apt-transport-https is already the newest version (1.2.31).
ca-certificates is already the newest version (20170717~16.04.2).
curl is already the newest version (7.47.0-1ubuntu2.13).
software-properties-common is already the newest version (0.96.20.8).
0 upgraded, 0 newly installed, 0 to remove and 185 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up docker-ce (5:18.09.6~3-0~ubuntu-xenial) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/dockerd-ce because link group dockerd is broken
Job for docker.service failed because the control process exited with error code. See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
dpkg: error processing package docker-ce (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by #&amp;thj^% on 2019-06-06
See if this makes things easier:
```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
Now update:
```
sudo apt clean
sudo apt update
```
If your package system is still in working order:
```
sudo apt install docker-ce docker-ce-cli containerd.io
```
The above installs stable version.
Or if you need a specific version:
```
sudo apt install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```
Replacing of course "<VERSION_STRING>" with your needed version.
Thanks deadflowr for the code tags.:)

---

### Post by tichman12 on 2019-06-06
Got this error:

Setting up docker-ce (5:18.09.6~3-0~ubuntu-xenial) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/dockerd-ce because link group dockerd is broken
Job for docker.service failed because the control process exited with error code. See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
dpkg: error processing package docker-ce (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by #&amp;thj^% on 2019-06-06
Thought so, Try this before we go on then:
```

sudo apt remove docker*
sudo apt autoclean
sudo apt autoremove
```
You may have to remove more directory/files here also, but lets first try this.
Now try your install again.

---

### Post by tichman12 on 2019-06-06
Still getting the same error

---

### Post by tichman12 on 2019-06-06
When I try to remove from directory

0 upgraded, 0 newly installed, 2 to remove and 190 not upgraded.
1 not fully installed or removed.
After this operation, 155 MB disk space will be freed.
Do you want to continue? [Y/n] y
Abort.

---

### Post by #&amp;thj^% on 2019-06-06
> **tichman12 said:**
> Still getting the same error
Well you got this really stuck (Joke), Well now we'll give it a harsher push then. ;)
Fist thing again:
```

sudo apt remove --purge docker*
sudo apt autoclean
sudo apt autoremove
```
At this point I always remind for a good backup in place, very very important!!
Now comes the hammer:
```
sudo rm -rf /usr/lib/docker
```
```
sudo rm -rf /etc/docker.service.d
```
Now if were me I would first reboot, before trying the install again.

> **tichman12 said:**
> When I try to remove from directory

0 upgraded, 0 newly installed, 2 to remove and 190 not upgraded.
1 not fully installed or removed.
After this operation, 155 MB disk space will be freed.
Do you want to continue? [Y/n] y
Abort.
What??? Show me the code you used to do that.
Also when asking for help try to be patient, and wait for assistance before adding more harm, to my efforts to help you.

---

### Post by tichman12 on 2019-06-06
Used the code you gave and it aborts

```
root@vps51801:~# sudo apt remove --purge docker*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'docker-engine-cs' for glob 'docker*'
Note, selecting 'docker-compose' for glob 'docker*'
Note, selecting 'docker' for glob 'docker*'
Note, selecting 'docker.io-doc' for glob 'docker*'
Note, selecting 'docker-containerd' for glob 'docker*'
Note, selecting 'docker-engine' for glob 'docker*'
Note, selecting 'docker-registry' for glob 'docker*'
Note, selecting 'docker-runc' for glob 'docker*'
Note, selecting 'docker-doc' for glob 'docker*'
Note, selecting 'docker-ce' for glob 'docker*'
Note, selecting 'docker-ee' for glob 'docker*'
Note, selecting 'docker-ce-cli' for glob 'docker*'
Note, selecting 'docker.io' for glob 'docker*'
Note, selecting 'docker-doc' instead of 'docker.io-doc'
Package 'docker-engine' is not installed, so not removed
Package 'docker-engine-cs' is not installed, so not removed
Package 'docker-ee' is not installed, so not removed
Package 'docker' is not installed, so not removed
Package 'docker-registry' is not installed, so not removed
Package 'docker-compose' is not installed, so not removed
Package 'docker-doc' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
The following packages will be REMOVED:
  docker-ce* docker-ce-cli*
0 upgraded, 0 newly installed, 2 to remove and 190 not upgraded.
1 not fully installed or removed.
After this operation, 155 MB disk space will be freed.
Do you want to continue? [Y/n] y
Abort.
```

---

### Post by #&amp;thj^% on 2019-06-06
Did you continue? if not do so.
EDIT I see you did, Now what dose this show:
```
apt list --upgradable 
```
I guess by now using code tags is out of the question.

---

### Post by tichman12 on 2019-06-06
I continued ended with the abort message again, then listed apps

```
root@vps51801:~# apt list --upgradable
Listing... Done
apache2/xenial-updates,xenial-security 2.4.18-2ubuntu3.10 amd64 [upgradable from: 2.4.18-2ubuntu3.1]
apache2-bin/xenial-updates,xenial-security 2.4.18-2ubuntu3.10 amd64 [upgradable from: 2.4.18-2ubuntu3.1]
apache2-data/xenial-updates,xenial-security 2.4.18-2ubuntu3.10 all [upgradable from: 2.4.18-2ubuntu3.1]
apache2-doc/xenial-updates,xenial-security 2.4.18-2ubuntu3.10 all [upgradable from: 2.4.18-2ubuntu3.1]
apt/xenial-updates 1.2.32 amd64 [upgradable from: 1.2.31]
apt-transport-https/xenial-updates 1.2.32 amd64 [upgradable from: 1.2.31]
apt-utils/xenial-updates 1.2.32 amd64 [upgradable from: 1.2.31]
base-files/xenial-updates 9.4ubuntu4.8 amd64 [upgradable from: 9.4ubuntu4.3]
bind9/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
bind9-host/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
bind9utils/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
binutils/xenial-updates,xenial-security 2.26.1-1ubuntu1~16.04.8 amd64 [upgradable from: 2.26.1-1ubuntu1~16.04.3]
bsdutils/xenial-updates 1:2.27.1-6ubuntu3.7 amd64 [upgradable from: 1:2.27.1-6ubuntu3.1]
busybox-initramfs/xenial-updates,xenial-security 1:1.22.0-15ubuntu1.4 amd64 [upgradable from: 1:1.22.0-15ubuntu1]
cifs-utils/xenial-updates 2:6.4-1ubuntu1.1 amd64 [upgradable from: 2:6.4-1ubuntu1]
coreutils/xenial-updates 8.25-2ubuntu3~16.04 amd64 [upgradable from: 8.25-2ubuntu2]
cracklib-runtime/xenial-updates 2.9.2-1ubuntu1 amd64 [upgradable from: 2.9.2-1build2]
db5.3-util/xenial-updates,xenial-security 5.3.28-11ubuntu0.2 amd64 [upgradable from: 5.3.28-11]
debconf/xenial-updates 1.5.58ubuntu2 all [upgradable from: 1.5.58ubuntu1]
debconf-i18n/xenial-updates 1.5.58ubuntu2 all [upgradable from: 1.5.58ubuntu1]
debconf-utils/xenial-updates 1.5.58ubuntu2 all [upgradable from: 1.5.58ubuntu1]
distro-info-data/xenial-updates,xenial-security 0.28ubuntu0.12 all [upgradable from: 0.28ubuntu0.2]
dpkg/xenial-updates 1.18.4ubuntu1.5 amd64 [upgradable from: 1.18.4ubuntu1.1]
dselect/xenial-updates 1.18.4ubuntu1.5 amd64 [upgradable from: 1.18.4ubuntu1.1]
expat/xenial-updates,xenial-security 2.1.0-7ubuntu0.16.04.3 amd64 [upgradable from: 2.1.0-7ubuntu0.16.04.2]
file/xenial-updates,xenial-security 1:5.25-2ubuntu1.2 amd64 [upgradable from: 1:5.25-2ubuntu1]
gcc-5-base/xenial-updates 5.4.0-6ubuntu1~16.04.11 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
gettext/xenial-updates,xenial-security 0.19.7-2ubuntu3.1 amd64 [upgradable from: 0.19.7-2ubuntu3]
gettext-base/xenial-updates,xenial-security 0.19.7-2ubuntu3.1 amd64 [upgradable from: 0.19.7-2ubuntu3]
gnupg/xenial-updates,xenial-security 1.4.20-1ubuntu3.3 amd64 [upgradable from: 1.4.20-1ubuntu3.1]
gpgv/xenial-updates,xenial-security 1.4.20-1ubuntu3.3 amd64 [upgradable from: 1.4.20-1ubuntu3.1]
ifupdown/xenial-updates 0.8.10ubuntu1.4 amd64 [upgradable from: 0.8.10ubuntu1.1]
init-system-helpers/xenial-updates 1.29ubuntu4 all [upgradable from: 1.29ubuntu3]
initramfs-tools/xenial-updates,xenial-security 0.122ubuntu8.14 all [upgradable from: 0.122ubuntu8.5]
initramfs-tools-bin/xenial-updates,xenial-security 0.122ubuntu8.14 amd64 [upgradable from: 0.122ubuntu8.5]
initramfs-tools-core/xenial-updates,xenial-security 0.122ubuntu8.14 all [upgradable from: 0.122ubuntu8.5]
iproute2/xenial-updates 4.3.0-1ubuntu3.16.04.5 amd64 [upgradable from: 4.3.0-1ubuntu3]
isc-dhcp-client/xenial-updates 4.3.3-5ubuntu12.10 amd64 [upgradable from: 4.3.3-5ubuntu12.4]
isc-dhcp-common/xenial-updates 4.3.3-5ubuntu12.10 amd64 [upgradable from: 4.3.3-5ubuntu12.4]
klibc-utils/xenial-updates 2.0.4-8ubuntu1.16.04.4 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.2]
kmod/xenial-updates 22-1ubuntu5.2 amd64 [upgradable from: 22-1ubuntu4]
ldap-utils/xenial-updates 2.4.42+dfsg-2ubuntu3.5 amd64 [upgradable from: 2.4.42+dfsg-2ubuntu3.1]
less/xenial-updates 481-2.1ubuntu0.2 amd64 [upgradable from: 481-2.1ubuntu0.1]
libapparmor1/xenial-updates,xenial-security 2.10.95-0ubuntu2.11 amd64 [upgradable from: 2.10.95-0ubuntu2.5]
libapt-inst2.0/xenial-updates 1.2.32 amd64 [upgradable from: 1.2.31]
libapt-pkg5.0/xenial-updates 1.2.32 amd64 [upgradable from: 1.2.31]
libasn1-8-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libasprintf0v5/xenial-updates,xenial-security 0.19.7-2ubuntu3.1 amd64 [upgradable from: 0.19.7-2ubuntu3]
libaudit-common/xenial-updates 1:2.4.5-1ubuntu2.1 all [upgradable from: 1:2.4.5-1ubuntu2]
libaudit1/xenial-updates 1:2.4.5-1ubuntu2.1 amd64 [upgradable from: 1:2.4.5-1ubuntu2]
libavahi-client3/xenial-updates,xenial-security 0.6.32~rc+dfsg-1ubuntu2.3 amd64 [upgradable from: 0.6.32~rc+dfsg-1ubuntu2]
libavahi-common-data/xenial-updates,xenial-security 0.6.32~rc+dfsg-1ubuntu2.3 amd64 [upgradable from: 0.6.32~rc+dfsg-1ubuntu2]
libavahi-common3/xenial-updates,xenial-security 0.6.32~rc+dfsg-1ubuntu2.3 amd64 [upgradable from: 0.6.32~rc+dfsg-1ubuntu2]
libbind9-140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libblkid1/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libc-bin/xenial-updates 2.23-0ubuntu11 amd64 [upgradable from: 2.23-0ubuntu4]
libc6/xenial-updates 2.23-0ubuntu11 amd64 [upgradable from: 2.23-0ubuntu4]
libcrack2/xenial-updates 2.9.2-1ubuntu1 amd64 [upgradable from: 2.9.2-1build2]
libcryptsetup4/xenial-updates 2:1.6.6-5ubuntu2.1 amd64 [upgradable from: 2:1.6.6-5ubuntu2]
libcups2/xenial-updates 2.1.3-4ubuntu0.8 amd64 [upgradable from: 2.1.3-4]
libdb5.3/xenial-updates,xenial-security 5.3.28-11ubuntu0.2 amd64 [upgradable from: 5.3.28-11]
libdbus-1-3/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3.1]
libdns-export162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libdns162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libdrm-intel1/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.2]
libdrm-radeon1/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.2]
libdrm2/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.2]
libexpat1/xenial-updates,xenial-security 2.1.0-7ubuntu0.16.04.3 amd64 [upgradable from: 2.1.0-7ubuntu0.16.04.2]
libfdisk1/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libfreetype6/xenial-updates,xenial-security 2.6.1-0.1ubuntu2.3 amd64 [upgradable from: 2.6.1-0.1ubuntu2]
libgcrypt20/xenial-updates,xenial-security 1.6.5-2ubuntu0.5 amd64 [upgradable from: 1.6.5-2ubuntu0.2]
libglib2.0-0/xenial-updates,xenial-security 2.48.2-0ubuntu4.1 amd64 [upgradable from: 2.48.1-1~ubuntu16.04.1]
libgnutls-openssl27/xenial-updates,xenial-security 3.4.10-4ubuntu1.5 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgnutls30/xenial-updates,xenial-security 3.4.10-4ubuntu1.5 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgomp1/xenial-updates 5.4.0-6ubuntu1~16.04.11 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libgssapi-krb5-2/xenial-updates,xenial-security 1.13.2+dfsg-5ubuntu2.1 amd64 [upgradable from: 1.13.2+dfsg-5]
libgssapi3-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libhcrypto4-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libheimbase1-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libheimntlm0-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libhogweed4/xenial-updates,xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libhx509-5-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libicu55/xenial-updates,xenial-security 55.1-7ubuntu0.4 amd64 [upgradable from: 55.1-7]
libidn11/xenial-updates,xenial-security 1.32-3ubuntu1.2 amd64 [upgradable from: 1.32-3ubuntu1.1]
libirs141/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisc-export160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisc160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisccc140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisccfg140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libk5crypto3/xenial-updates,xenial-security 1.13.2+dfsg-5ubuntu2.1 amd64 [upgradable from: 1.13.2+dfsg-5]
libklibc/xenial-updates 2.0.4-8ubuntu1.16.04.4 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.2]
libkmod2/xenial-updates 22-1ubuntu5.2 amd64 [upgradable from: 22-1ubuntu4]
libkrb5-26-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libkrb5-3/xenial-updates,xenial-security 1.13.2+dfsg-5ubuntu2.1 amd64 [upgradable from: 1.13.2+dfsg-5]
libkrb5support0/xenial-updates,xenial-security 1.13.2+dfsg-5ubuntu2.1 amd64 [upgradable from: 1.13.2+dfsg-5]
libldap-2.4-2/xenial-updates 2.4.42+dfsg-2ubuntu3.5 amd64 [upgradable from: 2.4.42+dfsg-2ubuntu3.1]
libldb1/xenial-updates,xenial-security 2:1.1.24-1ubuntu3.1 amd64 [upgradable from: 2:1.1.24-1ubuntu3]
liblwres141/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.14 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libmagic1/xenial-updates,xenial-security 1:5.25-2ubuntu1.2 amd64 [upgradable from: 1:5.25-2ubuntu1]
libmount1/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libnettle6/xenial-updates,xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libnl-3-200/xenial-updates,xenial-security 3.2.27-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2.27-1]
libnl-genl-3-200/xenial-updates,xenial-security 3.2.27-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2.27-1]
libpam-modules/xenial-updates 1.1.8-3.2ubuntu2.1 amd64 [upgradable from: 1.1.8-3.2ubuntu2]
libpam-modules-bin/xenial-updates 1.1.8-3.2ubuntu2.1 amd64 [upgradable from: 1.1.8-3.2ubuntu2]
libpam-runtime/xenial-updates 1.1.8-3.2ubuntu2.1 all [upgradable from: 1.1.8-3.2ubuntu2]
libpam0g/xenial-updates 1.1.8-3.2ubuntu2.1 amd64 [upgradable from: 1.1.8-3.2ubuntu2]
libpci3/xenial-updates 1:3.3.1-1.1ubuntu1.3 amd64 [upgradable from: 1:3.3.1-1.1ubuntu1]
libperl5.22/xenial-updates,xenial-security 5.22.1-9ubuntu0.6 amd64 [upgradable from: 5.22.1-9]
libplymouth4/xenial-updates 0.9.2-3ubuntu13.5 amd64 [upgradable from: 0.9.2-3ubuntu13.1]
libpng12-0/xenial-updates,xenial-security 1.2.54-1ubuntu1.1 amd64 [upgradable from: 1.2.54-1ubuntu1]
libprocps4/xenial-updates,xenial-security 2:3.3.10-4ubuntu2.4 amd64 [upgradable from: 2:3.3.10-4ubuntu2.2]
libpython-stdlib/xenial-updates 2.7.12-1~16.04 amd64 [upgradable from: 2.7.11-1]
libpython2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.4 amd64 [upgradable from: 2.7.12-1ubuntu0~16.04.1]
libpython2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.4 amd64 [upgradable from: 2.7.12-1ubuntu0~16.04.1]
libpython2.7-stdlib/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.4 amd64 [upgradable from: 2.7.12-1ubuntu0~16.04.1]
libpython3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.5 amd64 [upgradable from: 3.5.2-2ubuntu0~16.04.1]
libpython3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.5 amd64 [upgradable from: 3.5.2-2ubuntu0~16.04.1]
libpython3.5-stdlib/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.5 amd64 [upgradable from: 3.5.2-2ubuntu0~16.04.1]
libroken18-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libsasl2-2/xenial-updates 2.1.26.dfsg1-14ubuntu0.1 amd64 [upgradable from: 2.1.26.dfsg1-14build1]
libsasl2-modules-db/xenial-updates 2.1.26.dfsg1-14ubuntu0.1 amd64 [upgradable from: 2.1.26.dfsg1-14build1]
libslang2/xenial-updates 2.3.0-2ubuntu1.1 amd64 [upgradable from: 2.3.0-2ubuntu1]
libsmartcols1/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libsnmp-base/xenial-updates,xenial-security 5.7.3+dfsg-1ubuntu4.2 all [upgradable from: 5.7.3+dfsg-1ubuntu4]
libsnmp30/xenial-updates,xenial-security 5.7.3+dfsg-1ubuntu4.2 amd64 [upgradable from: 5.7.3+dfsg-1ubuntu4]
libsqlite3-0/xenial-updates,xenial-security 3.11.0-1ubuntu1.1 amd64 [upgradable from: 3.11.0-1ubuntu1]
libssl1.0.0/xenial-updates,xenial-security 1.0.2g-1ubuntu4.15 amd64 [upgradable from: 1.0.2g-1ubuntu4.5]
libstdc++6/xenial-updates 5.4.0-6ubuntu1~16.04.11 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.4]
libsystemd0/xenial-updates,xenial-security 229-4ubuntu21.21 amd64 [upgradable from: 229-4ubuntu12]
libtasn1-6/xenial-updates,xenial-security 4.7-3ubuntu0.16.04.3 amd64 [upgradable from: 4.7-3ubuntu0.16.04.1]
libtirpc1/xenial-updates,xenial-security 0.2.5-1ubuntu0.1 amd64 [upgradable from: 0.2.5-1]
libudev1/xenial-updates,xenial-security 229-4ubuntu21.21 amd64 [upgradable from: 229-4ubuntu12]
libuuid1/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libwbclient0/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 amd64 [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
libwind0-heimdal/xenial-updates,xenial-security 1.7~git20150920+dfsg-4ubuntu1.16.04.1 amd64 [upgradable from: 1.7~git20150920+dfsg-4ubuntu1]
libxml2/xenial-updates,xenial-security 2.9.3+dfsg1-1ubuntu0.6 amd64 [upgradable from: 2.9.3+dfsg1-1ubuntu0.1]
linux-base/xenial-updates,xenial-security 4.5ubuntu1~16.04.1 all [upgradable from: 4.0ubuntu1]
locales/xenial-updates 2.23-0ubuntu11 all [upgradable from: 2.23-0ubuntu10]
login/xenial-updates 1:4.2-3.1ubuntu5.4 amd64 [upgradable from: 1:4.2-3.1ubuntu5]
logrotate/xenial-updates 3.8.7-2ubuntu2.16.04.2 amd64 [upgradable from: 3.8.7-2ubuntu2]
makedev/xenial-updates 2.3.1-93ubuntu2~ubuntu16.04.1 all [upgradable from: 2.3.1-93ubuntu1]
mktemp/xenial-updates 8.25-2ubuntu3~16.04 all [upgradable from: 8.25-2ubuntu2]
module-init-tools/xenial-updates 22-1ubuntu5.2 all [upgradable from: 22-1ubuntu4]
mount/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
multiarch-support/xenial-updates 2.23-0ubuntu11 amd64 [upgradable from: 2.23-0ubuntu4]
openssh-client/xenial-updates,xenial-security 1:7.2p2-4ubuntu2.8 amd64 [upgradable from: 1:7.2p2-4ubuntu2.1]
openssh-server/xenial-updates,xenial-security 1:7.2p2-4ubuntu2.8 amd64 [upgradable from: 1:7.2p2-4ubuntu2.1]
openssh-sftp-server/xenial-updates,xenial-security 1:7.2p2-4ubuntu2.8 amd64 [upgradable from: 1:7.2p2-4ubuntu2.1]
openssl/xenial-updates,xenial-security 1.0.2g-1ubuntu4.15 amd64 [upgradable from: 1.0.2g-1ubuntu4.5]
passwd/xenial-updates 1:4.2-3.1ubuntu5.4 amd64 [upgradable from: 1:4.2-3.1ubuntu5]
patch/xenial-updates,xenial-security 2.7.5-1ubuntu0.16.04.1 amd64 [upgradable from: 2.7.5-1]
perl/xenial-updates,xenial-security 5.22.1-9ubuntu0.6 amd64 [upgradable from: 5.22.1-9]
perl-base/xenial-updates,xenial-security 5.22.1-9ubuntu0.6 amd64 [upgradable from: 5.22.1-9]
perl-modules-5.22/xenial-updates,xenial-security 5.22.1-9ubuntu0.6 all [upgradable from: 5.22.1-9]
plymouth/xenial-updates 0.9.2-3ubuntu13.5 amd64 [upgradable from: 0.9.2-3ubuntu13.1]
postfix/xenial-updates 3.1.0-3ubuntu0.3 amd64 [upgradable from: 3.1.0-3]
procmail/xenial-updates,xenial-security 3.22-25ubuntu0.16.04.1 amd64 [upgradable from: 3.22-25]
procps/xenial-updates,xenial-security 2:3.3.10-4ubuntu2.4 amd64 [upgradable from: 2:3.3.10-4ubuntu2.2]
python/xenial-updates 2.7.12-1~16.04 amd64 [upgradable from: 2.7.11-1]
python-crypto/xenial-updates,xenial-security 2.6.1-6ubuntu0.16.04.3 amd64 [upgradable from: 2.6.1-6build1]
python-ldb/xenial-updates,xenial-security 2:1.1.24-1ubuntu3.1 amd64 [upgradable from: 2:1.1.24-1ubuntu3]
python-minimal/xenial-updates 2.7.12-1~16.04 amd64 [upgradable from: 2.7.11-1]
python-samba/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 amd64 [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
python2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.4 amd64 [upgradable from: 2.7.12-1ubuntu0~16.04.1]
python2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.4 amd64 [upgradable from: 2.7.12-1ubuntu0~16.04.1]
python3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.5 amd64 [upgradable from: 3.5.2-2ubuntu0~16.04.1]
python3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.5 amd64 [upgradable from: 3.5.2-2ubuntu0~16.04.1]
rsync/xenial-updates,xenial-security 3.1.1-3ubuntu1.2 amd64 [upgradable from: 3.1.1-3ubuntu1]
rsyslog/xenial-updates 8.16.0-1ubuntu3.1 amd64 [upgradable from: 8.16.0-1ubuntu3]
samba/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 amd64 [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
samba-common/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 all [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
samba-common-bin/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 amd64 [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
samba-libs/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.21 amd64 [upgradable from: 2:4.3.11+dfsg-0ubuntu0.16.04.1]
sasl2-bin/xenial-updates 2.1.26.dfsg1-14ubuntu0.1 amd64 [upgradable from: 2.1.26.dfsg1-14build1]
sensible-utils/xenial-updates,xenial-security 0.0.9ubuntu0.16.04.1 all [upgradable from: 0.0.9]
sharutils/xenial-updates,xenial-security 1:4.15.2-1ubuntu0.1 amd64 [upgradable from: 1:4.15.2-1]
snmp/xenial-updates,xenial-security 5.7.3+dfsg-1ubuntu4.2 amd64 [upgradable from: 5.7.3+dfsg-1ubuntu4]
systemd/xenial-updates,xenial-security 229-4ubuntu21.21 amd64 [upgradable from: 229-4ubuntu12]
systemd-sysv/xenial-updates,xenial-security 229-4ubuntu21.21 amd64 [upgradable from: 229-4ubuntu12]
tcpdump/xenial-updates,xenial-security 4.9.2-0ubuntu0.16.04.1 amd64 [upgradable from: 4.7.4-1ubuntu1]
tzdata/xenial-updates,xenial-security 2019a-0ubuntu0.16.04 all [upgradable from: 2016h-0ubuntu0.16.04]
udev/xenial-updates,xenial-security 229-4ubuntu21.21 amd64 [upgradable from: 229-4ubuntu12]
util-linux/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
uuid-runtime/xenial-updates 2.27.1-6ubuntu3.7 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
vim/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vim-common/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vim-runtime/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 all [upgradable from: 2:7.4.1689-3ubuntu1.1]
wget/xenial-updates,xenial-security 1.17.1-1ubuntu1.5 amd64 [upgradable from: 1.17.1-1ubuntu1.1]
zlib1g/xenial-updates 1:1.2.8.dfsg-2ubuntu4.1 amd64 [upgradable from: 1:1.2.8.dfsg-2ubuntu4]
```

---

### Post by #&amp;thj^% on 2019-06-06
:lolflag:Well now that gives me clue.
Please run:
```
sudo apt upgrade
```
After that's done and complete>>Reboot and let me know how that goes first>>>Before doing anything else please.

---

### Post by tichman12 on 2019-06-08
sorry for the late response, I truly appreciate all the help

encountered this errors while updating

  Process: 5772 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 5772 (code=exited, status=1/FAILURE)

Jun 08 14:31:52 vps51801 systemd[1]: Failed to start Docker Application Con...e.
Jun 08 14:31:52 vps51801 systemd[1]: docker.service: Unit entered failed state.
Jun 08 14:31:52 vps51801 systemd[1]: docker.service: Failed with result 'ex...'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package docker-ce (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up locales (2.23-0ubuntu11) ...
Generating locales (this might take a while)...
Generation complete.

---

### Post by tichman12 on 2019-06-08
only took part of the code seems like other scripts updated just 
fine

---

### Post by #&amp;thj^% on 2019-06-08
Ok let's slow down a bit, please run:
```
sudo apt remove --purge docker-ce
sudo apt autoclean
sudo apt autoremove
```
Now when that completes, show me the return from:
```
sudo apt update && apt list --upgradable
```
I won't be around much longer today, so I'll check back if necessary at a later time.

---

### Post by tichman12 on 2019-06-08
after reboot

```
 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
Last login: Sat Jun  8 15:01:16 2019 from 102.164.212.227
root@vps51801:~#
```

---

### Post by tichman12 on 2019-06-08
sorry ignore the fop message

---

### Post by tichman12 on 2019-06-08
This is the code you requested

```
root@vps51801:~# sudo apt update && apt list --upgradable
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://software.virtualmin.com/vm/6/gpl/apt](http://software.virtualmin.com/vm/6/gpl/apt) virtualmin-xenial InRelease
Hit:3 [http://software.virtualmin.com/vm/6/gpl/apt](http://software.virtualmin.com/vm/6/gpl/apt) virtualmin-universal InRelease
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [109 kB]
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:7 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease [66.2 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [968 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [384 kB]
Fetched 1636 kB in 2s (719 kB/s)
Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:6 and /etc/apt/sources.list:8
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:7 and /etc/apt/sources.list:9
Listing... Done
```

---

### Post by #&amp;thj^% on 2019-06-08
> **tichman12 said:**
> after reboot

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)
Last login: Sat Jun  8 15:01:16 2019 from 102.164.212.227
root@vps51801:~#

Is this the return from "sudo apt update"?
Ok I'll be patient and wait a little longer for your reply's now. :)

---

### Post by #&amp;thj^% on 2019-06-08
Now can you show me this:
```
apt show  docker-ce
```
It would be very helpful to me if you used code tags for this, see my sig to use Code Tags. Thanks.

---

### Post by tichman12 on 2019-06-08
yes

---

### Post by tichman12 on 2019-06-08
```
root@vps51801:~# apt show  docker-ce
Package: docker-ce
Version: 5:18.09.6~3-0~ubuntu-xenial
Priority: optional
Section: admin
Maintainer: Docker <support@docker.com>
Installed-Size: 85.4 MB
Depends: docker-ce-cli, containerd.io (>= 1.2.2-3), iptables, libseccomp2 (>= 2.3.0), libc6 (>= 2.17), libsystemd0
Recommends: aufs-tools, ca-certificates, cgroupfs-mount | cgroup-lite, git, pigz, xz-utils, libltdl7, apparmor
Conflicts: docker (<< 1.5~), docker-engine, docker-engine-cs, docker.io, lxc-docker, lxc-docker-virtual-package
Replaces: docker-engine
Homepage: https://www.docker.com
Download-Size: 17.4 MB
APT-Manual-Installed: yes
APT-Sources: https://download.docker.com/linux/ubuntu xenial/stable amd64 Packages
Description: Docker: the open-source application container engine
 Docker is a product for you to build, ship and run any application as a
 lightweight container
 .
 Docker containers are both hardware-agnostic and platform-agnostic. This means
 they can run anywhere, from your laptop to the largest cloud compute instance and
 everything in between - and they don't require you to use a particular
 language, framework or packaging system. That makes them great building blocks
 for deploying and scaling web apps, databases, and backend services without
 depending on a particular stack or provider.

N: There are 23 additional records. Please use the '-a' switch to see them.

 
```

---

### Post by #&amp;thj^% on 2019-06-08
Every time I get brave here we get a smack on the hand, so lets see what other conflicts crop up with:
```
sudo apt purge docker-engine -s
```
We are doing a dry run here nothing will take place until we remove the safety switch "-s"

---

### Post by tichman12 on 2019-06-08
```
root@vps51801:~# sudo apt purge docker-engine -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'docker-engine' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Conf docker-ce (5:18.09.6~3-0~ubuntu-xenial Docker CE:xenial [amd64])

 
```

---

### Post by #&amp;thj^% on 2019-06-08
It dose not look to me like it un-installed docker-ce but see if this helps any:
```
sudo apt install --fix-broken
```
Show me the return.

---

### Post by tichman12 on 2019-06-08
```
root@vps51801:~# sudo apt install --fix-broken
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up docker-ce (5:18.09.6~3-0~ubuntu-xenial) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/dockerd-ce because link group dockerd is broken
Job for docker.service failed because the control process exited with error code. See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Sat 2019-06-08 15:49:34 EDT; 10ms ago
     Docs: https://docs.docker.com
  Process: 1968 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 1968 (code=exited, status=1/FAILURE)

Jun 08 15:49:34 vps51801 systemd[1]: Failed to start Docker Application Con...e.
Jun 08 15:49:34 vps51801 systemd[1]: docker.service: Unit entered failed state.
Jun 08 15:49:34 vps51801 systemd[1]: docker.service: Failed with result 'ex...'.
Hint: Some lines were ellipsized, use -l to show in full.
dpkg: error processing package docker-ce (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)

 
```

---

### Post by #&amp;thj^% on 2019-06-08
Try:
```
sudo rm -rf /var/lib/docker
```
Now try again with "sudo apt install --fix-broken"
My guess is that some conflicting files from a previous Docker install still exist in that directory, even after uninstalling with Apt.

---

### Post by tichman12 on 2019-06-08
```
root@vps51801:~# sudo rm -rf /var/lib/docker
rm: cannot remove '/var/lib/docker': Device or resource busy

 
```

---

### Post by #&amp;thj^% on 2019-06-08
Yep just as thought, show me this:
```
systemctl status docker.service
```
I have to run now or I'll be late.
See you when I get back.

---

### Post by #&amp;thj^% on 2019-06-08
Still waiting for the the retrun from the above "systemctl status docker.service"
Now this just some info for Docker, the concept of a "service" signifies a resource that represents an abstraction of a bunch of containers. It can exist or not exist, but you can't "run" a service. You can only run containers. Therefore you can't "stop" a service either, but just remove it.

They do not recommend using the standard command `docker stop`. By default, this command sends the `SIGTERM` signal to the Hub process inside the Docker container, then waits for 10 seconds. If Hub does not finish the shutdown within that time period, the `SIGKILL` is sent to the kernel and the Hub process is killed. This may lead to data corruption. To avoid this outcome, specify an appropriate timeout value when using this command. For example, the following command leaves enough time for the Hub service to shut down:
```

docker stop -t 60 <containerId>
```

You can also stop and start the service manually at any moment with the following commands, respectively:
```

sudo service docker.hub stop
sudo service docker.hub start
```
When we finally get this installed proper, Enable starting the service on system boot with the following command:
```

systemctl enable docker.hub
```

---

### Post by tichman12 on 2019-06-09
Morning, not sure your time that side. Here is the code from were we
left off
```
 root@vps51801:~# systemctl status docker.servic                                                                                                                         e
&#9679; docker.service - Docker Application Container
   Loaded: loaded (/lib/systemd/system/docker.s
   Active: failed (Result: start-limit-hit) sin
     Docs: https://docs.docker.com
  Process: 2606 ExecStart=/usr/bin/dockerd -H f
 Main PID: 2606 (code=exited, status=1/FAILURE)

Jun 08 16:07:48 vps51801 systemd[1]: Failed to
Jun 08 16:07:48 vps51801 systemd[1]: docker.ser
Jun 08 16:07:48 vps51801 systemd[1]: docker.ser
Jun 08 16:07:50 vps51801 systemd[1]: docker.ser
Jun 08 16:07:50 vps51801 systemd[1]: Stopped Do
Jun 08 16:07:50 vps51801 systemd[1]: docker.ser
Jun 08 16:07:50 vps51801 systemd[1]: Failed to
Jun 08 16:07:50 vps51801 systemd[1]: docker.ser
Jun 08 16:07:50 vps51801 systemd[1]: docker.ser
lines 1-16/16 (END)...skipping...
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: failed (Result: start-limit-hit) since Sat 2019-06-08 16:07:50 EDT; 10h ago
     Docs: https://docs.docker.com
  Process: 2606 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 2606 (code=exited, status=1/FAILURE)

Jun 08 16:07:48 vps51801 systemd[1]: Failed to start Docker Application Container Engine.
Jun 08 16:07:48 vps51801 systemd[1]: docker.service: Unit entered failed state.
Jun 08 16:07:48 vps51801 systemd[1]: docker.service: Failed with result 'exit-code'.
Jun 08 16:07:50 vps51801 systemd[1]: docker.service: Service hold-off time over, scheduling restart.
Jun 08 16:07:50 vps51801 systemd[1]: Stopped Docker Application Container Engine.
Jun 08 16:07:50 vps51801 systemd[1]: docker.service: Start request repeated too quickly.
Jun 08 16:07:50 vps51801 systemd[1]: Failed to start Docker Application Container Engine.
Jun 08 16:07:50 vps51801 systemd[1]: docker.service: Unit entered failed state.
Jun 08 16:07:50 vps51801 systemd[1]: docker.service: Failed with result 'start-limit-hit'.
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~


```

---

### Post by tichman12 on 2019-06-09
How do I find out the <container id>
to run firs command

---

### Post by #&amp;thj^% on 2019-06-09
Thankfully I'm not required to run any docker containers yet. ;)
See what this outputs:
```
docker images
```
Or even:
```
docker ls
docker ps -a&#8202;
```

---

### Post by tichman12 on 2019-06-09
Greetings

```

root@vps51801:~# docker images
Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running? 
```

---

### Post by #&amp;thj^% on 2019-06-09
Give me about 1 hr or so, I'm  working with one of the devs now.
for what it's worth I'm running into the same issues as you are.
What kernel are your running now:
```
uname -r
```

---

### Post by tichman12 on 2019-06-09
Greetings

```

  
2.6.32-042stab127.2


```

---

### Post by #&amp;thj^% on 2019-06-09
> **tichman12 said:**
> Greetings

```

  
2.6.32-042stab127.2


```

Well I now know what your problem is>>docker-ce needs Version 3.10 or higher of the Linux kernel.

---

### Post by #&amp;thj^% on 2019-06-09
Well I was able to fix mine, and I'm not sure my method will work for you with your kernel version,** but mine went step for step <<<>>> this was important so follow exactly as below:**
```
sudo apt remove --purge docker-ce
sudo apt autoremove
```
Close Terminal and open a New one:
```
sudo apt remove runc ##<<run one line at a time
sudo rm -rf /lib/systemd/system/docker.service
sudo rm -rf /etc/docker
sudo rm -rf /var/lib/docker
sudo rm -rf /run/docker.sock
sudo rm -rf /etc/systemd/system/docker.service.d

```
Now install again (in the same terminal used for the above commands) with:
```
sudo apt install docker-ce
```
You'll see the same error as before, in my case it was a non-issue...**."After a reboot"** we have:

```
sudo service docker status
[sudo] password for me: 
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: e
   Active: active (running) since Sun 2019-06-09 13:56:57 MDT; 3min 52s ago
     Docs: https://docs.docker.com
 Main PID: 1214 (dockerd)
    Tasks: 13
   Memory: 128.1M
   CGroup: /system.slice/docker.service
           &#9492;&#9472;1214 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/contain

Jun 09 13:56:50 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:50.405194
Jun 09 13:56:50 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:50.405216
Jun 09 13:56:50 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:50.405234
Jun 09 13:56:50 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:50.439969
Jun 09 13:56:52 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:52.106339
Jun 09 13:56:52 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:52.443401
Jun 09 13:56:56 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:56.566422
Jun 09 13:56:56 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:56.725624
Jun 09 13:56:57 me-ThinkPad-T430 dockerd[1214]: time="2019-06-09T13:56:57.348075
Jun 09 13:56:57 me-ThinkPad-T430 systemd[1]: Started Docker Application Containe

```
Installed:
```
apt show docker-ce
Package: docker-ce
Version: 5:19.03.0~2.2.rc2-0~ubuntu-disco
Priority: optional
Section: admin
Maintainer: Docker <support@docker.com>
Installed-Size: 107 MB
Depends: docker-ce-cli, containerd.io, iptables, libseccomp2 (>= 2.3.0), libc6 (>= 2.17), libdevmapper1.02.1 (>= 2:1.02.97), libsystemd0
Recommends: aufs-tools, ca-certificates, cgroupfs-mount | cgroup-lite, git, pigz, xz-utils, libltdl7, apparmor
Conflicts: docker (<< 1.5~), docker-engine, docker-engine-cs, docker.io, lxc-docker, lxc-docker-virtual-package
Replaces: docker-engine
Homepage: https://www.docker.com
Download-Size: 22.4 MB
APT-Manual-Installed: yes
APT-Sources: https://download.docker.com/linux/ubuntu disco/test amd64 Packages
Description: Docker: the open-source application container engine
 Docker is a product for you to build, ship and run any application as a
 lightweight container
 .
 Docker containers are both hardware-agnostic and platform-agnostic. This means
 they can run anywhere, from your laptop to the largest cloud compute instance and
 everything in between - and they don't require you to use a particular
 language, framework or packaging system. That makes them great building blocks
 for deploying and scaling web apps, databases, and backend services without
 depending on a particular stack or provider.

N: There are 5 additional records. Please use the '-a' switch to see them.
```
And:
```
apt policy docker-ce
docker-ce:
  Installed: 5:19.03.0~2.2.rc2-0~ubuntu-disco
  Candidate: 5:19.03.0~2.2.rc2-0~ubuntu-disco
  Version table:
 *** 5:19.03.0~2.2.rc2-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages
        100 /var/lib/dpkg/status
     5:19.03.0~1.5.beta5-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages
     5:19.03.0~1.4.beta4-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages
     5:19.03.0~1.3.beta3-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages
     5:19.03.0~1.2.beta2-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages
     5:19.03.0~1.1.beta1-0~ubuntu-disco 500
        500 https://download.docker.com/linux/ubuntu disco/test amd64 Packages

```
***Again if you do this on your own free will, Your Mileage May Vary.***

---

### Post by tichman12 on 2019-06-10
Still not winning

```
root@vps51801:~# sudo service docker status
&#9679; docker.service - LSB: Create lightweight, portable, self-sufficient containers
   Loaded: loaded (/etc/init.d/docker; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2019-06-10 03:08:21 EDT; 2min 16
     Docs: man:systemd-sysv-generator(8)
  Process: 233 ExecStart=/etc/init.d/docker start (code=exited, status=1/FAILURE

Jun 10 03:08:21 vps51801 docker[233]: mount: wrong fs type, bad option, bad supe
Jun 10 03:08:21 vps51801 docker[233]:        missing codepage or helper program,
Jun 10 03:08:21 vps51801 docker[233]:        In some cases useful info is found
Jun 10 03:08:21 vps51801 docker[233]:        dmesg | tail or so.
Jun 10 03:08:21 vps51801 docker[233]: rmdir: failed to remove 'cpuset': Read-onl
Jun 10 03:08:21 vps51801 docker[233]: mkdir: cannot create directory 'cpu': Read
Jun 10 03:08:21 vps51801 systemd[1]: docker.service: Control process exited, cod
Jun 10 03:08:21 vps51801 systemd[1]: Failed to start LSB: Create lightweight, po
Jun 10 03:08:21 vps51801 systemd[1]: docker.service: Unit entered failed state.
Jun 10 03:08:21 vps51801 systemd[1]: docker.service: Failed with result 'exit-co 
```

---

### Post by #&amp;thj^% on 2019-06-10
Your getting caught up with a couple of bad configs calling it to quickly>>ie:"Loaded: loaded (/etc/init.d/docker; bad; vendor preset: enabled)" and if you followed my instructions exactly, this is just not going to work as it should on your current system.
And from what I can see I'm guessing your using "/etc/init.d/" instead of systemd as mine shows ie: "Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor preset: disabled)"
If possible I would encourage you to upgrade or re-install to 18.04, for both a higher version of the linux kernel, and better support for systemd services.
I never asked why you are running kernel **2.6.32-042stab127.2**, and I guess you have a reason but this is not going to give you any warm and fuzzy feelings here. :(
Granted docker is a bit of problem installing but it should be doable with a proper environment. (Kernel and OS)
I also have noticed that when using a "VPN" the first start of docker will fail, until you disconnect from the VPN, then start docker and a restart of your VPN.(This only has to be done once)
I have now been able to install docker on All my linux installs. (Arch, Ubuntu, Fedora, and Some proprietary OS's etc)
And out of curiosity did you reload the daemon:
```
sudo systemctl daemon-reload
``` 
in order for the new settings to be loaded.(Also a reboot should have set it)
Now it may be possible, (I said "May be") to fool around a bit with the "ExeStart" option.
Show me this please:
```
sudo systemctl cat docker | grep ExecStart
[sudo] password for me: 
ExecStart=/usr/bin/dockerd -H fd://

```
To view logs related to the Docker service, run the following command:
```

journalctl -u docker
```
Will show something like a brief snip of mine:
```
-- Logs begin at Wed 2019-05-15 20:52:34 MDT, end at Mon 2019-06-10 10:21:11 MD>
Jun 10 09:25:37 arch systemd[1]: Starting Docker Application Container Engine...
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293191565-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293357822-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293377499-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293481826-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293512441-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.293592761-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.333434451-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.333932622-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.334140112-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.334486980-06:00" >
Jun 10 09:25:37 arch dockerd[8894]: time="2019-06-10T09:25:37.334525204-06:00" 
```

You can also see: "Jun 10 03:08:21 vps51801 docker[233]: mount: wrong fs type, bad option, bad super block" on your last return.
Well at the very least we can use this as a learning curve. ;)

---

