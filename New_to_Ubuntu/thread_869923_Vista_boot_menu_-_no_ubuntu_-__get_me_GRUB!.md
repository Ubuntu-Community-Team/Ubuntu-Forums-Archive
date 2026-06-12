---
title: "Vista boot menu - no ubuntu -  get me GRUB!"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by therancid on 2008-07-25
I seen another thread similar to this!

I installed ubuntu after vista, i tried sudo fdisk -l this is what i got:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a88f8c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdb2            8925       21979   104857600    7  HPFS/NTFS
/dev/sdb3           21980       30401    67649715   83  Linux

How do i change it so it loads grub instead of the vista boot menu?

---

### Post by logos34 on 2008-07-25
maybe grub installed on the other drive's mbr.  Change the Bios hard disk boot priority, see what happens

---

### Post by niyonk on 2008-07-25
Hi, and welcome :)

It seems most people point at this [thread]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

I did use it myself recently just make sure you follow the instructions carefully.
OR if you are interested in adding Ubuntu to vista bootloader, then try [EasyBCD]("http://neosmart.net/dl.php?id=1")

Cheers!

---

