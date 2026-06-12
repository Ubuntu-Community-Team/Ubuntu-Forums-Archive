---
title: "Using Graphical Install"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by Exia GN on 2013-06-14
Ok, I have been out of the loop for a few years, trying to dual boot my laptop with Ubuntu 12.04 I believe, and I am of course using the graphical install. When it comes time to install and use the partition system, I am kinda mind frelled.. I am using the first one the one where you can drag to allocate what needs to be partitioned.. But my question is which side is for Ubuntu and which is my Windows.. 

I do alot of Online gaming so I need to keep a little for the windows side.

---

### Post by byStanderone on 2013-06-14
.you may use gparted to create your partition for 12.04...and install it there....leaving windows untouch.

---

### Post by byStanderone on 2013-06-14
..kindly provide us more info...say how many hdd is in your box and its capacity,...how much area is free for ubuntu usage.

---

### Post by 3rdalbum on 2013-06-14
The left side is Windows, the right side is Ubuntu. There should be a Windows logo in the left side and an Ubuntu logo in the right side.

---

### Post by newb85 on 2013-06-14
As 3rdalbum said, Windows should be first.  In my experience, the installer gives more space to Windows than to Ubuntu by default.

---

### Post by Mark Phelps on 2013-06-14
If you're running Win7 (or Vista) do NOT, repeat NOT, drag the slider in the Ubuntu installer to shrink Windows.  Doing so risks corrupting the Windows boot loader and rendering it unbootable. 

If you're serious about dual booting with Win7 (or Vista), then read through the materials below BEFORE you do anything:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by 3rdalbum on 2013-06-14
@Mark Phelps: Shrinking an NTFS partition, whether it be created for Windows XP or Vista or Seven or Eight, is pretty well safe on Linux and has been for years and years. I've done it several times with no problems.

Your suggestion to create and burn a Windows repair CD is a good one, though. And of course, before doing anything with partitions, back up your data. Most of my partition resizing has worked just fine, but once it didn't (however, it was a Mac HFS+ partition; resizing those is probably not as well tested).

---

### Post by Exia GN on 2013-06-15
Well I am using a Toshiba C655 series, so I have no CD, the windows restore system is on a Hidden Partition, which you can not monkey with not even with linux, It tells me there is 2 hidden partitions but when you click the Advanced view it still does not show them, so hopefully I am fine, I normally do a monthly format of Windows anyway.. 

But I thank you for the help, I made my partition a small one for Ubuntu about 80GB, which left 180+ for windows

---

