---
title: "Ubuntu 13.04 doesn't read sd on Dell Inspiron m310z"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by daniele-iemmolo on 2013-10-27
Hello everybody,

please help me with this issue. On my Inspiron m310z Ubuntu 13.04 does not recognize a sd when I insert it into the internal card reader. Here you have some of the outputs:

annelies@annelies-Inspiron-M301Z:~$ lsusb
*Bus 002 Device 002: ID 0c45:6451 Microdia *
*Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*
*Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub*
*Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub*
[I]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[/I]annelies@annelies-Inspiron-M301Z:~$ sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000075ca


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484730879   242364416   83  Linux
/dev/sda2       484732926   488396799     1831937    5  Extended
/dev/sda5       484732928   488396799     1831936   82  Linux swap / Solaris

I already tried to follow the sollution suggested in [http://ubuntuforums.org/showthread.php?t=1559230](http://ubuntuforums.org/showthread.php?t=1559230) but it does not work.

Please help!

Daniele

---

