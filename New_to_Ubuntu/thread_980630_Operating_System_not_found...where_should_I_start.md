---
title: "Operating System not found...where should I start?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by jdpatt on 2008-11-13
I installed Ubuntu 8.10 on an older laptop.  When I finished and rebooted the computer, I get the error message "Operating system not found."  It boots fine from the CD.

My first thought is that my hard drive was bad, as it's not recognized in the BIOS.  However, once I boot up from the CD, the hard drive is visible and accessible. 

Basically, the computer won't see the hard drive when booting, but once Ubuntu is running, it seems to be fine.

Any recommendations?  I did a search, but it seems the answer is usually a bad hard drive, which mine doesn't seem to be.

Dave

---

### Post by baeksu on 2008-11-13
Have you made sure grub is installed? It seems that the BIOS has no problem finding the hard drive, it's just that there's nothing bootable there (hence "Operating system not found" instead of "hard drive not found" or something similar).

If you have all the necessary files in your boot folder, you can use the following guides to restore grub on the mbr:
[HOWTO: Restore GRUB (if your MBR is messed up)](http://ubuntuforums.org/showthread.php?t=76652)
[Using the Unofficial "Super Grub Disk"](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Unofficial%20%22Super%20Grub%20Disk%22)

---

