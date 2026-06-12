---
title: "how to use ddrescue to take data off failed hard drive"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by mrnewtothis on 2013-01-15
Using a dual boot of Ubuntu 10 4 and xp pro

Trying to get data off a failed hard drive that I have put into a USB plug and play type mount.

I did get some files off using tools on XP but just wanted to see if I could get more off using ubuntu, as there are still some files that xp missed.

When I try to use dd rescue or dd help I just keep getting errors and I have tried every combination that I have got from fdisk and using the various help pages that you find on the forum and online.

The fdisk shows:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x017d1941

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        8001    7  HPFS/NTFS
/dev/sda2               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0009082c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       31401   252224512+   7  HPFS/NTFS
Partition 1 does not start on physical sector boundary.
/dev/sdb2           31401       60802   236161025    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sdb5           31401       60620   234697728   83  Linux
/dev/sdb6           60620       60802     1462272   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007872e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19457   156288321    7  HPFS/NTFS

This is the last attempt and I get this fail

martin@martin-desktop:~$ sudo dd_rescue /dev/sdc1 /dev/sdb5/backup.img
dd_rescue: (fatal): open "/dev/sdb5/backup.img" failed: Not a directory
martin@martin-desktop:~$ 

As I said I tried several combinations but I know I am doing something stupid but do not know enough 

I did get this to work on a CD but not with this hard drive that I also can't get to mount.

Thanks for any help

---

