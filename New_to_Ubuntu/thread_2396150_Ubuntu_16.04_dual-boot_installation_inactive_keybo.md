---
title: "Ubuntu 16.04 dual-boot installation inactive keyboard"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by balkon16 on 2018-07-12
As I'm new to Linux I'm trying to install Ubuntu 16.04 LTS on my laptop Toshiba U920T, which runs Windows 8.1 at the moment.
 
I've chosen the bootable USB stick option. In the GRUB menu (version: 2.02~beta2-36ubuntu3.17) my laptop's keyboard is inactive. I've tried using an external one - the keyboard is inactive as well. Both of them are usable in BIOS.
 
My laptop is equipped only with USB3.0 ports. The legacy option is enabled in BIOS.

---

### Post by oldfred on 2018-07-12
You probably want legacy off, UEFI on, but UEFI Secure boot off (may be called Windows or "other".

Many UEFI require you to also turn on settings for full USB support. If UEFI Secure boot is on, allowing USB to do anything is not secure.

Issues are often common by brand, then if Intel or AMD. So similar models may have similar issues & solutions.

       Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    
If you run Boot-Repair it now copies shimx64.efi to bootx64.efi as hard drive or fallback boot entry. Many Toshiba will not boot Ubuntu entry, but will boot a hard drive entry.
       Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

