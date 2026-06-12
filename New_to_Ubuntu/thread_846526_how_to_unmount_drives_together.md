---
title: "how to unmount drives together"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by huxinda on 2008-07-01
hi, 

I have an external hard drive which I created 4 partitions.
When I plug in the drive, 4 icons(volumes) are automatically created on the desktop. And when I want to remove the external drive, I need to unmount each volumes respectively.

So, 
is there a way that I can unmount all 4 volumes together just like what we did in WinXP?

and BTW,
how to setup the system and the mounted volumes will not shown on the desktop? because I always have this external drive plugged in. It's a little bit messy to have 4 icons shown on the desktop.

Thanks.

---

### Post by aktiwers on 2008-07-01
Could you post the output of:
 ```
sudo fdisk -l
```
While the drive is plugged in? 

Then we can make a small script that you just run with double-click to unmount all 4 partitions at the same time.

---

### Post by huxinda on 2008-07-01
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc45181ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/sda2            2041       14593   100831972+   f  W95 Ext'd (LBA)
/dev/sda5            2041        5865    30724281    7  HPFS/NTFS
/dev/sda6            5866        9690    30724281    7  HPFS/NTFS
/dev/sda7            9691       13163    27896841    7  HPFS/NTFS
/dev/sda8           14314       14593     2249068+  1b  Hidden W95 FAT32
/dev/sda9           13164       14220     8490321   83  Linux
/dev/sda10          14221       14313      746991   82  Linux swap / Solaris

---

### Post by aktiwers on 2008-07-01
Is the drive plugged in? Is it 120gb drive? 
For me it looks like it has 10 partitions? 

I think your external drive is not showing in this fstab output.. are you sure it is plugged in and mounted? :)

---

