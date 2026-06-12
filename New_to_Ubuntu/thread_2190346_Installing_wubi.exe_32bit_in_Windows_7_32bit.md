---
title: "Installing wubi.exe 32bit in Windows 7 32bit"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by mdavis1231 on 2013-11-26
Is anyone besides me having trouble installing wubi.exe 32bit in Windows 7 32bit?  It installs, goes through the initial loading screen, but when it gets to the login screen, it freezes, then goes to a purple screen.  Help! ](*,)

---

### Post by oldfred on 2013-11-27
That may just be that standard video issues we all have whether wubi or a standard partitioned install.
You probably need to add no modeset to linux line in grub menu.
At grub menu use e, scroll down to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Realize 12.04 is the last version of wubi supported. Wubi does not work with gpt partitioned drives which all new Windows 8 systems have. 
Alternatives then are to just run as a live version with persistence on from a flash drive. Not quite as fast as hard drive but fully functional for testing which is the purpose of wubi. Wubi is not for long term use.
Or even a full install to a larger flash drive.

---

