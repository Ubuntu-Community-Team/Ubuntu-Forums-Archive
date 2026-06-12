---
title: "Need help setting up wifi and removing W7."
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Wildedog on 2013-02-19
Hello, I just installed Ubuntu 12.10 with the windows installer. I'm a complete linux nub. (Just found how to get to the terminal.) I've been searching the forums for other posts like mine and been having trouble following them so I'd figure I'd get some specific help. I have a Dell Inspiron 1525. I think my wifi card is a Broadcom 802.11 (BCM4312 802.11b/gLP-PHY. What do I need to do?

Also I have Windows 7 on the laptop and I would like to remove it. Could you please give me instructions on how to do so. Would this make the computer faster and Ubuntu faster by removing it?

When I log in with Ubuntu it will say the old owners name of the laptop from the Windows 7 OS. Also how could I change that? 

Sorry for all the questions. Thank you so much for reading.

---

### Post by kurt18947 on 2013-02-20
I am no expert but from what I read, I suspect you have a WUBI install.  You can't remove Windows 7,  Ubuntu is essentially running as a Windows 7 program.  Are you able to restore Windows 7?  Do you have a  restore DVD or functional restore partition?   I would not be in a tremendous rush to nuke Windows 7 unless disk space is limited.  Personally, I would delete the Ubuntu WUBI install.  I think it's found where other Windows programs are but I haven't used it.  

Once you have Windows 7 without Ubuntu, run defrag once or twice then shrink the Windows partition using Windows' tools.  You don't want to shrink the Windows partition too much.  If the Windows install were occupying say 20 GB, I wouldn't make the windows partition smaller than 40 GB.  Then install Ubuntu *beside* Windows 7, not *inside *Windows 7.  On startup, GRUB should present a choice to boot either Ubuntu or Windows 7.  

One possible complication with this is number of partitions.  Some preinstalled windows setups have more than 1 partition, they can have up to 4 which are all that  are allowed on machines that don't implement UEFI.  The solution is usually to copy the contents of one or more partitions to DVD or into another partition  then delete it.  You only really need one partition to install Ubuntu,   A swap partition is not really required if you have enough RAM installed, IMO 2 GB minimum, 4 GB is better. You can also create a swap **file** which doesn't use up one of the 4 partitions.  You can suspend without a swap partition but to hibernate requires a separate partition.    I use something called BootItNG which gets around the 4 partition limit while using traditional (Non-UEFI) disks.  That has been reliable for resizing Windows partitions  and booting multiple operating systems - it will support 100+ O.S.s - but BootItNG and newer BootItBM have their peculiarities too.

---

### Post by Wildedog on 2013-02-20
No I dont have the restore cd.

I was just wanting to have Ubuntu as the only operating system on this computer. Could I wipe the hard drive and then install Ubuntu via USB flash drive?

If so how would I go about wiping it?

---

### Post by varunendra on 2013-02-20
Hi Wildedog, Welcome to the forums! :)

Please use normal fonts for posting. Bold and coloured fonts are meant for highlighting only **parts** of a post. Entire post in such a font makes it difficult to read.

Onto your question-

> **Wildedog said:**
> I think my wifi card is a Broadcom 802.11 (BCM4312 802.11b/gLP-PHY.
Let us confirm that. Open a terminal, and run the following command (you may copy-paste to avoid typo)-
```
lspci -nnk | grep -iA2 net
```
and post back its output in your next post.


Onto your question about installation / partitioning-

> Also I have Windows 7 on the laptop and I would like to remove it. Could you please give me instructions on how to do so. Would this make the computer faster and Ubuntu faster by removing it?
I wouldn't recommend to remove Windows until you are comfortable enough with Ubuntu. By your way of asking questions I'm guessing you are not.

Also, removing or keeping windows will NOT make any difference in performance of Ubuntu. However, if yours is a WUBI installation *(WUBI is the installer on the live cd that installs Ubuntu from within windows just like a program)*, then doing a proper installation *(done by booting from cd/usb and installing Ubuntu on its own partition)* will definitely improve its performance.

To confirm whether you have a WUBI installation or a normal one, please post the output of following command-
```
sudo fdisk -l
```
It will ask for your password. Type in the one that you use for login. You won't see anything on the terminal while typing the password, just type it correctly and press Enter.

> **Wildedog said:**
> No I dont have the restore cd.

I was just wanting to have Ubuntu as the only operating system on this computer. Could I wipe the hard drive and then install Ubuntu via USB flash drive?
While you can certainly do so, I'd strongly recommend to keep it until you are confident enough with Ubuntu. At least create a set of backup DVDs from Control Panel > Backup & Restore *(or something similar, I don't remember that exactly)* before doing anything destructive. Even if you decide to keep windows, I'd recommend creating them anyway. Just in case anything goes wrong or you need windows back.

Once you have the backup DVDs in hand, you may boot from USB and choose the option to wipe out entire hard disk and install Ubuntu alone.

Be aware that doing so will also wipe out all your data on the hard disk. Let us know if you want it otherwise.

---

### Post by kurt18947 on 2013-02-20
Varunendra gives excellent advice.  There are some things for which there simply is no Windows substitute.    Updating firmware on hand held gadgets like cameras and GPSs are examples that come to mind.  There was a firmware upgrade for my Brother printer.  Guess how it came?  As an .exe file which *might* run with WINE but I sure wouldn't bet on it.  Another example for me is formatting USB flash drives to run live OS installs.  Gparted will create FAT32 partitions, no problem, right?  

On three machines, no problem.  On the fourth machine, the flash drive MUST be formatted to FAT32 on a Windows machine in order to boot.  Why?  I have no idea.  FAT32 partitions created with gparted and FAT32 partitions created on Windows look the same, have the same boot flag but something is different.  The boot part of the modular BIOS on the problem machine was supposedly written by Microsoft so who knows.  The point of this rambling is to think long and hard before nuking Windows entirely.  Shrink the partition? Sure.  At least look into creating backup DVDs so you could restore if necessary.

---

### Post by nhasian on 2013-02-26
If your wifi still isn't working try this terminal command:

```
sudo apt-get install bcmwl-kernel-source
```

Let me know if that gets you up and running

> **Wildedog said:**
>  I have a Dell Inspiron 1525. I think my wifi card is a Broadcom 802.11 (BCM4312 802.11b/gLP-PHY. What do I need to do?


---

