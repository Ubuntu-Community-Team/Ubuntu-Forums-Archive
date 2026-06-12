---
title: "unable to boot after successful installation"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by chlx on 2012-07-15
About six weeks ago I decided that I would try to build my own computer for the first time with the ultimate goal of installing and learning how to use Ubuntu 12.04.  Eventually I was able to install Ubuntu to the hard drive and successfully create a user account, but I haven't been able to boot the computer back up again ever since.  I'm not sure what the problem is exactly.  All I really know is that when I try to load Ubuntu from Grub, the boot process never advances beyond the purplish screen with the five flashing white and red dots (I've tried being patient with it but even after hours nothing happens).  The screen isn't freezing or going black, which is still what happens whenever I try to boot from the CD.  I was finally able to bypass this issue during the installation by specifying some boot parameters in Grub, but of course I wasn't smart enough to write them down or even remember how I found them in the first place.  I really don't have the slightest clue how to fix this situation and for whatever reason I just can't seem to find any information in help forums that would give me a clearer sense of what I should be trying to do differently.  Do I need to figure out how to do a boot repair?

---

### Post by Draexo on 2012-07-15
I have been having this same problem myself.  After a sucessfull install in a dual-boot situation with Windows 7 64 bit, I get a "purple screen of death".  When I then re-boot, I get into Ubuntu.  Seems I have success about half the time.  The other half, I get the "purple screen of death"

---

### Post by techvish81 on 2012-07-16
> **chlx said:**
> About six weeks ago I decided that I would try to build my own computer for the first time with the ultimate goal of installing and learning how to use Ubuntu 12.04.  Eventually I was able to install Ubuntu to the hard drive and successfully create a user account, but I haven't been able to boot the computer back up again ever since.  I'm not sure what the problem is exactly.  All I really know is that when I try to load Ubuntu from Grub, the boot process never advances beyond the purplish screen with the five flashing white and red dots (I've tried being patient with it but even after hours nothing happens).  The screen isn't freezing or going black, which is still what happens whenever I try to boot from the CD.  I was finally able to bypass this issue during the installation by specifying some boot parameters in Grub, but of course I wasn't smart enough to write them down or even remember how I found them in the first place.  I really don't have the slightest clue how to fix this situation and for whatever reason I just can't seem to find any information in help forums that would give me a clearer sense of what I should be trying to do differently.  Do I need to figure out how to do a boot repair?

give the specifications of your pc.  hardware details,  there are some display driver problems with some graphic cards.

---

### Post by mapes12 on 2012-07-16
Could be worth a try:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Failing that and if Ubu is the only OS on your machine then perhaps re installing after fully formatting the HDD will do the trick. Let the installer defaults lead the installation.

---

### Post by chlx on 2012-07-16
Thanks for taking the time to read my thread!  \\:D/

Here is some basic info about my hardware:

NVIDIA GeForce GTX 580
AMD fx (tm) - 8150 Eight-Core Processor 
Asus Crosshair V Formula motherboard
WD 3.5-inch SATA hard drive (1 TB) 
Creative Sound Blaster Recon3D THX PCIE Fatal1ty Champion Sound Card SB1354
Crucial Ballistix Tactical 16GB (8GBx2) DDR3-1600 (PC3-12800) CL8, 1.5V w/XMP

I'm using USB connections for both mouse and keyboard which seem to be working fine.

Re: boot repair...I figure I'll give it a try as soon as I can figure out the right boot parameters to stop my screen from freezing whenever I try to boot from CD.

---

### Post by cmcanulty on 2012-07-16
I had to disable the wireless card at install to get it to continue past where you are stuck I forget the exact steps
[http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/]("http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/")

---

### Post by chlx on 2012-07-18
Needless to say, part of my problem is that I'm not even sure where I should even be looking to find the information that I need.....so even a useful tip about where I might be looking for potential answers would be very much appreciated at this point.

---

### Post by Hadaka on 2012-07-18
probably that nvidia graphics card causing the problem, but...try this
when you boot...and see the little man symbol at the bottom of the screen
hold down the shift key...then the F6 key..choose nomodest  then escape key
and see if it boots.  It may also be your wireless card...i also had to go into
the bios setup and disable the wireless to get it to boot past the never ending
blinking dots. It sounds like your install was ok and you are just having the usual
needs tweaking situation. Please post back if any of this helps.

---

### Post by oldfred on 2012-07-18
I have an older nVidia card and have to use nomodeset all the time until I get the nVidia driver installed. I only install the one Ubuntu offers as that is automatically incorporated into the kernel. But some very new cards may need something newer from nVidia, but then you have to redo for every new kernel.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by chlx on 2012-07-19
thanks for this input.  this definitely looks helpful.  unfortunately it's going to be a few days before i'm able to sit down in front of the computer again but i'll definitely let you guys know what happens.

---

