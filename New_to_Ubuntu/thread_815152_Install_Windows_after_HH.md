---
title: "Install Windows after HH?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by webcoded612 on 2008-06-01
I installed WinXP fresh yesterday, thinking I'd reboot and use the HH install disk to resize the Windows partition.  Installer won't do that for me (said, helpfully, "Due to an unknown error, this partition cannot be resized"), so I went ahead and did a clean install of HH, wiping the Windows install (I'll go Linux before Windows anytime).

My question is this:  is there anyway to resize the partition from Linux and install Windows on the newly created partition without losing my HH install?  I want to play games, but Linux has no 3D support (for my vid card, anyway...ATI Radeon X1300 PCI-E).  

Can this be done?  I've read about gparted and such, but I also read that GRUB breaks when you install Windows after Linux.  

Any help would be wonderful.  :)

---

### Post by SunnyRabbiera on 2008-06-01
Its possible as long as you have the partition marked as blank.
Windows usually goes after the whole hard drive though, but with any luck it will just install on the most logical partition, your blank one.

---

### Post by sayakb on 2008-06-01
If Grub breaks, you can have it back by using [SuperGrub]("http://ubuntuforums.org/www.supergrubdisk.org/") Disk.

---

### Post by webcoded612 on 2008-06-01
I'm wondering...why wouldn't Linux resize the XP partition?  I'm using the ALT disk...would that make a difference?  A friend has almost the same system I do, and it worked for him using the regular install disk.  

I really want to keep Linux, but until it gets proper 3D support, I need Winblows.  

I also had another idea:  Couldn't I install Win XP, creating a new partition at install that's only part of the HDD, then go back and install Linux on the leftover space?  How would this affect GRUB?  

*Bangs head on keyboard*  Why can't this be easy?  *cries*

---

