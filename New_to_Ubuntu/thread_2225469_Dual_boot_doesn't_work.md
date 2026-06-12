---
title: "Dual boot doesn't work"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by eduarda2 on 2014-05-21
I tried to dual boot ubuntu 14.04 with windows 7. When i reboot my computer, a purple screen with a small white drawing appears and that's it! It stays there forever. Ubuntu never loads. Does anyone know how to solve this?

---

### Post by oldfred on 2014-05-21
What video card/chip?

Often a video issues and adding nomodeset lets you boot into low quality graphics until you install proprietary driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

