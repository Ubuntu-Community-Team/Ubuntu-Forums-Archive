---
title: "install Ubuntu on a HP laptop with windows 7"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by vibaviattigala on 2013-04-12
i got a laptop last month 

HP pavilion g6-2144tx

cpu core i7 3632QM 2.2 GHz
ram 8GB ddr3
VGA amd radeon Hd 7670m 2GB dedicated+intel HD graphics
750GB hard disk

i have a recovery partion given by HP it has all the drivers + windows 7

and i have 2 extra pations both contains about 200GB each
i am planing to install ubuntu 13.04 on 18th
they are saying we cant install ubuntu from WUBI
how do i install ubuntu without harming to the windows 7 +recovoery partion


what do i download 32 Bit or 64 bit is it possible to put the 64 bit to that laptop?
then how about that dual graphics drivers ?
usb 3.0 drivers??/
etc

---

### Post by coldraven on 2013-04-12
Even if you are not going to install Ubuntu you should make restore CDs using the Windows tools.
Or you could clone the restore partitions using Clonezilla.
Either way you probably need to free some space on your drive. You could shrink a Partition but this might break your Windows installation.
I do not have any experience of Win7. My HP laptop came with XP and restore partitions, after making restore CDs I deleted the lot and run XP in a VM.

---

### Post by Feathers McGraw on 2013-04-12
I can sympathise, I recently did something similar with my HP laptop. HP seem to think that just because you can have up to 4 primary partitions they should always use them all, filling them with things like "HP Tools":mad:.

So...am I right in saying you have 4 primary partitions? You'll be able to see this from within Disk Management in Win 7.

i.e. Windows 7 | Win 7 Recovery | "Extra partition" 1 | "Extra partition" 2 ?

If so I think you'll need to free up a primary partition, as you can only have four [more info on partitions here]("https://help.ubuntu.com/community/DualBoot/Partitions").

The best way to do this depends on what's in your "extra partitions".



In the meantime, I'll tell you what I did just in case it appeals (it has the benefit of removing all of HP's bloatware, and backing up should be quick and simple if the laptop is new):
1. Unless you have your product keys already: Download Belarc Advisor (Win7) and use it to find your product keys for things like Office and Win7 itself. Write the whole lot down or print it!!
2. Make fresh Win7 boot disk or bootable usb drive (for the version you have currently - e.g. home premium 64 bit)
3. Make an Ubuntu boot disk or bootable usb drive
4. Back up all your important files (shouldn't be a big deal if you've only had it a month)
5. Make a fresh installation of Win7, apply all updates etc.
6. Use the Ubuntu boot disk to install Ubuntu alongside Windows using the recommended settings.
7. Enjoy Ubuntu alongside a faster, less bloated Win7

Note after installing Ubuntu, the first time you try to boot into Win7 it will perform a disk check - don't panic ;)




Hope this helps,

Feathers

---

### Post by mastablasta on 2013-04-12
not sure if the graphics will work ok but you will need to install proprietary drivers. you might also need to use one of the boot parameters to boto into the syste.m it would be good to try it in live mode first anyway.

you have a 64bit CPU so you can use 64 bit version of the OS.

most drivers in linux are inlcuded in kernel (except from a few proprietary graphics, printer and WI-FI drivers)

---

### Post by zrdc28 on 2013-04-12
Before you do any of this you need to defragment your hard drive, I always do it 2 times for safety.  
[B][http://windows.about.com/od/maintainandfix/ss/SBSdefragWin7_all.htm](http://windows.about.com/od/maintainandfix/ss/SBSdefragWin7_all.htm)
[/B]
The next thing you need to chkdsk  /f . you will need to reboot after this and give it time to check disk for errors.
The easy way to chkdsk in win7 is.
[B]Open the "Computer" window
Right-click on the drive in question
Select the "Tools" tab
In the Error-checking area, click <Check Now[/B]

Now you are ready to shrink the partician, I always choose the largest partician that way you won't bother the recovery or boot.
be sure you write down the name and size of the partician.
**[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)**,

Now when you install ubuntu you will have a nice clean install. Be sure to add a swap partician of 2 times the size of your memory.

---

