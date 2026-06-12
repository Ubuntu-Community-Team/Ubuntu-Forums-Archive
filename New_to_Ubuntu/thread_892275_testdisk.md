---
title: "testdisk"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by tommynz1975 on 2008-08-17
I ran sudo testdiskn 

in order to findout if my partitions are in good order. But I do not understand the information

sudo testdisk
TestDisk 6.1, Data Recovery Utility, October 2005Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sda - 76316 MB - CHS 9729 255 63, sector size=512

TestDisk exited normally.

here are two screen prints can you please explain them for me...



my fdisk -l output  was

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4647    37326996    7  HPFS/NTFS
/dev/sda2            9056        9729     5413905    7  HPFS/NTFS
/dev/sda3            4648        8872    33937312+  83  Linux
/dev/sda4            8873        9055     1469947+   5  Extended
/dev/sda5            8873        9055     1469916   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Pro-reason on 2008-08-17
I can't see what you want to know.  The program you were using seems to indicate it has found no errors.  Did you want it to find errors?

If you want graphical information about your drives, use GParted.

---

### Post by tommynz1975 on 2008-08-18
I forget now the command I ran but it said my ntfs drives where corrupt and wanted to view information about them

Many thanks for your time...

---

### Post by lisati on 2008-08-18
Sometimes NTFS drives show up as "possibly corrupt" (or similar) if Windows wasn't shut down properly, even when there isn't a real problem. Restarting Windows, allowing it to boot completely, and accessing the NTFS drives, then shutting down Windows through the Start->Turn off Computer menu, is often sufficient to "cure" this problem.

---

### Post by caljohnsmith on 2008-08-18
Just thought I would mention that there's a great program called "ntfsfix" that will fix 99% of the problems caused by improper shutdowns in Windows. It will save you from having to boot into Windows and shut Windows down properly. Just install:
```
sudo apt-get install ntfsprogs
```
And run:
```
sudo ntfsfix /dev/sdXY
```
Where sdXY is your Windows partition. It should be unmounted of course to use that program.

---

