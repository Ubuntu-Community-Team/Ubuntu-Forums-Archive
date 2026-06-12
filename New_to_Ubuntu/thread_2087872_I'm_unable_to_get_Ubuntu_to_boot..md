---
title: "I'm unable to get Ubuntu to boot."
date: 2012-11-24
forum: New to Ubuntu
---

### Post by bacoon on 2012-11-24
My apologies for the alpha noob question. I'm brand new to Ubuntu and Linux... I've set up a dual boot (Windows 7 - Ubuntu) but when I choose Ubuntu on my boot screen, I'm presented with a CMD like screen asking for GNU GRUB commands?
This is most probably a really easy fix and I'd warmly welcome any response so I can experience Linux!  
If it helps, I installed using WUBI and not from a disk/usb.

Thank-you in advance!

---

### Post by Bashing-om on 2012-11-25
bacoon; Hi ! Welcome to the forum.

Regret the delay in responding, I do not use windows and my advise is limited to directing you to links with the needed instruction.
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#")
[https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)

and great docs - all about grub2 -:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Have a good read, post back with any queries for additional help.
[INDENT][INDENT]Just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2012-11-25
Just a quick heads-up --- have not used Wubi in a long time, but it has not historically used GRUB because that requires installation in a Linux filesystem.  Instead, it has used GRUB4DOS -- which is installed in the Windows filesystem.

IF you follow any of the guides and FORCE the installation of GRUB, not only will that NOT fix your  problem, it could also prevent Win7 from booting. Consider the following quote from the Wubi Guide: 
> Cannot boot into Ubuntu

Never try to correct Wubi boot problems by reinstalling Grub2. This will prevent Windows from booting and will not fix the Wubi install.

Read the section on troubleshooting and try the things the Guide suggests:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

