---
title: "Installation on external drive messed up boot from internal drive"
date: 2020-11-15
forum: New to Ubuntu
---

### Post by pattyland2 on 2020-11-15
Hi there,

I wanted to try Ubuntu Desktop for quite a time and wanted to give it a go on MacBook.
To avoid *any* problems with my macOS and Bootcamp installation, I attached an external USB HDD and installed Ubuntu 20.04 there from an USB Stick.
The installation seems to work without any problems but as soon as I turn on my laptop, even with the external hdd disconnected, it boots to “grub” and I can’t boot macOS not Windows(boot camp).

How could this happened? I’m 100% sure I choosed my external drive during the installation. The different sizes made that easy.

What can I do to boot macOS? I need to work tomorrow and I’m missing thousand of files...
(Yes I’ve time machine backups but I this would by my last resort...)

---

### Post by Impavidus on 2020-11-15
It looks like the bootloader was installed on the internal hard drive. It's a known problem with UEFI installs on drives other than the first drive. Is this a system running in UEFI mode? I don't know when Macs switched, but if less than 6-10 years old, it probably is. Can you access the UEFI and select the original bootloader? They should exist side by side.

---

### Post by pattyland2 on 2020-11-17
Sorry for the late reply, apparently I don't get emails when replying to my own thread. I had already recovered my data from the backup...


Oh God, this is a known problem? Why don't I get at least 20 warning banners during the installation?
Regarding UEFI: I don't know what's running on the MacBook, but if I hold down the ALT key during startup I can select macOS and boot, luckily.
How can I delete GRUB again? It's annoying that I can't boot my laptop normally anymore.

---

### Post by MartyBuntu on 2020-11-17
You need to repair the Mac's bootloader. Not familiar with Macs....maybe someone could chime in.

---

### Post by pbear42 on 2020-11-18
> **pattyland2 said:**
> 
Oh God, this is a known problem? Why don't I get at least 20 warning banners during the installation?
A better question is, why hasn't it been fixed?  The bug has been around for seven years or so.
> How can I delete GRUB again? It's annoying that I can't boot my laptop normally anymore.
Don't have a Mac, but on another forum saw this suggestion, "Once you are booted to MacOS, got to System Preferences > Startup Disk, and click to select the internal hard drive (you may need to unlock the panel with your password)."  Take a look and see whether that gets you where you want to go.

---

### Post by sudodus on 2020-11-19
**Live system:**

The easiest alternative (with for example [mkusb](https://help.ubuntu.com/community/mkusb)) is to clone from the iso file to a USB drive and get a **live-only** drive. Things will not be saved, so I don't think this is what you want.

The next alternative is to use (with for example [mkusb](https://help.ubuntu.com/community/mkusb)) to create a **persistent live** drive. This is also rather easy, and you get a system that is portable and you can install application program packages as well as save files. But you cannot upgrade the kernel and the kernel drivers.

**Installed system:**

It is more complicated to install Ubuntu like into an internal drive, but into a USB drive, but it is not too difficult, and this way you can also get a portable system (between computers). Such an installed system can be updated & upgraded like any installed system, also the kernel and its drivers can be kept up to date. I think this is what you want, and you can find advice via [**this link**](https://askubuntu.com/questions/1267370/can-i-install-ubuntu-in-a-usb-stick-and-run-it-as-my-learning-machine-will-it-r/1267376#1267376) **and links from it**.

In particular, the link (and links from it) helps you avoid writing to the internal drive. In short: If you use the installer, please unplug, disconnect or otherwise disable the internal drive during the installation process. 

Otherwise (if it is difficult to disable the internal drive) you can [expand and clone from a compressed image](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203) of an installed system, which helps you work around the problem (bug) with the installer.

---

### Post by pattyland2 on 2020-11-21
@MartyBuntu: That would be great. I have no clue what to do


@pbear42: Very good question... I think that's a pretty severe bug. I installed macOS and several Windows versions 100 times, aber never ever it messed up bootloaders of other drives! I tried "System Preferences > Startup Disk", I got 2 Disk there, my macOS Partition and my Windows Partiton. No matter what I select, I get 100 error messages and then the grub command line. If I type "exit" there, macOS starts. So I cannot start my Windows at all...


@sudodus: Thanks for the tips. 
live-only: No, I don't want that
persistent live: I thought about it, but I was deterred that you can't install any drivers. My WLAN does not work with Ubuntu ootb and I have to install some things
I have absolutely no idea how to get the SSD out of my MacBook without a soldering iron.
The solution with cloning sounds like the only reasonable solution, even if I find it messy and complicated.


I have always recommended Ubuntu to friends and family as very beginner friendly, this experience here was terrible.


Before I start thinking about a new installation I would like to fix my bootloader...

---

### Post by oldfred on 2020-11-21
If you partitioned in advance & included an ESP - efi system partition on external drive, then you just need to reinstall grub2's boot loader to external drive.

This is now an old bug, but unless users keep complaining they will not do anything.
Please add to the bug report.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

