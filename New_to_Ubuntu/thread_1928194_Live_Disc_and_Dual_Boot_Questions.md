---
title: "Live Disc and Dual Boot Questions"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by tj7572 on 2012-02-19
Hello folks,
 
I am thinking of switching from Windows to Ubuntu after hearing good things about the OS. So I tried the "live disc" version of Ubuntu 10.04 and didn't like what I saw. I have a few questions.
 
Ubuntu cannot locate my monitor, leaving horrible resolution. Will this be a problem when I install Ubuntu?
 
I would like to have dual-boot system with Windows 7, at least for a bit while I get used to Ubuntu. Is the dual booting as straight forward as the Ubuntu site makes it seem?
 
Anyone have a dual-boot and have problems?
 
 
Thanks for any info, cheers

---

### Post by Dry Lips on 2012-02-19
> **tj7572 said:**
> Hello folks,
 
I am thinking of switching from Windows to Ubuntu after hearing good things about the OS. So I tried the "live disc" version of Ubuntu 10.04 and didn't like what I saw. I have a few questions.
 
Ubuntu cannot locate my monitor, leaving horrible resolution. Will this be a problem when I install Ubuntu?
 
I would like to have dual-boot system with Windows 7, at least for a bit while I get used to Ubuntu. Is the dual booting as straight forward as the Ubuntu site makes it seem?
 
Anyone have a dual-boot and have problems?
 
 
Thanks for any info, cheers

You can change the resolution by going to system>preferences>monitors

Do you have a CRT monitor perhaps? If you have a nvidia or ati card, I would recommend installing the proprietary drivers upon installation. 
Go to system>administration>additional drivers

Dual booting is usually painless, but I would keep backup of important stuff just in case, before installing Ubuntu.

---

### Post by Mark Phelps on 2012-02-19
> **tj7572 said:**
> Ubuntu cannot locate my monitor, leaving horrible resolution. Will this be a problem when I install Ubuntu?
Yes ... it will.  While installing might correct a problem with video drivers, it will NOT solve the problem where the monitor is not even seen!
 
> I would like to have dual-boot system with Windows 7, at least for a bit while I get used to Ubuntu. Is the dual booting as straight forward as the Ubuntu site makes it seem?
From experience -- NO, it is nowhere as easy as it may seem.

While the process itself is not that hard, it runs the risk, if you make mistakes, of completely erasing Win7 and all your apps and data -- something that is almost NEVER mentioned.

If you're seriously thinking about dual-boot, then read the advice I provide below ...

You can also see the disk partitions if you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space. When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

