---
title: "problem with partitions"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by anarki007 on 2008-06-07
Hello, my problem is: I cant use my other 2 partitions (/windows , /dos both ntfs), from places menu, and desktop menu only from /dos in filesystem drive, also not showing in computer folder, Thanks

---

### Post by bumanie on 2008-06-07
> sudo fdisk -l (that's a lower case L) and > cat /etc/fstab

---

### Post by anarki007 on 2008-06-07
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30723288+   7  HPFS/NTFS
/dev/sda2            3826       19123   122881185    7  HPFS/NTFS
/dev/sda3           19124       19366     1951897+  82  Linux swap / Solaris
/dev/sda4           19367       30401    88638637+  83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=2a37849e-a021-4e00-8ccf-e437f5c52de1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=51F1729E330706FE /dos            ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=3CDC9703DC96B69C /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=53f1a852-7d6f-4041-b5e6-35427b28f282 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by bumanie on 2008-06-07
> sudo apt-get install ntfs-3g > sudo apt-get install ntfs-config Then go to Applications --> Accessories --> System Tools and use the configuration tool. That should allow read/write to your ntfs partitions and will also automatically edit /etc/fstab. The ntfs partitions should be automounted at boot. Hope this works. Good luck.

---

### Post by anarki007 on 2008-06-07
great and thanks, now i want to access them from my desktop and from places menu and from computer folder

---

