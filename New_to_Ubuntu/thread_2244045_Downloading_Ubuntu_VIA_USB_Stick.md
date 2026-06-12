---
title: "Downloading Ubuntu VIA USB Stick?"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by D_Torr on 2014-09-13
I have a USB stick with Ubuntu on, because I used Universal Usb Installer, But my computer won't boot from USB and keeps running Windows, and I can't find an option anywhere on BIOS. My computer is an HP pavilion g6 and runs on Windows 7 if that helps.

EDIT: I also want to be able to use Windows aswell by Dual-Booting.

---

### Post by Mike_Walsh on 2014-09-13
Have a look at oldfred's link to this thread; you may find it useful.

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)


Regards,

Mike.

---

### Post by D_Torr on 2014-09-13
Thanks for your reply, but I need to know how to boot from the USB (there is no option on Boot Manager or BIOS). It doesn't show up on the window and I need to be able to boot it from the USB. I can't find Legacy Mode or Secure Boot anywhere, so I don't know any solutions that work.

---

### Post by stalkingwolf on 2014-09-13
if the usb stick doesnt show up in the one time boot menu then the system is not seeing it.  Either f8 or f10 should bring that menu up when you hit them during initial boot.

If its not there you could have a bad stick or bad usb port.

---

### Post by pfeiffep on 2014-09-13
> **D_Torr said:**
> Thanks for your reply, but I need to know how to boot from the USB (there is no option on Boot Manager or BIOS). It doesn't show up on the window and I need to be able to boot it from the USB. I can't find Legacy Mode or Secure Boot anywhere, so I don't know any solutions that work.

I also have an HP that doesn't have USB boot capabilities - I burned a DVD to install ubuntu.

---

### Post by oldfred on 2014-09-13
Most Windows 7 systems are not UEFI, or Windows was not installed in UEFI mode even if hardware is UEFI capable. Only a few released just before Windows 8 or converted from Windows 8 have Windows 7 in UEFI mode.

Many systems boot USB flash drive from hard drive choice menu in BIOS/UEFI, not any USB boot option. But you have to have correctly installed ISO to flash drive, not copied it, to make it bootable.
System will not show a flash drive that is not bootable in boot choices.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Other options, sometimes one works better than others:
How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Most Windows 7 systems also use all 4 primary partitions. Use Windows to shrink the NTFS partition and immediately reboot so it can run chkdks. Best to fully backup Windows and make separate repair/recovery CD or flash drive in case you later need Windows repairs. (you should have backups & repairCD/flash even if not installing Ubuntu).

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by D_Torr on 2014-09-13
I've been using WUBI now, It finishes and then says "Permission Denied", Would it work if I booted it up?

---

### Post by yancek on 2014-09-13
> I've been using WUBI now, It finishes and then says "Permission Denied", Would it work if I booted it up? 				

Are you saying you used WUBI to install Ubuntu inside your windows 7?  The permission denied error comes at what point.  Would what work if you booted what up?  Are you trying to use WUBI instead of installing to a partition?

---

### Post by oldfred on 2014-09-13
Official support for wubi is discontinued. 
It is in 12.04 and that is a LTS so wubi will be around for a while.
But the newer versions may or may not work with your system. You are pretty much on your own.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by redrumrogue on 2014-09-13
Hi there - hopefully not too late to suggest this ... you may want to try **Plop Boot Manager** ([http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)).  Download it and burn the image to a CD.  Boot from the CD with your USB stick in the machine and the Plop Boot Manager will allow you to boot from the USB, even if your BIOS does not support booting from USB

Hope this helps!

---

