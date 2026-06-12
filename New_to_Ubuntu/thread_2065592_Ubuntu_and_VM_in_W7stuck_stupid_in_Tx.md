---
title: "Ubuntu and VM in W7:stuck stupid in Tx"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by rscottbruton on 2012-10-02
](*,)](*,)I need stand alone installation of Ubuntu , What Version of Ubuntu can I use? is there a true ISO I can use to format oracal Vertual box ? Does the desktop 'live cd' have a true ISO I can format with if so where the heck is it ?

---

### Post by Mark Phelps on 2012-10-02
IF you're seriously interested in installing Ubuntu in dual-boot setup with existing Win7, it's not a simple matter of "formatting with an ISO" -- there's a LOT more involved.

Read more below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by rscottbruton on 2012-10-04
Thanx for the info on the dual boot and partitioning.I don't really want a dual boot system and I could care less about crapping 7,I would like to create a Ubuntu VM stable enough for samuri wtf or just stand alone ubuntu,VM would this be possable with 12.04,11.10

---

### Post by rscottbruton on 2012-10-04
don't really want a dual boot system and I could care less about crapping 7,I would like to create a Ubuntu VM stable enough for samuri wtf or just stand alone ubuntu,VM would this be possable with 12.04,11.10

---

