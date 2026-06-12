---
title: "[SOLVED] Need to remove windows from two disk system"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by tydfil on 2008-10-05
I'm certain this question has been asked before.  I have a dual boot Windows XP on hda and Linux partitions on sdb.  I would like to completely remove windows.  I can use gparted to convert hda partition to ext3.  The question is, how will this effect booting with Grub?
> fdisk -l gives:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24432442

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1        9729    78148161    5  Extended
/dev/sdb5               1        9306    74750382   83  Linux
/dev/sdb6            9307        9729     3397716   82  Linux swap / Solaris


---

### Post by Elfy on 2008-10-05
It shouldn't - grub will be ok assuming that when you installed you didn't change any of the grub options. After you've finished you can remove the references to windows from the menu list.

---

### Post by tydfil on 2008-10-05
Thanks a lot.  Fastest solution ever.

:popcorn:

---

