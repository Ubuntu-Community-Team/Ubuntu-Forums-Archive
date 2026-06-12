---
title: "Ubuntu 16.04 LTS not booting - 'Default Boot Device Missing or boot failed' error"
date: 2018-07-01
forum: New to Ubuntu
---

### Post by garcon129 on 2018-07-01
Hello,

when I try to boot I get: 'Default Boot Device Missing or boot failed'

After the error shows up I get to a menu where I can select  LinplusLite. After another error I can select ubuntu, then the system  boots fine. Here is the link to the boot-repair output:  [http://paste.ubuntu.com/p/NJfxXBZqfK/](http://paste.ubuntu.com/p/NJfxXBZqfK/)

  The output of 

  sudo efibootmgr -v looks like this:

  [https://paste.ubuntu.com/p/Jp42SY89pB/](https://paste.ubuntu.com/p/Jp42SY89pB/)

  
Thanks for helping

---

### Post by oldfred on 2018-07-01
In the video info line on 668 it mentions Acer.
So is this an Acer and what model?

All Acer have a unique requirement of setting an UEFI password and enabling "trust" on the Ubuntu/grub boot entry. While a special requirement, it is a lot better than the work arounds we have to do with some brands.

All systems require that you have latest UEFI for Meltdown and Spectre CPU vulnerabilities, both Windows & Ubuntu have updated kernels for most of those related issues.
Some Acer do not have trust setting and older threads had users downgrading UEFI to an older version.
   
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

