---
title: "Trouble mounting an external HD in 8.04"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Tripawd on 2008-04-26
Hi,

I'm attempting to get 8.04 to recognize my external hard-drive, and not having much luck.  It shows the drive under my computer, but won't access it, saying it cannot mount.  The response I get from "sudo fdisk -l" is:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x584ccec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    c  W95 FAT32 (LBA)

Any suggestions would be appreciated.  Thanks!

---

### Post by Tripawd on 2008-04-28
bump

---

### Post by dokdoom on 2008-04-28
If your external HD is plugged in remove it, wait a moment then plug it back in. Now run 'dmesg' The last section should tell you your HD was connected and what to mount it as (Example:.. /dev/sda1)

I've only had to do this on debian but then you would run

mkdir /mnt/exthd (or whatever you want really.)

then

mount /dev/sda1 /mnt/exthd (note, it may not be sda1 so use what is listed when you run dmesg. Also make sure you mount it to the correct directory you mae in /mnt

Using this method, before you remove the HD make sure to run this command from your /mnt directory.

umount /exthd (Or whatever you named the directory.)

---

