---
title: "What graphics drivers should I use?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by conure on 2013-06-06
Hey all,

I have opted to install Ubuntu on a partition of my W7 drive, because I've never had much luck getting it to book from a USB memory stick.

Will I need to install Nvidia graphics for my GTX 660? I know Linux handles drivers differently to Windows, and I've only run Ubuntu via Virtualbox in the past.


Hope you can advise!

Luke

---

### Post by Feathers McGraw on 2013-06-06
When you install Ubuntu you'll automatically get the open source drivers for your card.

I'd only change them if you have a problem! I've installed ubuntu on four laptops recently for friends and only one had a problem with the open source drivers (this one, of course ;)).

Feathers

---

### Post by 3rdalbum on 2013-06-06
The open source driver comes by default, and it is not bad.

Nvidia does make its own driver for the GTX 660 that gives video decode acceleration and better 3D performance. If you go to the Software Sources program and click on the last tab, Ubuntu will offer to download and install it.

---

### Post by newb85 on 2013-06-06
That's right.  The best way with Nvidia is not to go searching the web for drivers to download.

I'm not sure I understand how you're installing for the short-term.

---

### Post by Mark Phelps on 2013-06-06
Since you're serious about dual-boot installation, and appear to be concerned about problems with Win7 in the process, then you need to read through all the material below BEFORE you jump into the Ubuntu install:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by TNFrank on 2013-06-06
IF you're sick of Win7 then why not just give it up altogether and go with only Ubuntu like I did?  You can install Ubuntu into Win7 using the wubi then once it's in use the Startup Disk Creator to make a bootable copy of Ubuntu to either a USB or CD. Then make sure you've set your BIOs to boot first to that device and do a clean overwrite install of Ubuntu. If there's some Win7 stuff that you just have to use you can probably run those programs under WINE. Be sure to save anything you have in Win7 and want to keep to a CD or USB drive so you'll have it to reinstall in Ubuntu.

---

### Post by Impavidus on 2013-06-06
Not sure why you would need wubi to create an Ubuntu live usb/dvd. Windows programs can do that too.

Although I completely ditched Windows myself, I think it would be best for you to keep Windows for a while. It will take time before you can do everything you want easely in Ubuntu, to keep productive during that time it's best to keep a system you're already comfortable with. Don't count on it that all your favorite Windows apps work in wine. Some will, but not all of them.

---

### Post by conure on 2013-06-06
Hello all,


Thanks for the replies,

A problem I continually run into despite attempting an install on two hard drives (one SSD with Windows on, and another RPM drive which was formatted) is this:


[IMG]http://img153.imageshack.us/img153/7264/ubuntu2.png[/IMG]



I've Googled the messages but because I'm quite new to Linux I'm struggling to interpret the meaning - any tips would be appreciated!

Luke

---

### Post by conure on 2013-06-06
Quick bump before I go to bed!

---

