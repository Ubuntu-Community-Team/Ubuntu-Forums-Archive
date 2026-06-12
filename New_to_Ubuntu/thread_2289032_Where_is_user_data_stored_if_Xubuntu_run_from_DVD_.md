---
title: "Where is user data stored if Xubuntu run from DVD or Flash Drive?"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by jerry49 on 2015-07-31
I have a installation (.iso) DVD and when booting to the DVD on a current XP Dell Desk Top I am offered to "Try" and to "Install"... if I try no changes are made to my PC, I understand,  but as the DVD is readonly what happens to user data (say a Thunderbird folder) when Xubuntu is shut down?  Or, does Xubunt run from DVD (or perhaps faster? Flash Drive) create a Windows recognized "folder" on the HDD that Xubunt can return to on the next boot up?

---

### Post by sudodus on 2015-07-31
If you run a regular live session - simply boot from the DVD drive, the data are stored temporarily in RAM, and they are discarded at reboot and shutdown.

If you create a casper-rw file or partition in a writable device (internal or external hard disk drive, SSD or a USB pendrive), the data from RAM are copied to an overlay file system and stored in the casper-rw file or partition. This is called a persistent live system.

See more details at the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot](http://ubuntuforums.org/showthread.php?t=2259682)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

