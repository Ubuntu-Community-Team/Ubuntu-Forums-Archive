---
title: "[SOLVED] Error 17 Grub Help?!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-06
Hi,

New install...i get error 17 Cannot Mount Selected Partition..

Here is menu.lst
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ee24ee1d-292b-4591-9091-6eb8bc28a907 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ee24ee1d-292b-4591-9091-6eb8bc28a907 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

and fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=ee24ee1d-292b-4591-9091-6eb8bc28a907 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd2
UUID=cb676900-2ba3-4be6-86e3-0e5b8cb748c5 /home           ext3    relatime        0       2
# /dev/sdd3
UUID=f45ec103-c1b5-44c6-b76b-d32b8e9e2235 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Please help me fix this up :confused:

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009c0eb

sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1275    10241406   83  Linux
/dev/sdd2            1276        1402     1020127+  83  Linux
/dev/sdd3            1403        1529     1020127+  82  Linux swap / Solaris

:(

thanks..

---

### Post by lisati on 2008-06-06
Edit: I asked a couple of hasty questions: The references to "hd3" don't look right......shouldn't they be "hd0" with the partitions listed?

---

### Post by hopelessone on 2008-06-06
4 hard drives..
3 partitions on the install

---

### Post by lisati on 2008-06-06
Please excuse me while I sit in a corner wearing a dunce's cap, thus giving someone who knows what they're talking about a chance to respond....

---

### Post by bumanie on 2008-06-06
Can you post the full output of > sudo fdisk -l please to show the 4 hard drives. A partial list is hard to interpret.

---

### Post by hopelessone on 2008-06-06
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9459814b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       36481   293033601   83  Linux

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075451

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010cad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009c0eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1275    10241406   83  Linux
/dev/sdd2            1276        1402     1020127+  83  Linux
/dev/sdd3            1403        1529     1020127+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by bumanie on 2008-06-06
I unfortunately have to go but I think the problem may be that you have boot flags on both sda and sdd. That may be causing the confusion for grub. I check again later when I'm free and see if you have sorted things out.

---

### Post by hopelessone on 2008-06-06
Ahhhhhhhhh....

THANKS..

---

