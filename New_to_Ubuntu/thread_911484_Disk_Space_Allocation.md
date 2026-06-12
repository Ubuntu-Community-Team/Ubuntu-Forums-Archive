---
title: "Disk Space Allocation"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by ryanchang on 2008-09-05
Hello,

I have an HP Pavillion dv6000 that came with Vista, and I installed Hardy with the boot CD in Windows. Unbeknowst to me, I thought I would be able to have access to the entire 200 GB hard drive in either OS, but unfortunately, I only have 9 GB available to me when using Ubuntu, causing many problems (Firefox crashing b/c my tmp is full, openoffice.org not saving documents, etc.). I was wondering if there was anyway I could increase the size of the partition within the terminal or any other method? These problems have recently occured and it's causing me a lot of headache! HELP!!

Thanks
Ryan

---

### Post by Paul41 on 2008-09-05
I have never used GParted however I have heard a lot of good things about it. It may do it for you. If you do try to resize make sure that you back up both Ubuntu and Windows before you do anything just in case.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Elfy on 2008-09-05
Is it installed inside windows as wubi or is it a seperate install? If you're not sure and are inside ubuntu - run this from a terminal ```
df -h
``` and post the result.

If it's wubi you can resize the virtual disk, if it's a seperate you can resize the partition.

If it is wubi - the rest of the windows disc should be accessible in /hosts in nautilus.
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I resize the virtual disks?

---

### Post by HunterA3 on 2008-09-05
When you installed Ubuntu, did you choose install in available disk space?

---

### Post by halitech on 2008-09-05
you should be able to access the windows partition from Ubuntu if you have a storage area set aside as Ubuntu can read NTFS with no problem.

I would boot into Windows, run a defrag then reboot at least twice then use the disk manager to resize your windows partition.

then use the gparted cd to resize your Ubuntu partition. You can't do it from within Ubuntu as the system will not let you do anything to a mounted partition.

---

### Post by 7raTEYdCql on 2008-09-05
You can resize using Gparted/Qtparted. Haven't tried them earlier though. Remember to take backup before resizing. You have installed Hardy in Windows? Didn't understand.

If you are running a virtual machine then i you can change the settings most definately.

---

### Post by Caedis on 2008-09-05
Just to clarify for you. They are asking you to pull out your ubuntu install disk, put it in the cd drive, restart, and start from the live cd. From there you need to go to the system options and open the partion editor. Its called "gparted"

With gparted you can freely and with relative safetly edit your partion tables.

---

### Post by Elfy on 2008-09-06
> Just to clarify for you. They are asking you to pull out your ubuntu install diskI'm not, Im trying to find out what sort of install it is  - if it is a wubi install then gparted will not help ;) and it would cetainly appear to be a wubi install

> and I installed Hardy with the boot CD in Windows

---

### Post by halitech on 2008-09-06
open a terminal and do ```
sudo fdisk -l
``` and post the results back here

---

