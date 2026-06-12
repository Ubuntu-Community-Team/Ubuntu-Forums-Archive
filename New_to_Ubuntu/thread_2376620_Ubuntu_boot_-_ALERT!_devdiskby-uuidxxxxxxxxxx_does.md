---
title: "Ubuntu boot - ALERT! /dev/disk/by-uuid/xxxxxxxxxx does not exist. Dropping to"
date: 2017-11-04
forum: New to Ubuntu
---

### Post by theexpert1234 on 2017-11-04
Hi Everyone ,

I have recently cloned dual boot Win7 and Ubuntu14 LTS  from HDD to SSD with Acronis . I am able to boot WIN7 fine  but having issues with ubuntu booting with following error

**********************************************************************************************************************************
error: no such device: 3892DDC792DD8A30 .
Loading Linux 3.13.0-112-generic ...
Loading initial ramdisk ...

Press any key to continue...


Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/3892DDC792DD8A30 does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)
*************************************************************************************************************************************

I have tried to repair GRUB 2 with Ubuntu live USB but it didnt work . The output is in the following URL boot info.

[http://paste.ubuntu.com/25884944/](http://paste.ubuntu.com/25884944/)

from the boot info ,I can see the UUID "3892DDC792DD8A30" almost 95 times   which I believe is my old  HDD partition UUID .

from my beginner knowledge perspective I believe If the old HDD partition UUID is replaced by new device SSD partition UUID  it can work, but not sure which partition UUID to use  and how to do it ?.

Please help.

Thanks.

---

