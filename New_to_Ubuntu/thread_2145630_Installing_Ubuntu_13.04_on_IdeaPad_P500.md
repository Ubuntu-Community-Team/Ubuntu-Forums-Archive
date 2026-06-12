---
title: "Installing Ubuntu 13.04 on IdeaPad P500"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by uhhhnoakes on 2013-05-16
I'm installing Ubuntu for a friend on his laptop (Windows 8) and I was able to load off of my USB and install like I did for my Samsung Laptop however when I restart his computer without the USB in it it says "Windows Boot Failed" then "Ubuntu blocked by current security." I attempted Boot-Repair in the Terminal but it didn't allow me to boot either into Ubuntu or Windows 8, I can only access the demo through the LiveUSB...

---

### Post by moody_mark on 2013-05-16
I've not actually installed Ubuntu alongside Win8 but 13.04 will support UEFI boot, however you'll need to turn off the secure boot in the BIOS, at least thats what I had to do to boot the live DVD. Have a look at the UEFI docs, they might help give you some pointers: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by uhhhnoakes on 2013-05-16
Ok well I was able to get into the BIOS by pressing the NOVO button on the side of the laptop, ensured Secure Boot was disabled and set "Ubuntu" to the top of the EFI selections. When I reset it, GNU GRUB loads up and I have the following options:

Ubuntu
Advanced options for Ubuntu
Windows UEFI recovery bkpbootmgfw.efi - loads fine
Windows Boot UEFI recovery - works fine
Windows UEFI recovery LrsBootmgr.efi - doesn't work, displays "Tip: One Key Recovery partition has damaged, so do not launch the main application"
Windows Boot UEFI recovery bkpbootx64.efi - doesn't work, displays "Tip: One Key Recovery partition has damaged, so do not launch the main application"
Windows 8 (loader) (on /dev/sda5) - "error invalid EFI file path."
System Setup - loads BIOS

I found a bug report that helped me access the BIOS with the NOVO button and had some other useful info in it but I'm still VERY new to Ubuntu/Linux so half of it is like a foreign language to me still... [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694388](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694388)

On the last three Windows options, why do they not work? Do I need to change anything? I was able to successfully delete Windows on my Samsung laptop and move to strictly Ubuntu fairly well but if my friend decides he wants to remove Ubuntu and go back to Windows 8, how would I start that process?

---

