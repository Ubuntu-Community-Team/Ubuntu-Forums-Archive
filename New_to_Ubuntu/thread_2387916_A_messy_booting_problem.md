---
title: "A messy booting problem"
date: 2018-03-25
forum: New to Ubuntu
---

### Post by emir19785 on 2018-03-25
I  recently purchased a Purism librem 15 v3 laptop and it has pre installed Purism OS. I used a bootable USB to install Ubuntu on my second hard drive. While I formated the first hard drive with Purism OS. When I start the system I get this message: 
"Booting from Hard Disk ..." message by SeaBIOS (version rel-1.10.0-53-gdd9bba5)


  It does not boot, the message is stuck forever. I then have to switch off PC and get in to BIOS and manually choose second hard drive with Ubuntu in order to boot it. How can I fix this issue and get Ubuntu booted promptly? Any advice more then welcome.

I made few pictures below.

---

### Post by oldfred on 2018-03-25
Know nothing about Purism.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Most systems let you set default boot drive in BIOS. But yours may not?
It looks like you installed Ubuntu using the advanced LVM  volume system.

---

