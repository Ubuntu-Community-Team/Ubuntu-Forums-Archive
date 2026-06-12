---
title: "command comparison"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by melrokz on 2008-11-25
Is there any literature on equivalent commands on Ubuntu and Fedora? Ubuntu's commands don't work on fedora. If not, please tell me the equivalent commands for:
lsusb
modprobe
dmesg
wvdialconf
wvdial

to connect a Reliance mg880 usb modem on fedora.

---

### Post by ndefontenay on 2008-11-25
They should be pretty much the same the commands are *nix command and rarely distro related.

Although their are some like apt-get which could be something different for fedora because it's 2 big schools: Debian vs Red Hat, most of the commands should work.

The way you should tackle this is to completely ignore that you know about ubuntu and find out fedora commands. 

A document comparing both if existing would be irrelevant.

---

### Post by scorp123 on 2008-11-26
> **melrokz said:**
> Ubuntu's commands don't work on fedora. If not, please tell me the equivalent commands for:
lsusb
modprobe
dmesg
wvdialconf
wvdial The commands are identical. But: Are you sure that the necessary packages are installed? If those packages are not installed then the commands will obviously not work. I am not so sure (haven't used Fedora in ages), but I think the package manager there is called "yum"? So to get "wvdial" you'd have to change into "root" and then tell "yum" to install "wvdial" if it isn't installed already:  ```
su -
yum install wvdial
```

Again - I am not so sure about "yum" and the syntax ...

---

### Post by Sorivenul on 2008-11-26
> **melrokz said:**
> Is there any literature on equivalent commands on Ubuntu and Fedora? Ubuntu's commands don't work on fedora. If not, please tell me the equivalent commands for:
lsusb
modprobe
dmesg
wvdialconf
wvdial

AFAIK, most of the command will be similar, however some have to be done as root on fedora using "su" unless you have "sudo" setup.  After that, sometimes the command must be prefixed with its directory, i.e.:
```
[root@fedora sorivenul]# /sbin/ifconfig
```
(Note, this command works for me without being root and without the prefix.)

---

