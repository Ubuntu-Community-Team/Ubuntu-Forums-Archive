---
title: "UEFI won't allow me to install using USB"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by ally5 on 2014-09-22
I have purchased an acer Aspire E 11...it is a netbook without a cdrom, the default OS is windows 8.

I would like to install lubuntu 14.04 (64 bit?) using the USB, but settings in BIOS won't allow me to boot up in UEFI and when I choose "legacy" I get the same result.

Could anyone walk me through this process?  I have used the instructions in the ubuntu forums and tried yahoo answers...I am getting no where

---

### Post by oldfred on 2014-09-22
Some UEFI have specific settings to prevent USB from booting. Check UEFI settings. And some only show extra settings if you set a password. But never lose password or else you may never be able to reset or use UEFI/BIOS settings.

And it may just be in secure boot mode it prevents anything else, even if Ubuntu can boot in secure boot mode.

See link in my signature for general UEFI info and useful links. 

Some other Acer systems, may have had similar issues?
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by haplorrhine on 2014-09-27
F2 goes to the BIOS.  Start pressing F2 immediately after you press power.  In the  BIOS, set the laptop to boot from the flashdrive by default (move it to the top of the list).

Mine is the C0WA model.  I just used StartUpDiskCreator to put a 64-bit *.iso*  image of 14.04 onto a DataStickPro.  I had no problems.  My aspire one  722, but not my friend's, had problems, perhaps because it was an incompatible 32-bit  image.

The touchpad seems to have problems.  Have a USB mouse available.  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1366637](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1366637)

---

