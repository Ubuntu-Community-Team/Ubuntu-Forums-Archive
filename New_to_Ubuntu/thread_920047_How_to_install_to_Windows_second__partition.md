---
title: "How to install to Windows second  partition?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by ubuntu1sttimer on 2008-09-14
Have a friend with a Dell Dimension 4700 & XP-Home that picked up something that killed Windows. 

He wants to try out Ubuntu 8.04 but retain Windows for some special programs. Doing Ubuntu alone is not an option. 

I wiped the 80 GB drive and reinstalled XP using it's partition option to split the drive into two 40 GB partitions. I installed XP on the first one and would like to put Ubuntu on the second.

However, I don't see a way to do it with the live CD and have not found a way mentioned on the forum.

Anyone have a way to do this? Would like to give him an intro to Ubuntu.

---

### Post by Ms_Angel_D on 2008-09-14
Check this out

[How to dual-boot XP and Ubuntu (with XP installed first)]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu")

---

### Post by doctorbighands on 2008-09-14
The setup you're asking for is known as a "dual-boot" system, and it's generally quite simple and straightforward to get it running.

[This tutorial]("http://www.psychocats.net/ubuntu/installing") should provide everything you need!

Hope this helps! :)

---

### Post by ubuntu1sttimer on 2008-09-14
Thank you both for your replies.

I did not explain what I needed as well as I should have. 

I have two 40 GB install partitions on the hard drive. Windows uses the first one on the HD and I want to install Ubuntu to the second 40 GB partition which is empty at this time. From what I have read and seen when I tried the live install disk, Ubuntu wants to use part of the partition that Windows already has and that is not what I am trying to do. I do not want to take any space from the existing Windows partition.

---

### Post by Tatty on 2008-09-14
There are several options for partitioning your hard disk on the installer.  The most commonly used option is to shrink an already-existing windows partition, which is why that appears as default.

To do what you are trying to do, you will need to select the "manual" option on the partitioning part of the installer.  There you can manually set up how you want your hard drive configured.

However, as you are new to ubuntu it will probably be easier for you to do it slightly differently (until you have a few installs under your belt anyway). 
Simply delete the spare 40Gb partition you have created, but leave the space unallocated.  That way when you install you can select the option "Guided - use the largest continuous free space", and ubuntu will automatically grab your unallocated space.

---

### Post by Sef on 2008-09-14
> I have two 40 GB install partitions on the hard drive. Windows uses the first one on the HD and I want to install Ubuntu to the second 40 GB partition which is empty at this time. From what I have read and seen when I tried the live install disk, Ubuntu wants to use part of the partition that Windows already has and that is not what I am trying to do. I do not want to take any space from the existing Windows partition.

There is a selection to use the largest free space.  Use either that or manually partition.

---

