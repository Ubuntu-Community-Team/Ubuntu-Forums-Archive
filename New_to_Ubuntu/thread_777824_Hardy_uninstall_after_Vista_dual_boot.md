---
title: "Hardy uninstall after Vista dual boot"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by yc2 on 2008-05-01
Hello,

I just bought an HP Pavillion DV 6751.eo (Vista Premium OEM) and burnt the recovery DVDs.

I want to install Hardy (dual boot) on it. Just as a precaution, I want to know how to uninstall Hardy. With the XP recovery disks one had to make "fixmbr" before removing Ubuntu partitions. However, when I start the HP Vista recovery disks I can only see total recovery opotions. (But I haven't checked in detail, I am afraid I run the recovery-program too far and start the actual recovery.)

**Can someone please tell me how to uninstall Ubuntu from this laptop, without reinstalling Vista entirely?**

Thanks :)

---

### Post by jrlii on 2008-05-01
I haven't tried it yet(all my Ubuntu machines are pure Ubuntu) but Hardy is said to have an option to install inside of Windows. 

Then if you don't like it, you could just use the standard Windows uninstaller. . . I'll bet it is much better behaved than most Windows apps, most of which leave a mess behind in the registry. 

Then if you like it you could set up a dual boot or wipe Windows and make it a pure Ubuntu installation. . .

---

### Post by yc2 on 2008-05-02
Thanks, I think it sounds like a good option for me to install inside Windows.

But WHERE DO I FIND THIS OPTION ??

I boot my Hardy CD and a traditional Ubuntu CD boot menu opens (black background, choose with arrow-keys):

Alt 1. Try Ubuntu (Works like Live CD)
Alt 2. Install ubuntu (Seems to install to hard disk directly with partitioning, I haven’t dared run it too far though.)
Other alternatives are not related to installation.

So, please tell me, where do I find the option “Install within Windows”?

Thanks

---

### Post by Paqman on 2008-05-02
Boot up into Windows, pop your Ubuntu CD into the drive and it'll autorun and give you a menu to start the Wubi installer.

---

### Post by yc2 on 2008-05-02
Thank you very much.
Why didn't I think of that ... :redface:

---

### Post by lassegs on 2008-05-02
The beauty of it is at after you have installed through Wubi you are able to uninstall it from the Windows Control Panel -> Add/Remove Programs.

---

### Post by yc2 on 2008-05-02
Yes, in my case it seems to be absolutely necessary to use the Wubi way.
If I use the traditional (partitioning) way of installing Ubuntu on my HP-Vista laptop, I WILL NEVER BE ABLE TO UNINSTALL UBUNTU WITHOUT SWEEPING THE ENTIRE DISC using the HP-recovery discs that I was asked to burn just after starting the computer for the first time!
Maybe I could get back the MBR to Vista bootloader by borrowing "real" Vista recovery discs from a friend. But as I understand the problem, the disks that HP makes me burn, will not be able to perform this function. As I understand the situation, it is strange by HP not supplying disks for selective recovery of the MBR. (Like ordinary Vista disks.)

---

### Post by zvacet on 2008-05-02
Maybe [this]("http://ubuntuforums.org/showthread.php?t=740221") can help.

---

### Post by yc2 on 2008-05-02
> **zvacet said:**
> Maybe [this]("http://ubuntuforums.org/showthread.php?t=740221") can help.
Thank you very much. Exactly what I needed. Now I can hopefully partition the HDD and dual-boot Hardy/Vista and if necessary, however unlikely, unistall Ubuntu without swiping the disk.

I am a little surprised the solution had to come through BitTorrent and not through HP, though :)

I am sure everything will go as planned and I will not have to uninstall Ubuntu, but old geezers like me like to use both belt and suspenders at the same time (as we Swedes say) ;)

---

### Post by yc2 on 2008-05-02
Another question which is related, but maybe not appropriate for this forum is:
Will Norton Ghost (12 or above) restore MBR and partition table? I have heard different replies to this question.

---

