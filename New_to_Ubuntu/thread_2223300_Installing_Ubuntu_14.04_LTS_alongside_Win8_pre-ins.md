---
title: "Installing Ubuntu 14.04 LTS alongside Win8 pre-install"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by suprleg on 2014-05-10
I've read several howto's that have been posted previously regarding a new Ubuntu 14.04 LTS install alongside  an existng pre-installed Win8 install and just want to confirm my information is current.
The computer is a new Lenovo H530 with Win8.

1.Create a LiveDVD of Ubuntu 14.04 "64bit"
2.Disable Quickboot/Fastboot, SRT, and FastStartup.
3.Set up firmware (BIOS) to boot the disk in UEFI mode
4.Install Ubuntu in EFI mode.
5.Use the automatic installer of Ubuntu ("Install Ubuntu alongside others") 

Any other thoughts, suggestions would be appreciated.
Thanks

---

### Post by oldfred on 2014-05-10
Backups, otherwise your procedure looks good. Some links in link in my signature include details & screen shots so you know what is going to happen.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by suprleg on 2014-05-12
FWIW, I would strongly caution anyone from trying a dual boot Ubuntu 14.04 LTS and Win8 on a (Lenovo H-series desktop with Win8 pre-installed). Lenovo uses a Spanish version of Win8, on their H-series desktops,  that lacks many options in the bios.
The UEFI/Legacy bios and the recovery partition make it all but impossible. I tried to accomplish a dual boot even though the documentation strongly suggested it was virtually impossible.
Even after applying all the reported workarounds and preparatory steps I was left with no usable OS of any kind.
I've since managed to get into the bios and was able to format and install Win7 pro and Ubuntu 14.04 LTS.
Thought I'd post this, hopefully it's helpful to someone.

---

