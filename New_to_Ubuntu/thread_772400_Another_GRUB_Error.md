---
title: "Another GRUB Error"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by amgc5 on 2008-04-28
I am certain this is like the zillion th post on GRUB Errors with "Hardy". The system is a Athlon 2600+, 1.2MB, NVIDIA FX 5200, Dual Boot (XP and Hardy) and so as the story goes...

Installed Ubuntu 8.04 ( changed the menu.lst to make XP the default)..that ended up giving me Grub Error 21.

So finally decided (after about 3 hours of using Live CD to reset the GRUB) to reinstall Hardy again. When I restart this system, the classical error message comes up

Grub Loading 1.5
Error 5 or 21 or 22 ( Different times that I tried this out)

Now the wonderful thing about CNTRL +ALT+ DEL is that once used after this error, I can see the Boot menu loud and clear!  I also noticed this error does not seem to occur when I restart the machine after using CTRL+ALT+DEL.

*************************
I have pasted the results of the FDISK -L below....
*************************

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dea4f0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         397     3188871   82  Linux swap / Solaris
/dev/sdb2             398       19456   153091417+   f  W95 Ext'd (LBA)
/dev/sdb5             398        2212    14578956    7  HPFS/NTFS
/dev/sdb6            2213        4675    19784016    7  HPFS/NTFS
/dev/sdb7            4676        7189    20193673+   7  HPFS/NTFS
/dev/sdb8            7190        9609    19438618+   7  HPFS/NTFS
/dev/sdb9            9610       13896    34435296   83  Linux
/dev/sdb10          13897       16355    19751886    7  HPFS/NTFS
/dev/sdb11          16356       19456    24908751    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x665994ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

**********************
and the MENU.LST looks like this....

********************

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

***************************
Suggestions are welcome!

---

### Post by oedha on 2008-04-28
have you try supergrubdisk ?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Zralou on 2008-04-28
I'm far from an expert in grub, but from what I see, it looks like you have 3 HDD's, make sure the grub is installed on the first disk's boot sector, or grub will get confused.

Sara Lou

---

### Post by amgc5 on 2008-04-28
Thanks for the input.

After much deliberation I have come to realize that part of the issue is sitting in the BIOS MENU. The Primary slave which is set up as  "AUTO DETECT" is not recognized and hence as you pointed out, GRUB is confused.

Do I then need a firmware/BIOS update from the motherboard manufacturer?

---

### Post by Zralou on 2008-04-28
A firmware upgrade wouldn't hurt any.  But one thing I also noticed, on your second HDD, you have around 9 partitions, only 4 'primary' partitions are allowed, the rest need to be extended or logical (I can never remember which one is which!!).  I've never had any experience of more than 4 partitions, so i don't know how that would affect things or whether that is your problem or not.

Sara Lou

---

### Post by amgc5 on 2008-04-28
Do you imply it is safe to go with 4 partitions instead of the many I have. Could you offer more explicit guidance as to what you mean by having them as logical/extended drives and how one would go about fixing this issue?

Thanks for your attention.

---

### Post by Zralou on 2008-04-28
As I stated earlier, i've never had any dealings with more than 4 partitions, so I don't want to advise you on things that I am only guessing at.
Its possible you may already have your partitions set out as they should be, I don't know, all I know is a HDD can only have 4 'primary' partitions, after that, you have to 'split-up' the primary partitions with extended/logical to get more.  I was just throwing out possible causes of your problem.

Sara Lou

---

