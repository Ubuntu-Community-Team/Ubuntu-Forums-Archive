---
title: "Mounting PS2 HDD"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by azafaraht on 2008-11-24
Hello.  I'm new to Ubuntu, just installed it 3 days ago. 

I have a PS2 HDD I want to mount on Ubuntu to extract some files, old screenshots of FFXI.  I haven't been able to mount this drive or get info on the file system used for this HDD.  

This the output of sudo fdisk -l:

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbce1bce1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6994    56179273+  83  Linux
/dev/sda2            6995        7297     2433847+   5  Extended
/dev/sda5            6995        7297     2433816   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Any help or suggestions will be greatly appreciated.

---

### Post by Keen101 on 2008-11-24
I've never owned a PS2, and i've never tried to mount a PS2 Hard Drive. But, i will try and help as best i can.

as far as i can tell, your PS2 drive is a ~40GB drive, but is partitioned with something that fdisk cannot recognize. you will probably have to reformat and repartition. Try to google to see if anyone has some sort of alternative to reformatting and repartitioning.

> Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table 

---

### Post by azafaraht on 2008-12-02
Found no alternative so basicly gave up on trying to browse my PS2 files in either Ubuntu or Windows (that was my first attempt months, MONTHS ago).  I hooked it up again to the "broken PS2" and managed to log on to FFXI again on the PS2... Emailed myself the pictures and I'll soon be reformatting the little ******* to add it to my internal drives.

Thanks for the reply Keen101.

---

