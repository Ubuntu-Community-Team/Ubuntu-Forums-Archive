---
title: "Partitions"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by xsilvergs on 2008-08-28
Hi

I have Ubuntu on an 80g drive but the drive is a bit of a mess I think.
In GParted it looks like this:
Partition__Filesystem__Mountpoint__Size______Used_____Unused___Flags
/dev/sda1____unkown_______________38.86BiB____--________--______boot
/dev/sda2___extended______________37.86GiB_____--________--______lba
 /dev/sda5____ntfs__________________3.21GiB_______--________--
 /dev/sda6____ext3_______/__________33.18GiB__12.24Gib___20.93GiB
 /dev/sda7___linux-swap_____________1.47GiB______--________--

I'd like to get ride of the small bit of ntfs partition and anything else you would recommend but what happens to Grub of which I know nothing about?

If someone could advice I'd be grateful.

Tony

---

### Post by kabotage on 2008-08-28
similar discussion here.

[http://ubuntuforums.org/showthread.php?t=871374&highlight=ubuntu+ntfs+parition](http://ubuntuforums.org/showthread.php?t=871374&highlight=ubuntu+ntfs+parition)

---

### Post by Elfy on 2008-08-28
Grub shouldn't be affected - you should be able to delete the ntfs and grow you / ext3 to take it up. What is the first partition then - sda1?

You iwll have to do it either in a gparted livecd or from the buntu livecd, you''l not be able to do anything in the buntu livecd until you turn swap off

If you run ```
sudofdisk -l
``` it will show us your partitions - easier than typing it out :)

---

### Post by phidia on 2008-08-28
Back up anything you don't want to lose before you start making changes.
Grub will not be affected by changes you make-grub is on a special reserved section of the hd 
called the master boot record or MBR. If you accidentally delete a boot partition grub won't be able to find it.

There's info on partitioning at the Ubuntu wiki [here]("https://help.ubuntu.com/community/DrivesAndPartitions").

---

### Post by xsilvergs on 2008-08-28
@ forestpixie
from the sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5022    40339183+  83  Linux
/dev/sda2            5023        9964    39696615    f  W95 Ext'd (LBA)
/dev/sda5            5023        5441     3365586    7  HPFS/NTFS
/dev/sda6            5442        9772    34788726   83  Linux
/dev/sda7            9773        9964     1542208+  82  Linux swap / Solaris

So using GParted I can delete the ntfs partition, then expand sda6 to fill the free space?

Yes or No?

Thanks

---

### Post by Elfy on 2008-08-28
AFAIK yes - you might need to move sda6 to the left after you have deleted sda5 and then resize though not completely sure as I use partedmagic.

Bu there is no reason why you won't be able to achieve your end, if you do use the gpartyed on the buntu cd you can turn swap off with

```
sudo swapoff -a
```

---

### Post by xsilvergs on 2008-08-28
@ forestpixie

Just realised you live down the road from me.

When I try to delete the ntfs partition I get a warning "Please unmount any logical partitions having a number higher than 5".

Ubuntu lives on /dev/sda6, if I unmount it what are the consequences?

You asked about sda1, it's just empty.

Tony

---

### Post by Elfy on 2008-08-28
You must first do it from a livecd of some sort and also run the swapoff command.

You can't work on mounted partitions - so if you are in your installed buntu it won't be possible.

Cool - didn't notice - that must be about 6 or so in shouting distance almost enough to meet :D

---

