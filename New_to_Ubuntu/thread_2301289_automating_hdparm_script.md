---
title: "automating hdparm script?"
date: 2015-11-01
forum: New to Ubuntu
---

### Post by DanH860 on 2015-11-01
Hi all,

I've got a Western Digital Green hard drive (WD20EARS) as a second storage drive in my PC. I'm trying to set up the PC so that after say 10 minutes of non-use the drive will spin down. I've tried to setup a spindown time with hdparm but it seems that this green drives are quite problematic at spinning down. if I run ```
hdparm -S 5 /dev/sdb
``` I get a message stating that the time has been set (25 seconds) but the hard drive won't spin down. However, running ```
hdparm -y  /dev/sdb
``` will spin down the disk straight away

After a bit of research I followed advice from [this blog]("https://blog.vandenbrand.org/2012/04/05/western-digital-green-caviar-wd10eads-and-hdparm-problems/") and using a live cd, disabled the wdidle3 setting on my drive. However, this still hasn’t fixed the problem. Figuring other people had this problem and looking around a bit, I found this excellent[ post on the forums]("http://ubuntuforums.org/showthread.php?t=2216028") that will just run the hdparm -y command after monitoring a certain amount of inactivity. However, my linux knowledge is very poor and after a bit of research I'm really not much the wiser on how to modify and automate this script on my system. 

Could anyone point me in the right direction to get this set up on my PC? Any help at all would be great thanks!

---

### Post by sandyd on 2015-11-01
I've been using [hd-idle]("http://hd-idle.sourceforge.net/") to spin down the disks on WD drives that don't have propper support for spindowns.

To install:
```

mkdir hd-idle
cd hd-idle
curl "http://downloads.sourceforge.net/project/hd-idle/hd-idle-1.04.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhd-idle%2F&ts=1446423538&use_mirror=iweb" > hd-idle.tar.gz
tar xvf hd-idle.tar.gz
cd hd-idle
sudo apt-get install dpkg-dev debhelper libc6-dev
sudo dpkg-buildpackage -rfakeroot
sudo dpkg -i ../hd-idle_*_amd64.deb 

```
You can then configure the idle times using the examples at [http://hd-idle.sourceforge.net/](http://hd-idle.sourceforge.net/)

You will need to start hd-idle at boot, so you can probably tack it onto /etc/rc.local or similar.

---

### Post by DanH860 on 2015-11-03
Wow thanks for the help Sandyd, it works! I had to also install  build-essentials before running the dpkg command but now I've got my  hard disk spinning down as I want. All I have left to do is get it  starting up after a restart, will investigate using rc.local as you  suggest

---

