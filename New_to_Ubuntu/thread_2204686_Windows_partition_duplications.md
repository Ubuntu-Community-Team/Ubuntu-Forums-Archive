---
title: "Windows partition duplications"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by Krabun on 2014-02-09
Ubuntu 13.10
Dual boot with windows 7

Ubuntu shows windows ntfs partitions duplicated:

BACKUP
BACKUP1
MULTIMEDIA
MULTIMEDIA1
FOTO'S
FOTO'S1
FOTO'S2
DATA
DATA1

Partition 'FOTO'S even three times.

How can I get rid of these duplications?

---

### Post by Vladlenin5000 on 2014-02-09
How exactly did you mounted such partitions?

---

### Post by Krabun on 2014-02-09
By clicking on them or I save a file on those partitions.

---

### Post by Vladlenin5000 on 2014-02-09
And the "duplicates" were already there before you clicked?

---

### Post by Krabun on 2014-02-09
Only the partition 'FOTO's' which appears three times. When I unmount the partitions, the duplicates disappear, except for 'FOTO'S1'.

---

### Post by Vladlenin5000 on 2014-02-09
Sorry, it's beyond my (lack of) expertise. I hope someone else can help you.

---

### Post by Krabun on 2014-02-09
Thanks anyway.

---

### Post by fantab on 2014-02-09
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

Are the contents of the 'duplicate' folders same?

---

### Post by Krabun on 2014-02-10
sudo parted -l:

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   1000GB  1000GB  extended                  lba 
 5      106MB   18,9GB  18,8GB  logical   ntfs
 6      18,9GB  19,4GB  499MB   logical   linux-swap(v1)
 7      19,4GB  31,6GB  12,1GB  logical   ext4
 8      31,6GB  73,4GB  41,8GB  logical   ntfs
 9      73,4GB  336GB   262GB   logical   ntfs
10      336GB   598GB   262GB   logical   ntfs
11      598GB   807GB   210GB   logical   ntfs
12      807GB   903GB   95,4GB  logical   ntfs 
13      903GB   1000GB  97,4GB  logical   ntfs  




Disk /dev/sdb: 2000GB
Sector size (logical/physical): 4096B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      8389kB  2000GB  2000GB  primary               boot
 
************************************************************************

sudo fdisk -l:
[COLOR=#222222][FONT=Verdana]
Device Boot      Start         End      Blocks   Id  System [/FONT][/COLOR]
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206852  1953520064   976656606+   f  W95 Ext'd (LBA)
/dev/sda5          206854    36949183    18371165    7  HPFS/NTFS/exFAT
/dev/sda6        36950016    37924863      487424   82  Linux swap / Solaris
/dev/sda7        37926912    61644799    11858944   83  Linux
/dev/sda8        61646848   143364095    40858624    7  HPFS/NTFS/exFAT
/dev/sda9       143364123   655371674   256003776    7  HPFS/NTFS/exFAT
/dev/sda10      655371738  1167379289   256003776    7  HPFS/NTFS/exFAT
/dev/sda11     1167379353  1576988594   204804621    7  HPFS/NTFS/exFAT
/dev/sda12     1576988658  1763358659    93185001    7  HPFS/NTFS/exFAT
/dev/sda13     1763358723  1953520064    95080671    7  HPFS/NTFS/exFAT
Note: sector size is 4096 (not 512)


Disk /dev/sdb: 2000.4 GB, 2000398929920 bytes
255 heads, 63 sectors/track, 30400 cylinders, total 488378645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x90aac2d4


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   488378644  1953506388    7  HPFS/NTFS/exFAT

---

