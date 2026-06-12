---
title: "Ubuntu wont load after booting."
date: 2014-07-07
forum: New to Ubuntu
---

### Post by pieterdekunder on 2014-07-07
I have a problem after booting Ubuntu from my Usb-stick.
I can boot Ubuntu in UEFI mode and in legacy mode, 
I get the normal purple starting screen in UEFI mode, then it changes to the loading screen where it wont do anything anymore.
I have the same problem in legacy mode with the usb-stick, and with a live DVD in both modes.
The loading screen stops after 2 cycles on the third dot, then my pc wont even react to the reset button.
I have done everything as described, and changed the bios boot options a dozen times for both the cd and usb, but nothing works.

My computer specs are:
Celeron 2.4Ghz Processor
8GB Ram
Asrock z77 professional motherboard
ocz agility 3 60GB SSD

I have no idea what to do anymore.
Any help is welcome.

---

### Post by Gordonbp531 on 2014-07-07
Did you create both the USB and CD from the same iso?
It's possible you've got a borked iso file.
Try downloading it again, check the MD5 sum hash  and re-create both the USB stick and the CD.
What software are you using for the USB stick?

---

### Post by pieterdekunder on 2014-07-07
I checked the MD5 hash, and it was correct.
I used 3 different programms for the Usb-stick: Lili, Win32DiskImager and Pendrivelinux.
The result was exactly the same everytime.

---

### Post by yancek on 2014-07-07
Have you tried the usb or DVD on another machine to see if they boot?  Do you have windows installed on the machine?   If so, which release?  I've never used the windows software you've tried to create the bootable flash but it usually works.

---

### Post by pieterdekunder on 2014-07-08
I have tried the usb on a different computer and it worked perfectly. The motherboard in that pc was a asus p5qld pro.
My pc has Windows 7 SP1 installed, both pc's have the same OS.

---

### Post by yancek on 2014-07-08
Here's something you could try for one boot.  It makes no permanent change and is only good for one boot attempt.  Go to the link below and read the example at the top of adding quiet splash to the syslinux bootloader.  You don't want to add quiet splash, they may already be there that but rather, put:  nomodeset at the end of the line and hit the Enter key.  You need a space before nomodeset.  See if that boots it, if not nothing has changed and you can try something else.

[https://wiki.archlinux.org/index.php/kernel_parameters](https://wiki.archlinux.org/index.php/kernel_parameters)

---

### Post by Gordonbp531 on 2014-07-08
Just a thought - have you created your USB stick while connected to a USB3 port?
I found that I had to use a USB2 port as for some reason the stick created using a USB3 port wouldn't boot - but it did when I created it using a USB2 port....

---

### Post by pieterdekunder on 2014-07-09
The Usb-stick isnt the problem because it works fine on a different pc.
So the problem has something to do with the Bios of my pc, but I dont know how to fix it.

---

### Post by oldfred on 2014-07-09
As others have already suggested video issues are most likely the issue, although UEFI/BIOS settings may be part of it. What video card/chip are you using. 

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

If using Intel video you may need other settings than nomodeset.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by pieterdekunder on 2014-07-09
The video card im using is the Radeon HD5450, but I dont think that this could cause the problem, because the pc it worked on has the same video card.
Tomorrow I will try the fixes you suggested.

---

