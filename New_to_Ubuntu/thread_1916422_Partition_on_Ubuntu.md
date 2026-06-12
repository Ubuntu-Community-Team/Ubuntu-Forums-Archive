---
title: "Partition on Ubuntu"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by swavijay on 2012-01-28
Hi All,

It's been a day since I started using Ubuntu (linux). so may sound a very basic question. 

I installed Ubuntu in my desktop and I went with the auto partition method. Now I would like to know how my Hard disk is partition. Is there a way to see the Partition in Ubuntu

I use AMD 64bit athlon processor and the Ubuntu version is: 10.04

Thanks for your help in advance.

-Vijay

---

### Post by ptsubin on 2012-01-28
There is a Disk Utility in ubuntu. Locate it in the menu. You can see the partition layout. Although I suggest you install and use gparted if you want to edit the partitions.

---

### Post by carl4926 on 2012-01-28
Gparted is installed in Ubuntu
If you open that you get a graphical look. But be careful, this is a partition editor too.

Or, just open a terminal and do:

```
sudo fdisk -l
```

It will report something like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93900d8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   136327589    68163763+   7  HPFS/NTFS/exFAT
/dev/sda2   *   136327651   312576704    88124527    5  Extended
/dev/sda5       136327653   141259544     2465946   82  Linux swap / Solaris
/dev/sda6       141259608   177582509    18161451   83  Linux
/dev/sda7       177584128   312575999    67495936   83  Linux

```

---

### Post by mastergkage on 2012-01-28
This the command i was looking for seeing how it was partition on default mode.:popcorn:

---

