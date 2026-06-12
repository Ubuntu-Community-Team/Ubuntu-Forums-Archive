---
title: "installing ubuntu on a clevo based laptop (xmg)"
date: 2018-11-08
forum: New to Ubuntu
---

### Post by parradox on 2018-11-08
Hello, I have been trying to install (dual boot) ubuntu on my laptop for days now but with no success at all (i managed to install it, but its not running properly). I have a laptop that has a mux switch between a discrete only gpu or mshybrid (optimus). When i am in discrete mode, installation goes well with nouveau.modeset=0 and I am also able to boot up. This is not really ideal since I want to use intel graphics to save power. After a lot of research and rebooting I found out that the only way to boot ubuntu properly is with acpi=off, but that messes up even more stuff than it actually fixes (laptop hangs on reboot/shutdown, keyboard in terminal doesnt work and theres no power management). Other settings I have tried were acpi_osi=! and acpi_osi=Linux but my login screen is black (i can type in the password and login, after that desktop is normal, but its anyway concerning). 

The biggest problem of all however, is the fact that any change made to the kernel makes the laptop unbootable. Whenever I use sudo apt update/upgrade and the kernel is updated, after reboot the laptop is stuck on "Loading initial ramdisk.." and fans spin quickly, only option is to hard shutdown with power button. I tried to follow one article I found where I chroot into the system and update it again, but that didnt help. When running "check disk for defects" it only writes that theres one error and reboots afterward. I also tried to install other kernel versions through Ukuu, none of which booted and all were stuck on Loading initial ramdisk..

Secure boot in bios is disabled, fast boot in windows is disabled as well.

I am really getting desperate because I cant find any proper guide on how I can properly run ubuntu on this laptop (its an XMG P507 - Clevo P651-HP6) with intel graphics and everything working. Does anyone know how to work this out? I am willing to try anything you suggest.


EDIT: installed ubuntu through legacy mode without any issues

---

