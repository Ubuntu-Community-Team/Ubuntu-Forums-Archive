---
title: "[SOLVED] Can't find Samsung player"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by arj446 on 2008-08-20
hi


I have a Samsung YP-K3 MP3 player and I can't even find it if I run gparted. Using : "sudo fdisk -l", I get the following :

> Disk identifier: 0x1a2d1a2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        9729    52548615    f  W95 Ext'd (LBA)
/dev/sda5   *        3188        5099    15358108+   7  HPFS/NTFS
/dev/sda6            5100        7011    15358108+   7  HPFS/NTFS
/dev/sda7            7012        9636    21085281   83  Linux
/dev/sda8            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS


No MP3 player anywhere... Any idea ?


Edit : I found a way to solve my problem !!

---

