---
title: "doesn't contain a valid partition table"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by jellf on 2013-04-24
Dear Member,

I have an issue with the partition after upgrade release from 10.04 to 12.04 LTS.
i found **"doesn't contain a valid partition table" **when enter fdisk -l command.
here the output :
root@smtp:~# fdisk -l


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001afd6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   312580095   156039169    5  Extended
/dev/sda5          501760   312580095   156039168   8e  Linux LVM


Disk /dev/mapper/smtp-root: 153.7 GB, 153700270080 bytes
255 heads, 63 sectors/track, 18686 cylinders, total 300195840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/smtp-root doesn't contain a valid partition table


Disk /dev/mapper/smtp-swap_1: 6081 MB, 6081740800 bytes
255 heads, 63 sectors/track, 739 cylinders, total 11878400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/smtp-swap_1 doesn't contain a valid partition table
root@smtp:~#


Just for information i  have use LVM for this with the auto default from the beginning installation.

Regards,

---

### Post by steeldriver on 2013-04-24
AFAIK that's not really an issue with your partition table - it's an issue with fdisk not understanding LVM volumes - unless you are actually having problems with the installation you can safely ignore the message I think

---

### Post by mörgæs on 2013-04-24
Slightly off topic: I noticed you are using the root account, so [this]("https://help.ubuntu.com/community/RootSudo") might be worth reading.

---

