---
title: "[SOLVED] no login screen aftering installing 2d SATA drive"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by dansan on 2008-08-06
I run Gutsy, but startup no longer gets to the login screen.

I just installed a 2d SATA drive, which messed up grub. So I reinstalled grub as described in [https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4]("https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4") and then edited /boot/grub/menu.lst accordingly. 

This got me the gfxboot screen, which works normally to boot Gutsy, displaying the startup splash screen, but after that finishes, there is nothing but a black screen. First, I thought I'd hit a disk check, but the black screen continues unless...

... I press Ctrl+Alt+Backspace; then, Ubuntu shuts down: I get the reverse splash sequence and the machine reboots, but I never get the logon screen. Do I need to edit another file?

---

### Post by coolaj86 on 2008-08-06
Try rebooting and use the 'recovery mode' option. Then when it asks you tell it to try to fix X.

---

### Post by dansan on 2008-08-07
Thanks for the tip --

> **coolaj86 said:**
> Try rebooting and use the 'recovery mode' option. Then when it asks you tell it to try to fix X.

 -- but it's pretty hard to follow on Gutsy (my UbuntuStudio installation, anyway). When I choose "recovery", I am not asked about fixing X. I just wind up in Terminal at root.

The tip nevertheless got me to try fixing X, which eventually led to the following:

SOLUTION: Re-install gdm. As root I typed 

> apt-get install gdm and > apt-get remove

Then, I rebooted and everything was fine.

---

