---
title: "Debian will not start in dual-boot with 12.04"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by DeezyFaReal on 2012-05-30
Debian 6.0.4 will not start on my dual boot with Ubuntu 12.04
I installed Ubuntu first but I tried to make Debian the root file system, it's on a partition. I have a Compaq Presario Laptop with 2.9 GB of memory
I get this error when I try to select it in the grub boot loader
############################
Gave up waiting for root device. Common problems:
     -Boot args (cat /proc/cmdline)
       -check rootdelay = (did the system wait long enough?)
       -check root = (did the system wait for the right device?)
     -Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disc/by-uuid/b648d8b6-c822-e556a59... does not exist.

Busy box v1.17.1
     (Debian 1:1 17.1-8)
     built in shell (ash)
##############################

---

### Post by wilee-nilee on 2012-05-30
Go to this link and use this tool to run the boot info summary and post the HTTP address. Wait to use the tool until after we have looked at the script.

You can download the tool to a running Ubuntu, a live cd, or download its cd.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by DeezyFaReal on 2012-05-30
The url I got from boot-repair is
[http://paste.ubuntu.com/1014962/](http://paste.ubuntu.com/1014962/)

---

### Post by wilee-nilee on 2012-05-30
I think you are safe to run the recommended repair, try that and see if Debian does not boot.

Whichever OS is at the the top of the grub list is the one in the mbr, after running the recommended which one is at the top.

This secondary info is for if the repair does not work.

---

### Post by DeezyFaReal on 2012-09-19
Problem solved... a long time ago. I'm running Kubuntu 12.04 now, and I stopped trying to run Deb with Ubuntu.
________________________________
Hey guess what I did in September 2009 -- I got this computer!

---

