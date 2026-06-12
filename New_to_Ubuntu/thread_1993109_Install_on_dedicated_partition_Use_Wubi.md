---
title: "Install on dedicated partition: Use Wubi?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Yora on 2012-06-01
I have a Windows XP PC and want to add Linux.

The Hard Drive has three Partitions:
c:\ 100 GB, Windows, browser, media players, etc.
d:\ 100GB, set apart for Ubuntu, plus browser, media players, etc.
e:\ 730 GB, all my personal files and also the few occasional games I play on Windows.

Should I use Wubi to install Ubuntu 12.04 on what is now still the d:\ partition? I've done some search and read that Wubi is for temporary trial instalation on the same partition as Windows and not for permanent dual OS setups like this. But then the Ubuntu-website says I should use Wubi.
Yes?
No?
Something else?

Also, I still need to format d:\. What type of File System should I use? I have FAT, FAT32, NTFS, EXT2, and EXT3 available.

I also do have an external USB Hard Drive, but that one only caused trouble for the last 30 hours I tried to get Ubuntu running. I could completely whipe it and set up a new USB-Installer-Thingy if it really has to be, but I would need some additional assistance with how to set this up. The LiveUSB version that is on it now never worked in attempting to make an installation on the internal Hard Drive, it was always broken beyond use, unable to get a network connection set up.

---

### Post by Megaptera on 2012-06-01
Wubi is installed *within* Windows - so it would have to reside in Windows in your C drive.
You don't *have* to use Wubi before moving to a more traditional dual boot - it's only a stepping stone for those who want to *try* without partitioning.

Whatever you decide - make backups of your important docs,pics tunes etc to external media beforehand just in case.

---

### Post by yeats on 2012-06-01
> **Yora said:**
> I have a Windows XP PC and want to add Linux.

The Hard Drive has three Partitions:
c:\ 100 GB, Windows, browser, media players, etc.
d:\ 100GB, set apart for Ubuntu, plus browser, media players, etc.
e:\ 730 GB, all my personal files and also the few occasional games I play on Windows.

Should I use Wubi to install Ubuntu 12.04 on what is now still the d:\ partition? I've done some search and read that Wubi is for temporary trial instalation on the same partition as Windows and not for permanent dual OS setups like this. But then the Ubuntu-website says I should use Wubi.
Yes?
No?
Something else?

I would say no.  Just install boot into the Ubuntu installation disk/usb and install to the space you've selected.

> Also, I still need to format d:\. What type of File System should I use? I have FAT, FAT32, NTFS, EXT2, and EXT3 available.

What you're calling "d:\" is where you're installing Ubuntu, right?  If so, I would just let the installer take care of the partitioning.

> I also do have an external USB Hard Drive, but that one only caused trouble for the last 30 hours I tried to get Ubuntu running. I could completely whipe it and set up a new USB-Installer-Thingy if it really has to be, but I would need some additional assistance with how to set this up. The LiveUSB version that is on it now never worked in attempting to make an installation on the internal Hard Drive, it was always broken beyond use, unable to get a network connection set up.

Not sure what you're trying to do here...  If you provide some more details about what you're after, someone may be able to assist.

---

### Post by Yora on 2012-06-01
Now that clears up a lot of confusion. ^^

When I start the OS on the portable USB-drive, I can chose the options "Run OS from this USB drive" and "install OS on a hard drive". I also have a desktop icon on the portable OS "Install Ubuntu 12.04 LTS", which I also assumed is used to install Ubuntu on a Hard Drive.
However, both options ended with an Ubuntu installation on the hard drive that lacked USB-Mouse support, network access, and use of the graphics card, and any attempt to remvove and reinstall "xserver-xorg" failed with an error message about missing or broken packages, so I assume the installer that is now on the portable drive is corrupted in some way.
So I want to install Ubuntu directly on the hard drive, using the USB drive just in the same way as an installation CD.

I'm currently trying to figure that out, but if someone can point my directly to the instructions or give a short step by step list, that would be highly appreciated.

---

### Post by Yora on 2012-06-01
Okay, now that I used Lili to prepare the USB drive everything worked perfectly!

They may make this important difference a bit more visible on the main download page.

---

