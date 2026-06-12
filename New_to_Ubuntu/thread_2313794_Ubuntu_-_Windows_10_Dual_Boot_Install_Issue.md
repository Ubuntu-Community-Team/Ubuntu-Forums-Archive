---
title: "Ubuntu - Windows 10 Dual Boot Install Issue"
date: 2016-02-16
forum: New to Ubuntu
---

### Post by hoffmann2 on 2016-02-16
Hey guys,

[SIZE=1]I did a quick search and couldn't find anything that was particularly specific to my issue. I am trying to install Ubuntu on the save drive as Windows 10, but once I get to the "download updates while installing" screen before actually installing, then hit continue I am getting this error:

"Force UEFI Installation? This machines firmware has started this installer in UEFI mode but it looks like there maybe existing operating systems already installed using BIOS compatibility mode. If you continue to install Debian in UEFI mode, it might be difficult to reboot into any BIOS-mode operating system."

I poked around in my BIOS and tried disabling fast boot, disabling Compatibility (CSM) and I'm still managing to get the same error. When I look in my boot options there is only one option for the USB drive and it is UEFI. 
My motherboard is a ASUS ROG Maximus VII Hero, do you guys have any suggestions?[/SIZE]

EDIT: 
I managed to get Ubuntu to install by disabling Secure Boot, but after the installation my PC just boots straight into Windows 10. 

Fixed by running Boot Repair from Live Ubuntu USB - Feel free to delete post

Thanks for your help here,

Hoffmann

---

### Post by ajgreeny on 2016-02-16
Welcome to the forum, and I'm happy that you managed to solve your problem.

For others who may be searching the forum for answers to a similar problem please mark this thread as SOLVED from the Thread Tools menu at the top.

Marked as SOLVED on your behalf.

---

