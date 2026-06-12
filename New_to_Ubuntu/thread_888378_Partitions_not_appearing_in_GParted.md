---
title: "Partitions not appearing in GParted"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SOULRiDER on 2008-08-13
Im trying to install Ubuntu on my Desktop. The problem i am having is that partitions on my sda do not show up on GParted during installation.

The output of fdisk -l is
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db7d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3937    31623921    7  HPFS/NTFS
/dev/sda2            3938       19457   124664400    f  W95 Ext'd (LBA)
/dev/sda3            7826        7891      530145   82  Linux swap / Solaris
/dev/sda5            3939        7825    31222296   83  Linux
/dev/sda6            7892       19457    92903863+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8ca3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    5  Extended
/dev/sdb5               1       30401   244195969+  83  Linux

```
My partitions seem to be there.

GParted says i do not have any partitions on sda but shows the partitions in sdb correctly. I ran gparted from a terminal as root and I get these errors when I try to refresh sda:
```
Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
Unable to open /dev/hda - unrecognised disk label.
Can't have overlapping partitions.

```

Any ideas on how to fix this issue without loosing any data would be greatly apreciated.

Thanks in advance.

---

### Post by ggaaron on 2008-08-13
And what disk-label do you use? Probably ubuntu doesn't have support for it compiled in. Maybe you should just use some module to make it work. On the other hand if fdisk sees it - gparted should too.

---

### Post by SOULRiDER on 2008-08-13
I believe i do not use a disk label.

---

### Post by Shazaam on 2008-08-13
Harddrives usually have a dos disklabel as default. Unless you are using a drive from a Sun/BSD system.
Sometimes, since the Ubuntu livecd is mostly loaded into memory, some apps/programs either are very slow to open or do not work very well (or at all) depending on the specs of the target system. What you can do is make a gparted livecd to do all of your partitioning beforehand. What can also work is to completely shut down the pc (using the Ubuntu livecd) and do a "cold boot" (with the Ubuntu cd inserted).

---

### Post by ggaaron on 2008-08-13
Yes, try this cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). It should support everything that gparted can do.

---

### Post by SOULRiDER on 2008-08-13
Ive already used that and stuff is still not working. I decided to install Genoo manually once again.

Thanks for the help anyway.

---

