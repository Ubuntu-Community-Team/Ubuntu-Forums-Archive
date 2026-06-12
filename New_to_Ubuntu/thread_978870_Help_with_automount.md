---
title: "Help with automount"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by NHBF92ITpRhT on 2008-11-11
I just changed my home media server from OpenSuse to Xubuntu 8.10 and my Fat32 drives aren't auto-mounting.  I am setting this box up to just be a simple Samba server, and I am doing it from work right now using Putty.  I'll show you what I have so far:

jimmy@linux-server:/media/windows/c$ sudo fdisk -l

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b180b17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3648    29302528+   c  W95 FAT32 (LBA)
/dev/sdb2            3649       14593    87915712+   f  W95 Ext'd (LBA)
/dev/sdb5            3649        7296    29302528+   b  W95 FAT32
/dev/sdb6            7297       14593    58613121    b  W95 FAT32

/dev/sdb1 on /media/windows/c type vfat (rw)
/dev/sdb5 on /media/windows/d type vfat (rw)
/dev/sdb6 on /media/windows/e type vfat (rw)

If someone could guide me as to what should be added to fstab, i'd appreciate it.

---

### Post by bodhi.zazen on 2008-11-11
Post your /etc/fstab :)

Usually all that is needed is to add the work "auto" in the options column.

---

### Post by NHBF92ITpRhT on 2008-11-11
jimmy@linux-server:/media/windows/c$ vi /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c7795aea-939b-4f1e-a5fb-ddb0c93871e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=080dc206-414b-40ad-a979-ebddef62708f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~
~
~
~
~
~
~
~
~
~
~
~
"/etc/fstab" [readonly] 9 lines, 480 characters

---

### Post by bodhi.zazen on 2008-11-11
```
/dev/sdb1 /media/windows/c vfat auto,users,uid=1000,gid=100,dmask=027,fmask=137 0 0
```

Those dmask and fmask settings may be too restrictive, relax them if needed.

---

### Post by NHBF92ITpRhT on 2008-11-12
worked perfect, thank you.

---

