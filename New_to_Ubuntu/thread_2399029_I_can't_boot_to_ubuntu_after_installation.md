---
title: "I can't boot to ubuntu after installation"
date: 2018-08-21
forum: New to Ubuntu
---

### Post by devalais on 2018-08-21
I tried with 16.04 and 18.04. After intallation is complete it shows a boot manager page with an ubuntu option but it won't work.
Boot repair isn't working either
[http://paste.ubuntu.com/p/F9YVrkR3rF/](http://paste.ubuntu.com/p/F9YVrkR3rF/)
[http://paste.ubuntu.com/p/WzM2H2qSZm/](http://paste.ubuntu.com/p/WzM2H2qSZm/)

---

### Post by yancek on 2018-08-21
The last line in boot repair shown below tells you what you need to do.  I don't know what hardware/BIOS you have but you should be able to access the boot options to boot from EFI file and select the file below to boot.  You have Grub installed in the MBR and you have an EFI system with boot files on it.  You should not have both.

> Please do not forget to make your BIOS boot on sdb1/EFI/ubuntu/shimx64.efi file! 

---

### Post by oldfred on 2018-08-21
Is this an Acer? They need "trust" from within UEFI.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by oldrocker99 on 2018-08-22
On most desktops with UEFI, it is important **NOT** to boot a USB in UEFI mode into a live system for installation. The system will not install GRUB, which results in an unbootable drive. If you boot in legacy mode, or whatever mode is NOT UEFI, all will be well.

I learned this after several very frustrating attempts to install a new system. I have learned that it is true.

---

### Post by devalais on 2018-08-26
I could solve the issue by following oldfred solution in 
[http://bernaerts.dyndns.org/linux/74...-cloudbook-431]("http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431")
thanks people!

---

