---
title: "files via fdisk -l not same as via System Monitor File Systems"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by aspergerian on 2008-08-24
I have 8.04.1 somewhat functional on an Asus eee 901 and am trying to understand how installation-partitions correspond with partitions reported by fdisk -l and with partitions reported by system monitor file systems. The latter shows only sda1, sdb1, and sdc1 -- whereas fdisk -l reports sda1,2,3,4 and sdb1,2,5, and sdc1.  File Browser shows even less information, so I'm wondering why my system monitor file systems is showing only some of partitions. Here's the fdisk -l: 



/dev/sda1   *           1         400     3212968+  83  Linux
/dev/sda2             401         488      706860   83  Linux
/dev/sda3             489         489        8032+  83  Linux
/dev/sda4             490         490        8032+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         730     5863693+  83  Linux
/dev/sdb2             731        1962     9896040    5  Extended
/dev/sdb5             731        1962     9896008+  82  Linux swap / Solaris

Disk /dev/sdc: 16.0 GB, 16071000064 bytes
218 heads, 56 sectors/track, 2571 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Disk identifier: 0x000cb24d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2572    15690240   83  Linux

---

### Post by Pro-reason on 2008-08-25
GNOME System Monitor shows you only mounted filesystems.  Fdisk shows you all filesystems.  To see all filesystems graphically, try GParted.

---

