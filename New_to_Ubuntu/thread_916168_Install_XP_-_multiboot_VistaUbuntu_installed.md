---
title: "Install XP - multiboot Vista/Ubuntu installed"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by dbremer on 2008-09-10
I want to install XP on my system.  I have Vista 64bit and Ubuntu 8.04 already installed.  I use the Grub boot loader.

I saw this thread discussing the same issue: [http://ubuntuforums.org/showthread.php?t=535111](http://ubuntuforums.org/showthread.php?t=535111)

This was posted 1 year ago.  Is there any new or better advice since that time?

Here is my configuration:

Drive 1: 500GB drive -  Vista (dev/sda1) Ubuntu (dev/sda2) another install of Ubuntu (dev/sda3)  
Drive 2: 500 GB drive  - formatted ntfs (dev/sdb1) ext3 (dev/sdb2) ext3 (dev/sdb3).  

I want to install XP on the dev/sdb1 partition.  Any advice?  

Do I just boot the XP disc and tell it where to install, or do I have to boot into the partition I want it installed upon?

If I have to reinstall Grub, I think that would not be a problem.  This thread seems to cover that part: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I am new to Ubuntu and partitions, having only used them for one month.  I have to use Windows for work, so a complete transition is not possible.  I use Ubuntu 100% for my personal computing.

---

### Post by roquefilipe on 2008-09-10
yah, that first thread seems to cover it. The ideia is that windows just doesn't care about linux so the windows bootloader will substitute Grub (the linux bootloader), so the order is first windows then linux.

Also be aware that I don't know of which imcompatibilities there may be with XP and Vista, meaning that I don't know if the XP bootloader can see the Vista install.

---

### Post by dbremer on 2008-09-10
Thanks for the advice.  I'll try installing XP from the instructions on that thread that post my results.

---

### Post by SunnyRabbiera on 2008-09-10
just be careful, XP's partitioner might wipe off both Vista and Ubuntu in full, make sure to back up!

---

### Post by dbremer on 2008-09-10
I was afraid that the XP install might wipe my drive.  Thanks for the words of caution.  I've got an extra 500GB drive that I'll use to Ghost an image of my original drive and then test the install on the ghosted drive.  

Does anyone know a good open source or Ubuntu tool for imaging a drive?  I used Norton Ghost, but I'd prefer to use something open source.

---

### Post by dbremer on 2008-09-27
My advice to everyone is to install XP first, on the first drive, on the first partition.  I could have save myself alot of time if I'd done that.  Basically, when I installed XP onto the first partition on the second drive, with Vista already installed, I was unable to access Vista.  I didn't lose any files because I backed everything up first.  I followed numerous suggestions from other postings and nothing worked for me.  After hours of failed attempts, I erased the Vista partition and installed XP there- the first partition of the first drive.  At a later date I might try to install Vista on the second drive.  If I attempt that install I will update this thread.

Reinstalling Grub and accessing my Ubuntu systems was never a problem and took two minutes to reconfigures.  No one should be afraid of an XP install over existing linux systems, just make sure you have an Ubuntu live cd to boot from to reconfigure the Grub bootloader.  Without the live cd you're going to have problems.

---

### Post by Xiong Chiamiov on 2008-09-27
> **dbremer said:**
> Does anyone know a good open source or Ubuntu tool for imaging a drive?  I used Norton Ghost, but I'd prefer to use something open source.

I've used [Partimage]("http://www.partimage.org/Main_Page") successfully.

> **dbremer said:**
> Without the live cd you're going to have problems.
Or [Super Grub Disk]("http://www.supergrubdisk.org/")

---

### Post by bumanie on 2008-09-27
To triple boot with vista/xp/ubuntu, the easiest way is to install vista first, followed by xp. xp will overwrite vista's bootloader (they are different). You then have to recover vista's bootloader with a recovery dsik. During the recovery, vista should recognize xp's bootloader and add xp's bootloader files to it's own bootloader files, giving you the option of booting into vista or 'an older version of windows'. That being done and (hopefully) working correctly, install ubuntu as normal for a dual boot system procedure or if already installed, reinstall grub.

---

### Post by kansasnoob on 2008-09-27
> Drive 1: 500GB drive - Vista (dev/sda1) Ubuntu (dev/sda2) another install of Ubuntu (dev/sda3)
Drive 2: 500 GB drive - formatted ntfs (dev/sdb1) ext3 (dev/sdb2) ext3 (dev/sdb3).

I want to install XP on the dev/sdb1 partition. Any advice? 

First of all, I personally prefer having ALL operating systems on one drive. Why? Because I don't like drive mapping:

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

You'd do well to study this whole tutorial:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If I were forced at gun-point to do what you want to do I'd unplug drive sda and then install XP to drive sdb. Then, well you didn't say if you're using Vista's bootloader or Grub, but assuming you're using Grub I'd "map" the new sdb (XP) Os into the existing Grub.

---

