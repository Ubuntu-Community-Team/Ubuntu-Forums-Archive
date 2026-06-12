---
title: "noob dual boot question"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by JParkus on 2008-05-15
i have (2) 80 gig serial hdd raid 0 for ubuntu and just added a 40 gig ide hdd that i put windows on. how do i find out the volume number for the 40 gig so i can add it to grub

---

### Post by rockerphil on 2008-05-15
i'd personally boot in to Ubuntu and do a

sudo fdisk -l

and look for your Windows drive, that should tell you the volume #

---

### Post by JParkus on 2008-05-15
[sudo] password for parkus: 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7507

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+  fd  Linux raid autodetect
/dev/sda2            9727        9848      979965   82  Linux swap / Solaris
/dev/sda3   *        9849        9964      931770   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70746e75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  fd  Linux raid autodetect
/dev/sdb2            9727        9964     1911735   82  Linux swap / Solaris

Disk /dev/md0: 159.9 GB, 159997886464 bytes
2 heads, 4 sectors/track, 39061984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c3827ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4864    39070048+   7  HPFS/NTFS

sdc1 is the windows drive so when i sudo gedit /boot/grub/menu.lst

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/md0 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/md0 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
root (hd3,0)
chainloader +1

the root should be root (sd3,0) right?

---

### Post by rockerphil on 2008-05-15
not exactly sure, but it sounds right, but just to be safe i'd save the old grub menu.lst file so that if it's not you can restore to it, but i hope it comes out all good man :)

---

### Post by meierfra. on 2008-05-16
(sd3,0) is definitely wrong. Try


title Windows XP
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


If that did not work:

title Windows XP
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1


and  

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

