---
title: "When I try to install ubuntu gnome I get Force UEFI Installation"
date: 2017-04-15
forum: New to Ubuntu
---

### Post by flex567 on 2017-04-15
I have a Windows 7 installed alongside Ubuntu. 
Now I would like to install Ubuntu Gnome over existing Ubuntu. 
I went to Windows and ran Rufus and created an bootable USB drive with Ubuntu Gnome. 
When I boot from the USB drive and want to install  Ubuntu Gnome I get the prompt in the picture. 
What should I do so i would be able to run Win7 and Ubuntu Gnome?

[https://postimg.org/image/a5budv29p/](https://postimg.org/image/a5budv29p/)

---

### Post by RobGoss on 2017-04-15
Hello and welcome to the forum, It's telling you to install Ubuntu in **UEFI** mode, this is because your Windows is obviously installed in UEFI. I would just click continue and proceed with the installation

In any case when installing Ubuntu or other Linux distributions, you will have to install then in ether **UEFI ,**which most newer system requires or **Legacy, ** this is very important when trying to setup a dual boot system

Here is more information about UEFI that might be of help [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Dennis N on 2017-04-15
You booted your installer in UEFI mode, but the message indicates you have Windows already installed in old-fashioned BIOS mode ("Bios Compatabilty Mode"). When dual booting, both OS must be installed in the same mode for dual booting to work, so abort the installation, and boot the Ubuntu installer again in BIOS mode. You system's boot menu should show two entries for your install media - one with some mention of UEFI, and the other without any (which will be BIOS mode) - this is the one to choose.

---

### Post by yancek on 2017-04-15
Take a look at the Ubuntu site below which shows what you should see when booting either UEFI or MBR.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

