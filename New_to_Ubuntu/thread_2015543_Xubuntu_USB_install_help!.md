---
title: "Xubuntu USB install help!"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by django0909 on 2012-07-03
Hi, 

Trying to install Xubuntu via USB onto an Asus EEE PC. It has two SSD hard drives, one 4GB one 8GB, currently has Winxp on the 8gb drive. Trying to install to the 8GB drive using wubi with the boot from CD helper software, which caused one SSD drive to run out of space. Wubi refuses to run again as it says there is a 'previous install' on the drive, even though Winxp isn't seeing it - not in a hidden folder.

When I try to boot the machine without the CD boot helper it gets as far as a black screen with a blinking cursor in the top left corner but that's it. Really frustrating me - don't know where to go! The machines BIOS recognises all drives and POST sees the memory....(2GB DDR2).

help!!

---

### Post by bcbc on 2012-07-03
Wubi doesn't work well with USBs. It copies the partition as the ISO (so instead of copying the 700MB ISO it copies whatever the USB partition size which could be 4GB or even higher). Uninstall it via the Control Panel, Add/remove programs, "Ubuntu".
Or look in C:\Ubuntu and remove the ISO.

Wubi says there is a previous version whenever you try to install a second time, because the first time it saves a bunch of stuff (to enable uninstalling) like registry entries and the uninstaller etc. So even if Ubuntu didn't get successfully installed, Wubi will still have some remnants that need to be removed.

Finally, what exactly are you trying to do. If you have an 8GB drive with XP on, there's not exactly any room for Ubuntu. And it's not clear whether you are intending to install with Wubi or as a normal dual boot (that's what the CD boot helper does). I don't even know if the CD boot helper will work with the USB as it's a seldom used feature that isn't well tested.

---

