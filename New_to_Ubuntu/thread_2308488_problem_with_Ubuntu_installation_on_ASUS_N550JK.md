---
title: "problem with Ubuntu installation on ASUS N550JK"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by 1ns1d3r on 2016-01-03
Hello everyone,

I have a non-trivial problem (as I think) with installation Ubuntu (I tried 14.04 and 15.10) on my notebook (ASUS N550JK with GeForce 850M).

First I am trying install Ubuntu from USB flash: bootable flash have been created with Universal USB Installer. and I caught many ... SCHED_ERROR ... - there is some information that option "nomodeset" could help with this and it worked. After installation sometimes OS doesn't boot and sometimes OS hangs up. I really don't know how to solve this problem... May be there are errors with creating bootable flash and NVidia card?

I'm new to Linux and if you know a solution write it down in details please.

---

### Post by oldfred on 2016-01-03
Even after you install, you need to use nomodeset on first reboot or until you install nVidia driver that is correct for your version of nVidia card/chip.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

These may be enough similar to have some more useful info:

 Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)

---

### Post by 1ns1d3r on 2016-01-04
oldfred, thank you

---

