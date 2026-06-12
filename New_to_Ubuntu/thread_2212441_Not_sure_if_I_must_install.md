---
title: "Not sure if I must install"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by Aslam_Chandlay on 2014-03-21
Hello,  
Everyone I wanted to know if I install Ubuntu with the side by side feature on a pc that already has Windows 7. Do I have to back up my data and reload the windows or can I just leave all my programs installed, and install Ubuntu side by side..... 

Thank you for your anwsers
Aslam

---

### Post by Mark Phelps on 2014-03-21
Welcome to the forums ...

You can install side-by-side, but do NOT take the option to install INSIDE, that is, while running in Win7; instead, use the option to install from the boot media.

It's always best to back up what you have before attempting this, as reinstalling Win7 and all your apps would be a LOT of work -- but it's not required.

Since you have Win7, you need to read through the details below BEFORE you attempt the dual-boot install:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Impavidus on 2014-03-21
You don't have to reinstall Windows, but make backups of your important files nonetheless. A Windows recovery disk may be useful, just in case something goes wrong. Use Windows tools to shrink your Windows partition and make unallocated disk space for Ubuntu (or install an extra drive), boot from the live disk and select the "install alongside windows" option if available. If you don't see that option, come back for further advice.

---

### Post by su:bhatta on 2014-03-21
Well as always, Mark Phelps & Impavidus are spot on. 

I will give 2 Help page links which might come in handy :

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

This next one has screenshots for better clarification : [https://help.ubuntu.com/community/GraphicalInstall#continueinstall](https://help.ubuntu.com/community/GraphicalInstall#continueinstall)

Also suggest, since it will be a Live DVD, first 'TRY Ubuntu', get a live session and see if there are any problems reagrding hardware compatibility and then install.

---

