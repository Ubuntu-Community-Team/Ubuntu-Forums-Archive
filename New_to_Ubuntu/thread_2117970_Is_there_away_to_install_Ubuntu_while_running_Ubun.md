---
title: "Is there away to install Ubuntu while running Ubuntu"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by 101kitty on 2013-02-19
Is there away to install Ubuntu while running Ubuntu, i'm having problem with the windows installer and i think its time for me to install ubuntu stand alone

---

### Post by papibe on 2013-02-19
Hi 101kitty.

Ideed there is ;)

Go to the Ubuntu website and download Ubuntu (Download -> Desktop -> Get Ubuntu).

You will be downloadin an ISO image that has to be burn on a CD or properly install on USB stick. Boot your computer into the Ubuntu Media. There you can go directly to install it or 'Try it first'. That option would take you to the desktop and you'll be running Ubuntu as a Live version of the CD. You can chose to install Ubuntu from there.

Note that you need space to install Ubuntu. I would start by shrinking your Windows partition from Windows itlsef (check [here]("http://technet.microsoft.com/en-us/magazine/gg309169.aspx")). Then install Ubuntu on the space you made available.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by 101kitty on 2013-02-19
You live in Dallas tx, your not to far from me, any-who i don'y have a sub stick nor a cd.

---

### Post by Mark Phelps on 2013-02-20
IF you're running Win7, and you're going to do a traditional dual-boot (Linux in its own partition), then read through the material below BEFORE you attempt the installation:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

