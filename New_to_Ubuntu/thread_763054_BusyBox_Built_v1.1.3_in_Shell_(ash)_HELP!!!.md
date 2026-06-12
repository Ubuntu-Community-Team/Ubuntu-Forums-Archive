---
title: "BusyBox Built v1.1.3 in Shell (ash) HELP!!!"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-22
I recently just installed Ubuntu and took the cd out and restarted the computer and the Ubuntu loading screen came up and did its thing and then took me to a dos looking screen saying:


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I am pretty new to Ubuntu and Linux.  Anyone have any idea on what i should do.  Here are my computers specs

Bio Star Tforce 6300 - 939 Mobo
Amd64 x2 4200+
4x 256mb pc3200 RAM
1x Sata 80g hard drive (Windows XP Pro)
1x IDE 250g hard drive (Game Installations)
1x IDE 120g hard drive (Ubuntu Installation)
1x IDE 160g hard drive (Storage)
Sound Blaster X-Fi Fedlity Plat sound card

Haven't installed anything on the Ubuntu Partition yet because I haven't even gotten into it. So any help would be appriciated.

---

### Post by jondska on 2008-04-22
Same here. Mine gave me an error message about gnome not being installed and is now giving me the same prompt.

---

### Post by dtrot55 on 2008-04-23
Well I got Ubuntu to boot, but I had to unplug my windows partitioned hard drive.  But that is kind of annoying because if I want to jump back and forth if have to shut down..plug in...restart...so any idea??

---

### Post by hitman47 on 2008-04-23
> **dtrot55 said:**
> Well I got Ubuntu to boot, but I had to unplug my windows partitioned hard drive.  But that is kind of annoying because if I want to jump back and forth if have to shut down..plug in...restart...so any idea??

In the boot menu...select the first option and press 'e'.

In this menu select boot option and press 'e' to edit the line and delete the word "splash" at the end and add this all_generic_ide

Press enter then 'b' to boot.

---

### Post by tadcan on 2008-04-23
This may also help

[http://ubuntuforums.org/showthread.php?t=602957&page=3](http://ubuntuforums.org/showthread.php?t=602957&page=3)

---

### Post by dtrot55 on 2008-04-24
Well after i unplugged my windows partition and restarted Ubuntu booted up off my other hard drive.  After messing with Ubuntu for a day i replugged in my windows partition and now im offered both at the boot menu...so i have no idea what i did but its working...thanks for the help.

---

### Post by spiderbatdad on 2008-04-24
right busybox is a minimal shell, usually the result of hardware detection errors. The alternate cd may solve the problem, or use special boot parameters by editing the kernel line from the grub menu. noapic nolapic, or lapic pci=routeirq, or all_generic_ide

---

### Post by Solrac924 on 2008-04-29
installing 7.10 is the only thing that worked for me. :(

---

