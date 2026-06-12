---
title: "Bootable usb stick running gparted software at the boot time"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by ramkashyap117 on 2013-05-18
I used Ubuntu 12.04 with WUBI installer for Windows7 for 2months. I wanted to install it directly so I made a bootable usb stick following the instructions given in [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) but during the boot time Gparted disc partition software is running .I couldn't understand how to install ubuntu13.04 directly(without WUBI). Please help me out......My PC configuration is 2Gb ram,500Gb harddisk,intel G630 processor

---

### Post by Mark Phelps on 2013-05-18
If you're asking how to repartition your Win7 system using GParted to install Ubuntu -- the answer is simpe -- you don't!!

Using Gparted to shrink Windows partitions is asking for trouble as it can result in filesystem corruption rendering Win7 unbootable.

If you are serious about wanting to dual-boot your system, then read on ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

