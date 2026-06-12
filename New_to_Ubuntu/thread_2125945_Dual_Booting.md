---
title: "Dual Booting"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by Robert1305 on 2013-03-15
I have used Ubuntu for the past few years, but I had to recently wipe it and install Win7 :frown:

Now I would like to re-install Ubuntu 12.10, to dual boot with Win7, I have a 12.04 purchased disc, I also have a 12.10 which I downloaded and burned to a DVD.What I would like to know is, if I start my PC to load with either disk will it ask me if I wish to run it along side Win7, or will it load Ubuntu and wipe Win7. or do I have to do something different.

Regards Bob

---

### Post by chrisod on 2013-03-15
If you boot off an Ubuntu CD or USB and follow the install prompts it should recognize Windows and give you the option to install without affecting Windows.

---

### Post by Mark Phelps on 2013-03-15
Depends on what is on the PC at present.

If there is ONLY Win7, such that it fills the drive and there is no space for Ubuntu, do NOT, repeat NOT, just follow the install directions and use the slider to shrink Win7.  That runs the risk of corrupting the Win7 boot loader -- essentially negating all the work you just did.  Instead, use ONLY the Win7 Disk Management utility to shrink Win7 to make some room. And after that, reboot into Win7 a couple of times so it can make filesystem adjustments.  Do not create any new partitions with Win7, just leave the space alone.  Then, when you boot to install Ubuntu, use the "something else" option to create the partitions.

If Ubuntu is still there on the drive, and all you want to do is install over it, then use Something Else to select the existing partitions.

---

### Post by Giveingitago on 2013-03-15
Hi bob,
What does your current hard disk space look like, how is it organised in terms of number of partitions and size, space available?

Dave

---

### Post by Robert1305 on 2013-03-16
> **Giveingitago said:**
> Hi bob,
What does your current hard disk space look like, how is it organised in terms of number of partitions and size, space available?

Dave

This is what it looks like, but its double dutch to me.[ATTACH=CONFIG]240229[/ATTACH]

---

### Post by Mark Phelps on 2013-03-16
What it means is what I suspected in my thread -- you have only Windows on your drive.

If you want to install Ubuntu in dual-boot, then read through the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

