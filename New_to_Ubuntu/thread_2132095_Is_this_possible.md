---
title: "Is this possible?"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Dallas2coolio on 2013-04-03
I' am still new to using Ubuntu but I was wondering that if I did a full install and deleted my Windows 7 OS on this on a Sony notebook will I still have the system recovery so if I decide to go back to Windows 7 I can recover my system like new? My netbook had Ubuntu installed when I got it used so that's why I' am using it but I wanted to know if I can use it on my Win 7 system but just wanted to make sure that I can recover my system if I wanted to go back. I didn't want to leave two systems installed I wanted one at a a time but wanted to keep the Windows partition that's for recovery.

---

### Post by KnownSyntax on 2013-04-03
It depends on if you delete the partitions, if you did then it also depends on if there is a "ghost" drive on your notebook. If there is no "ghost" drive with the Windows 7 recovery located on it, then no you'll delete everything and have to end up re-installing it with a valid key since your OEM key will not work anymore (due to the OS not matching up perfectly with the OEM product key).
If anything just dual boot so you have the best of both worlds without ever worrying about having to lose one OS, or never having access to one or the other at a time.

---

### Post by agent-squirrel on 2013-04-03
One sure fire way of saving a recovery image is either to manually ghost the machine using somehting like Clonezilla Live. Or use Sony's built in recovery media creator and burn some recovery disks. 
That way even if you totally blast the machine and have no data on the disk, you have some dvds to recover from.

---

### Post by UltimateCat on 2013-04-03
When I go my Sony Vaio the first thing I did was burn the 'Recovery Media'
If you weren't able to do that Sony will provide you with 2-5 Recovery disc for a fee.

[http://sony.mytechhelp.com/?cpid=34139&gclid=CK-swcn-r7YCFWpnOgodnDoAgg](http://sony.mytechhelp.com/?cpid=34139&gclid=CK-swcn-r7YCFWpnOgodnDoAgg)

It's up to you what you decide but I have learned that it is much easier to install Windows on the Sony first.
Than install Linux.  That is; if you are interested in a 'dual boot'.

My Sony works amazingly in a dual boot with Windows 7 and Fedora!:popcorn:
But I had to shrink the Windows 7 partition first in order to install Fedora.

---

### Post by Dallas2coolio on 2013-04-03
Well are you able to adjust the size of hard drive space when you install both systems? I thought if Sony already made a set on the size you can't change it unless you delete the partition but then I think I would lose the recovery program meaning the press F10 feature to load recovery and to format and reinstall Windows 7.

---

### Post by AndyOpie150 on 2013-04-03
Another added note:
The Windows partition must be big enough to allow for at least 10GB of free space in it or it will not boot up. Chased my tail on that one for a couple of days until someone here mentioned it. 
I think there might even be a % of the total Hard Drive space rule for the partition as well.

 I only have 120GB. 35GB for Windows, 35GB for Xubuntu, and I'll use the rest for a BSD distrobution (need to learn more before that happens).
If you have the space: Dual Boot.
 I have a couple applications that are Windows only that won't run with Wine, so I still need the Windows partition every great now and again.

---

### Post by Dallas2coolio on 2013-04-03
Also I have Win 7 on my HD already since Sony came with it but I wanted to know that if I choose the have current system and Ubuntu on the side will that work when I load the CD? Also I don't know how I can adjust the size on the Win 7 that came with my notebook so it would have enough room for the Ubuntu.

---

### Post by Dallas2coolio on 2013-04-04
There is something weird but I tried loading the CD that has the Ubuntu OS that I downloaded that around around 700mb but my Sony notebook doesn't detect the CD it thinks it's a blank CD. On my netbook it works that has Ubuntu already on it but the Sony that has Win 7 doesn't think the CD has anything. I tried reloading it on another blank CD but same thing happens.

---

### Post by Baldrick_NZ on 2013-04-04
> **Dallas2coolio said:**
> There is something weird but I tried loading the CD that has the Ubuntu OS that I downloaded that around around 700mb but my Sony notebook doesn't detect the CD it thinks it's a blank CD. On my netbook it works that has Ubuntu already on it but the Sony that has Win 7 doesn't think the CD has anything. I tried reloading it on another blank CD but same thing happens.

You need to make sure you're burning the LiveCD as an image CD (.iso), otherwise it'll think it's either a blank CD our just show data files.

---

### Post by Mark Phelps on 2013-04-04
> **Dallas2coolio said:**
> Also I don't know how I can adjust the size on the Win 7 that came with my notebook so it would have enough room for the Ubuntu.

IF you're really interested in running a dual-boot with both Win7 and Ubuntu, then read through the material below BEFORE you start down that path ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by UltimateCat on 2013-04-06
Before I put Linux on my Sony Vaio laptop I first shrunk the Windows 7 partition.
[http://technet.microsoft.com/en-us/magazine/gg309169.aspx](http://technet.microsoft.com/en-us/magazine/gg309169.aspx)

Until I did that when I tried to install Linux the Live CD told me that there was not enough room.
> "Could not allocate requested partitions, not enough free space"


Most likely the reason why your Sony is not recognizing the CD is because your Sony is not set to boot to the CD ROM Drive--
When you first turn your Sony on press F2 until your BIOS comes up.
You will have to change the boot sequence for you Sony to see the DVD/CD -

---

