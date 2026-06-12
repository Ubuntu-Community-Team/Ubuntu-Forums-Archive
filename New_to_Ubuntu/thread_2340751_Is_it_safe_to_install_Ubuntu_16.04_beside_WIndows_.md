---
title: "Is it safe to install Ubuntu 16.04 beside WIndows 10 with UEFI?"
date: 2016-10-21
forum: New to Ubuntu
---

### Post by OctaVive on 2016-10-21
So I am kinda worried about installing Ubuntu on my main PC, since I love it.
  But the problem is, my motherboard is UEFI. Its a gigabyte h81m-hd3.
  Would it be safe to dual boot Windows and Linux on this? Also, is the  installation as easy as installing it on a PC that has BIOS? (I have  Ubuntu on my laptop)
  Also, last question, let's say I installed Ubuntu and Windows, and  Windows gets an update, can the update break the Grub2 bootloader?
  Thanks for your help, if I am able to install Ubuntu 16.04 on my custom build PC I'd be happy as hell.

---

### Post by oldfred on 2016-10-21
Single drive or do you have more than one drive?

I have an Ubuntu only install on a newer Gigabyte, but only one Windows 10 system for TV as DRM required for my cable system.

UEFI is more complex.
UEFI has three boot modes, UEFI with Secure Boot, standard UEFI, and BIOS/CSM/Legacy. So just that adds to complexity.
But UEFI itself has lots of added configuration settings, some must be changed.

Gigabyte has with many motherboard required IOMMU setting changes, not sure if your model needs that or not. But make sure you have newest UEFI from Gigabyte.
 Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

Major updates in Windows often resets Windows to first in boot order, but that can easily be reset. In BIOS, Windows always reinstalled its boot loader, so issue of some changes required to get Ubuntu to boot is not really different.
 
In link in my signature is a lot more info, the main steps you need to go thru, and many links to even more info.
Main link, how you boot install media is then how it installs, so always boot in UEFI mode:
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by RobGoss on 2016-10-21
> [COLOR=#000000]Would it be safe to dual boot Windows and Linux on this? Also, is the installation as easy as installing it on a PC that has BIOS?[/COLOR]

Ubuntu make the installation very simple but! just like anything else do your **homework **before you start experimenting Linux is new for you so keep this in mind. Here's a guide for installations [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)



> [COLOR=#000000]Also, last question, let's say I installed Ubuntu and Windows, and Windows gets an update, can the update break the Grub2 bootloader?[/COLOR]

Any Windows updates you receive will not effect a Ubuntu system too totally different operating systems and the Grub will not be effected so no worries there

---

### Post by Geoffrey_Arndt on 2016-10-21
Depends on how informed, and how persistent you are.   Some new systems are "relatively" easy (Dell, most Lenovos), and many others can be a royal PITA (pain in the adams-apple).   Win10, as OldeFred suggests in his post can certainly overwrite bootloaders, (I've read where some claim, even partitions . . although I can't verify that last).    Consumer Windows is not designed to be cross-platform.

The safest method is just to keep Win10 on it's own hardware, and Linux on it's own hardware.   These days, there are more choices.   Even dual-boot systems can be ordered with the latest mobo's and chipsets.   But I personally just prefer to order a simple, less expensive, small form-factor Ubuntu PC such as the System76 Meerkat (see my sig. for link to pre-loaded linux vendors).

---

