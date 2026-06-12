---
title: "ubuntu 14.04 root on ZFS Disk Drive for /boot is not yet ready S skip M Manual"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by judaly on 2016-08-20
Hallo all,

I have a single server S that has ubuntu 14.04 root on ZFS configured. 
After I took out a hardware card connecting to a external Tape drive the server no longer boots.
It gets to the grub menu, boots but then stops with the message ... The Disk Drive for /boot is not yet ready, S to Skip or M for Manual.
I cannot enter a terminal by pressing m however often I tried up to this point.
S does work but also get the message that / can also not be found.
The biggest problem I see is that this is an ubuntu root on ZFS system and as such I may not be able to recover the system.
Is this true ? Can I recover the server ?
Just read [https://pthree.org/2013/01/03/zfs-administration-part-xvii-best-practices-and-caveats/](https://pthree.org/2013/01/03/zfs-administration-part-xvii-best-practices-and-caveats/) where he says: " Avoid running a ZFS root filesystem on GNU/Linux for the time being. It's a bit too experimental for /boot and GRUB"
Will I be able to recover this server with systemrescue disk?
to try and reproduce the problem I attempted to create an ubuntu root on zfs following the steps at [https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS](https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS) but it ended with FATAL -> Failed to fork. when trying to do a simple apt-get update
This might have been as I only gave the VM 1G
Thanks for any informations,

julian
:confused:

---

