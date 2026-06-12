---
title: "Installing Windows and partition help"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by KevNice on 2008-10-13
I don't have any problems with Ubuntu, but I want to install Windows XP so that I can play world of warcraft.

I know I have to edit my partitions, but it won't let me edit them as they are. Do I need to unmount them first? Will doing so cause any problems?

Here is what it looks like:

**Partition _____       File System  _____      Mountpoint  _____     Size   _____         Used   _____        Unused   _____        Flag **

/dev/sda1   _____     fat16   _____  _____   _____  _____   ___                       78.41MB  __     7.21MB  __       71.20MB   _____     
/dev/sda2  _____            ext3  _____ _____       /storage  _____  ___ 130.85GB  _      77.79GB _       53.06 GB _____ 
/dev/sda4  _____     extended  _____  _____   _____  _____ _                        18.13GB  _____   ----  _____       -----   _____ 
/dev/sda6  _____     ext3  _____  _____        /      _____  _____   ____        14.93 GB  __    10.08GB  __     4.85GB _____   boot 
/dev/sda7  _____       linux-swap   _____  _____   _____     _____                    705.95MB  ___     ---  ___        -----   _____   
unallocated   _____      unallocated    _____  _____  _____ ____                      6.72MB  ____    ---  ___    -----  _____   
/dev/sda5   _____    fat32   _____  _____  _____  _____ _____      2.50GB  ___  737.63MB   ___      1.78GB    _____   



I want to take space from /dev/sda2 and make a new partition for windows. How do I do this? How much space would be enough? I will only use it for WoW. Also any tips on if and how I can clean up these partitions a bit to make them more efficient would be great.

Thanks

---

### Post by Orange_and_Green on 2008-10-13
```
sudo umount /storage
```

I don't think it will do any harm as that's not a system folder, as that's probably a place you have set up to keep your data on.

Then try System->Administration->Partition Editor, right-click on /dev/sda2 and resize. (It's wise to back up important data first, just in case). Use the empty space to set up a **primary** partition (/dev/sda3) as windows needs to be on a primary partition to boot.

If you don't have System->Administration->Partition Editor, you can install it with
```
sudo apt-get install gparted
```

WARNING: windows will overwrite the mbr with it's own boot loader, which (surprise surprise) is not compatible with Ubuntu, so after installing windows, keep your Ubuntu live CD handy and follow these instructions:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck :KS

---

### Post by Elfy on 2008-10-13
I assume that the fat16 is a recovery partition so you don't want to touch that. 

You'll have to do it either from the livecd, if you have hardy there is a partition editor on there, but personally I used [partedmagci]("http://partedmagic.com/") to do my partition work

What I would do is resize sda2 from the left so that the unallocated space is at the front of the hdd for xp to find.

Once it has been installed you will need to reinstall grub wither with the livecd or supergrub, both options are given here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Then you will have to add xp to your menu list.

---

### Post by bumanie on 2008-10-13
WOW should work in wine on 8.04 - [look here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329")

---

### Post by KevNice on 2008-10-14
Hey guys thanks a lot! All of the posts were very helpful :)

---

### Post by namegame on 2008-10-14
> **bumanie said:**
> WOW should work in wine on 8.04 - [look here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329")

This could be changing in the next month or so.

The next expansion will be out November 14th, along with it comes increased hardware requirements. I hope that the Wine developers can adapt to the change if need be.

---

### Post by KevNice on 2008-10-20
Have to bump this thread for a few simple questions...

Wine with WoW didn't work so I am going for the XP re-install after all. Couple easy questions for you:

1. I tried to boot off the Windows disk but it didn't work. I was just trying to check whether or not the XP CD that I had burned was functional. Am I correct to assume that I must first allocate disk space in gparted, create a new primary partition, before the CD will run at boot?

2. How much space should I allocate for XP? I just need it to run, and have enough space for WoW, the patches, and the two expansion sets. Would 20GB do it?

3. My current boot menu is messy. I am running Hardy 8.04 generic-21. But I still have boots for Gutsy on the boot menu, from generic-14 all the way up to 20. I clicked on one of them and it booted me up, meaning that these versions are still on my PC taking up space. How do I delete all of these? In addition, my old Vista/XP boot options are there too, even though neither are currently installed (neither boot works). How do I delete these off the menu?


I know these are a lot of questions but they are mostly n00b questions ;-)

---

### Post by KevNice on 2008-10-25
OK here is where I'm at...

I resized /storage and made a new 30GB primary petition (FAT32 filesystem). It's there in gparted but appears not to be mounted, and "sudo mount /dev/sda3" doesn't work.

I put in the (illegal) windows XP copy that I downloaded and made. However on reboot, it will not run the windows DVD. It just goes to the Ubuntu boot menu. Is this a problem with the DVD itself or with my boot settings?

---

### Post by Elfy on 2008-10-25
You're not going to get any help using illegal copies of xp.

---

### Post by bumanie on 2008-10-25
Although most of the forum members are not great fans of microsoft and its business practices, the use of illegal copies of microsoft products is not condoned. You shall have to work this out on your own unless you purchase a genuine microsoft product first.

---

### Post by KevNice on 2008-10-25
Well I'm only using it because I lost the install CD. Anyway, point taken, no worries.

---

### Post by KevNice on 2008-10-25
OK I did a search through all my CDs, because I was sure I lost the install disk, but I found a Windows recovery CD. However, this is Vista, which is what my computer came with, and not XP, unfortunately. **I assert that this is a legal copy of Windows Vista.**

Now, I had formatted 30GB of HD space, and made it fat32. When I went to install Vista, it said it was only compatible with NTFS, so I formatted it. But then I got a message saying that "the partition did not meet the minimum requirements for installing Vista." I logged back into Ubuntu and pulled up gparted, and it was changed to ntfs, but now there is a "!" caution flag for that partition. What's going on?

---

### Post by KevNice on 2008-10-26
Nevermind, I got it working, all it required was a re-start apparently. Thanks for everyone's input

---

### Post by bumanie on 2008-10-26
It may have helped if you had said you had a legal copy that had been lost - losing or destroying a disc (scratches etc.) is not hard to do. You must appreciate that we cannot give out information will-nilly if there is questions about the legitimacy of the software being used.

---

### Post by KevNice on 2008-10-26
yeah i know, I didn't think about that before I posted. It's fine though, I've got it up and working now anyway. Once I found my old copy it was a piece of cake!

---

### Post by hellawaitschrist on 2008-12-18
i got this vista install disc (it was burned for me) and the disc space i guess isn't enough (i deff. have more than 481MB on my computer).  im getting an XP-something or an other (burned)disc later in the day, any tips if the problem arises again, or will it?

---

