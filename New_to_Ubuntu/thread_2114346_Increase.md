---
title: "Increase"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by ebbishop on 2013-02-09
I installed Ubuntu alongside Windows 7 (using wubi) and want to increase the size of my Ubuntu partition. (Eventually, I'd like to wipe windows, but I'm not ready for that leap yet.)

I think I understand the instructions I've found for adjusting partitions.  Trouble is, I can't tell for sure which one it is. :confused:

df -h:
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   16G  727M  96% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           1.2G  928K  1.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.9G  252K  2.9G   1% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sda2       576G  215G  361G  38% /host
/dev/sdb1       299G  141G  158G  48% /media/emma/FESTE
/dev/sda4       100M   15M   85M  15% /media/emma/HP_TOOLS
/dev/sda1       199M   29M  171M  15% /media/emma/SYSTEM


sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1207068671   603329536    7  HPFS/NTFS/exFAT
/dev/sda3      1207068672  1250050047    21490688    7  HPFS/NTFS/exFAT
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)

Which partition is ubuntu?

---

### Post by cwsnyder on 2013-02-09
Ubuntu under WUBI is installed _under Windows_ as a folder in the Windows partition (/dev/sda1), it is actually /dev/loop0 as seen from Ubuntu.

---

### Post by bcbc on 2013-02-10
See [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) to create a large copy of the root.disk or if you want to do a real resize you have to boot a live CD/USB and you can follow instructions here: [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

---

### Post by MadmanRB on 2013-02-10
Yeah WUBI is a limited in the space it allows, do a dual boot if you have the room.

---

### Post by ebbishop on 2013-02-10
> **cwsnyder said:**
> Ubuntu under WUBI is installed _under Windows_ as a folder in the Windows partition (/dev/sda1), it is actually /dev/loop0 as seen from Ubuntu.
> **MadmanRB said:**
> Yeah WUBI is a limited in the space it allows, do a dual boot if you have the room.

OOHHH. Well, quite a few things make a lot more sense. I suppose I should have done more reading about wubi before I went that route.

I think what I actually want to do is do a real dual-boot. Thanks for turning on that light bulb for me.

:-)

---

### Post by howefield on 2013-02-10
> **ebbishop said:**
> I think what I actually want to do is do a real dual-boot.

Not so easy when you have the maximum number of primary partitions already taken for your windows system..

Have you made back up / recovery / system disks yet ?

---

