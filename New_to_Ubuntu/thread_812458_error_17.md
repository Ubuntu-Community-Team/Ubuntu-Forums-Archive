---
title: "error 17"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by lio_013 on 2008-05-29
hey every body 
im a new ubuntu user and i install the kde desktop but i had a small prob with grub
after installing windows i couldnot see the boot menu to access ubuntu so i resetup grup again by the live cd 
the boot menu appear but when i highlight ubuntu and press enter it gives me that error
ERROR 17 can't mount selected partition
so did i destroy my ubuntu partition:(

---

### Post by Oldsoldier2003 on 2008-05-29
> **lio_013 said:**
> hey every body 
im a new ubuntu user and i install the kde desktop but i had a small prob with grub
after installing windows i couldnot see the boot menu to access ubuntu so i resetup grup again by the live cd 
the boot menu appear but when i highlight ubuntu and press enter it gives me that error
ERROR 17 can't mount selected partition
so did i destroy my ubuntu partition:(

from the live cd open a terminal and post the output from 
```
sudo fdisk -l
```
and we can help you get it sorted out.

---

### Post by quelx on 2008-05-29
boot the live cd, open terminal window (**ALT-F2** > **gnome-terminal**), and post the output of the following commands in your next post 

```
sudo fdisk -l
```

if you just have one drive mount the partition marked **Linux**

replace **#** with the number after the sda in the **Linux** line
```
sudo mount /dev/sda#
```

```
sudo cat /mnt/boot/grub/menu.lst
sudo cat /mnt/etc/fstab
```

---

### Post by Oldsoldier2003 on 2008-05-29
as an aside what happened is installing xp after ubuntu broke grub. a quick setup of grub followed by update-grub will have you back in action in no time flat.

---

### Post by lio_013 on 2008-05-30
i did mount the linux partition but when i put
[COLOR="Red"]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a834a83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       14593    96735397+   f  W95 Ext'd (LBA)
/dev/sda5            5101       10710    45062293+   7  HPFS/NTFS
/dev/sda6            2551        2794     1951866   82  Linux swap / Solaris
/dev/sda7            2794        5100    18530946   83  Linux
/dev/sda8           10711       14593    31190166    7  HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount /dev/sda7
mount: /dev/sda7 already mounted or /media/disk busy
mount: according to mtab, /dev/sda7 is already mounted on /media/disk
ubuntu@ubuntu:~$ sudo cat /mnt/boot/grub/menu.lst
cat: /mnt/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ sudo cat /mnt/etc/fstab
cat: /mnt/etc/fstab: No such file or directory
ubuntu@ubuntu:~$ [/COLOR]
[SIZE="6"]im waiting ur reply and thanks for help[/SIZE]

---

### Post by quelx on 2008-05-30
Well that kinda worked...  at least we know the device nodes for your linux partitions.  Boot the live CD again and do this (post the results)
```

sudo vol_id /dev/sda6
sudo vol_id /dev/sda7
sudo cat /media/disk/boot/grub/menu.lst
sudo cat /media/disk/etc/fstab

```

With that we should be able to fix **grub** and make sure your **fstab** is okay.

---

### Post by lio_013 on 2008-05-30
thanks alot 
im now working on the live cd 
the result is attached

---

### Post by quelx on 2008-05-30
Okay while booted from the live CD, run in a terminal

```
sudo gedit /media/disk/**boot/**grub/menu.lst
```

edit all the instances of **(hd0,7)** with **(hd0,6)**, (hint there are 4 make sure you get all of them) save and close

and well I though there would be more, but your fstab looks fine (aside from comments regarding the partitions being wrong **# /dev/sda7** should be **# /dev/sda6** and sda8 -> sda7 but don't worry about that).

reboot and you should be on your way

---

### Post by lio_013 on 2008-05-30
[SIZE="5"]when i type that it gives me an empty menu list :([/SIZE]

---

### Post by quelx on 2008-05-30
I mistyped, do this...
```
sudo gedit /media/disk/boot/grub/menu.lst
``` then follow the rest...

---

### Post by lio_013 on 2008-05-30
thaaaaa:guitar::guitar::guitar:aaaaaaaaaaanks 

im in now 
:guitar:

---

