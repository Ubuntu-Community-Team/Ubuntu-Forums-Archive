---
title: "0 active partitions"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Zenmij on 2008-10-31
So whilst installing Ubuntu, I made a mess of the partitions and when I tried to re-boot, i got 0 active partitions message.

As my Cd-drive isn't working, I got GParted on USB. I was quite impressed I was able to surf the internet on a 128mb flash drive. Anyways - heres my fdisk -l:

```
root@PartedMagic:~# fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        7296    58605088+   5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris
/dev/sda6               1        4255    34178193    b  W95 FAT32
/dev/sda7            4256        7108    22916691   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 131 MB, 131072000 bytes
2 heads, 63 sectors/track, 2031 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0076bfb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2032      127984    6  FAT16

```

Why would I still be getting 0 active partitions? I am hoping to install ubuntu from a larger USB drive tomorrow. Would that solve the problem. 

Thanks v much.

---

### Post by phidia on 2008-10-31
I think it would help if you provide the complete error message.

Looks like you have two drives-4 partitons on sda & one on sdb.
Did you shrink the win95 partition on sda? 

I don't know what happened during partitioning but if you're not afraid of CLI (command line) then cfdisk is a faster and simpiler way to partition. You can use cfdisk from the live cd.

---

