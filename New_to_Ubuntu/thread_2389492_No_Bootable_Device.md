---
title: "No Bootable Device"
date: 2018-04-17
forum: New to Ubuntu
---

### Post by gdawgs47 on 2018-04-17
I have a Acer Aspire One Cloudbook 14 laptop that came with Windows 10 installed. I deleted Windows 10 and attempted to install Ubuntu 16.04 LTS. I believe that it is installed on the eMMC 32GB internal hard drive, but I'm not sure. The BIOS is in UEFI. 

The problem is that Ubuntu will boot fine with the flash drive plugged in. However, when the flash drive is not plugged in, the computer says "No Bootable Device" and will not boot.

The following menu comes up when the flash drive is in:
Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

Ubuntu will boot in UEFI and Legacy as long as the flash drive is plugged in. I'm ok with wiping everything on this computer. I just want to run Linux on it, so I can learn how to use it. This is my first time installing Linux on a computer, so I'm not really sure what I'm doing and any help is appreciated!

The boot order is:
EMMC: HBG4e 32G
USB HDD: USB DISK 2.0
USB FDD:
USB CDROM:
Network Boot-IPV6:
Network Boot-IPV4:

---

### Post by oldfred on 2018-04-17
Acer ( all models) needs you to enable "trust" in UEFI on the Ubuntu/grub .efi boot files.

       Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by gdawgs47 on 2018-04-17
The first link worked, thanks!

---

