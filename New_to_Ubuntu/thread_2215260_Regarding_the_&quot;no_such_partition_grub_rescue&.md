---
title: "Regarding the &quot;no such partition grub rescue&quot; problem,"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by chet2 on 2014-04-05
Can I use a usb or does it have to be a livecd? Also does it have to be the same version of ubuntu as I was using?

---

### Post by sikander3786 on 2014-04-05
You can use both a Live USB  or a CD/DVD, whichever available. And no, it doesn't need to be the same version but make sure it isn't very old. Grub2 was introduced in Ubuntu 9.10 and anything newer will do. I would prefer 12.04 and newer versions though.

Once booted into the live medium, follow "2nd option" from the page below and choose "Recommended repair":

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2014-04-05
For what? What are you thinking of doing? There is no difference between a Ubuntu ISO image burned to a DVD disk and one burned/installed on a USB memory stick. Either will do what you want, whatever that is.

My guess would be that Grub is trying to boot a Linux image from a partition that does not exist. You need to see what grub.cfg has listed for set root= Is it pointing to a partition that does not exist?

Grub use hd0 for the first hard disk and hd1 for the second hard disk and so one. Partitions are labelled  msdos1 for the first partition and msdos2 for the second partition, and so on. So, for Ubuntu installed in sda4 look for set root='hd0,msdos4' Ubuntu installing on sda2 would be set root='hd0,msdos2'

Regards.

---

### Post by chet2 on 2014-04-05
I uninstalled ubuntu and now I just want my computer to work. I have some commands from [this thread]("http://ubuntuforums.org/showthread.php?t=1359802") that are supposed to make my computer try to boot from the right spot.

---

### Post by sikander3786 on 2014-04-06
So, I guess you are trying to boot Windows and don't want to see the Grub menu on start-up, right?

If yes, you need to boot a Windows USB/DVD and perform startup repair:

[http://windows.microsoft.com/en-us/windows7/products/features/startup-repair](http://windows.microsoft.com/en-us/windows7/products/features/startup-repair)

It will fix any and all issues with your PC's start-up and you won't see the Grub menu any further.

If this is not the case and you want to achieve something else, please elaborate.

Thanks.

---

