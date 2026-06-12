---
title: "can't get started"
date: 2021-05-14
forum: New to Ubuntu
---

### Post by dave_moran on 2021-05-14
HELP!!!!

trying to set up Ubuntu as a dual boot with windows 10 on a Dell desktop.
 it won't start. 
i have tried a USB stick, a live CD, and a regular CD.
i have rearranged the boot device sequence to make the internal hard drive last. i have tried UEI with secure boot. . and without secure boot.
i have tried the Legacy boot setting. 
and every combination of all these i can think of.


it just won't begin.


i am wondering if Windows 10 has something in it to block this  from happening?
what am i missing?

thx

D~~~!

---

### Post by dddman on 2021-05-14
I originally set up a dual boot with win10/dell/20.04 using rufus.  Worked first try.

What kind of a Dell (model) is this?

[https://rufus.ie/en_US/](https://rufus.ie/en_US/)

[https://certification.ubuntu.com/make/Dell](https://certification.ubuntu.com/make/Dell)

[https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-us/000131655/how-to-install-ubuntu-linux-on-your-dell-pc)

---

### Post by dave_moran on 2021-05-14
itz an XPS8700. 
64 bit
8GHz

is that what u meant?

---

### Post by dave_moran on 2021-05-14
i did it years ago on a Packard Bell dest top running XP at the time. didn't have any troubles then.
no clue why this one is fight ing me.

---

### Post by grahammechanical on 2021-05-14
> it just won't begin.

What does that mean? Does the Ubuntu live session load? Does the installation begin and fail to finish? Does the installation finish but Ubuntu does not load on reboot? If Ubuntu loads on reboot Windows does not? Or, the other way around? Your statement has previously been used by others asking for help of this forum and can cover many types of failure.

When you arranged the boot sequence to make the internal hard disk last did the utility list the USB/DVD drive as a boot option? I ask because it is usual to set the USB/DVD drive as the first to boot from. In this way in the absence of a USB stick or DVD disc the internal hard disk will be chosen as the boot device.

Have you read these tutorials?

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regards

---

### Post by dave_moran on 2021-05-14
what i mean is i have the software ready and waiting on both/either a USB stick and a CD. i have the DVD drive and the USB ports in line in the boot sequence ahead of the hard drive. and when i restart, expecting the software to load and do its install, the PC continues to bypass it all and continues to the hard drive and boots up on windows. loke mike stick or cd just are not there.

---

### Post by dddman on 2021-05-14
I got some hits on 8700; here's one:
[https://forum.level1techs.com/t/difficulty-installing-any-linux-on-dell-xps-8700/154759](https://forum.level1techs.com/t/difficulty-installing-any-linux-on-dell-xps-8700/154759)

I think your running the 4core 8700.  If so then Ubuntu could be ran inside windows using a virtual system.  No dual boot.  That's how I do it with my Dell.
There is a learning process, but its not rocket science.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

The only other thought I have is somewhere in BIOS is an overlooked option.

---

### Post by Rocky_Bennett on 2021-05-14
> **dave_moran said:**
> HELP!!!!

trying to set up Ubuntu as a dual boot with windows 10 on a Dell desktop.
 it won't start. 
i have tried a USB stick, a live CD, and a regular CD.
i have rearranged the boot device sequence to make the internal hard drive last. i have tried UEI with secure boot. . and without secure boot.
i have tried the Legacy boot setting. 
and every combination of all these i can think of.


it just won't begin.


i am wondering if Windows 10 has something in it to block this  from happening?
what am i missing?

thx

D~~~!


Ubuntu does not fit on a CD, that might be your problem. Burn the ISO to a DVD, that might work.

---

### Post by grahammechanical on 2021-05-14
This might help. It is from the Dell Corporation. See the section Set Up the Ubuntu Install.

[https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc)

> 
[LIST=1]
[*] Insert the Ubuntu disk into your DVD drive or connect your bootable USB into a port on the system.


[*] Tap rapidly on the **F12** key when the Dell logo appears during startup. This takes you to the **Boot Once** menu.


[*] You can use the **Cursor** or **Arrow** **keys **to navigate the menu and highlight your selection. You can choose to either **boot from USB** or **Boot from CD/DVD Drive**. Once your Choice is highlighted, hit the **ENTER** key.


[*] When the system reboots, choose the **Try Ubuntu** option. This option checks whether Ubuntu can see your hardware.

[/LIST]


Regards

---

### Post by dddman on 2021-05-14
> **grahammechanical said:**
> This might help. It is from the Dell Corporation. See the section Set Up the Ubuntu Install.

[https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc](https://www.dell.com/support/kbdoc/en-uk/000131655/how-to-install-ubuntu-linux-on-your-dell-pc)



Regards

Good point

The f12 (boot once) option will always take priority over BIOS set up.

---

### Post by Impavidus on 2021-05-15
If Windows 10 has been installed in UEFI mode, boot the Ubuntu live disk (usb or dvd) in UEFI mode too, which will install Ubuntu in UEFI mode. If Windows 10 has been installed in legacy mode (unlikely), stick to legacy mode.

Use Windows tools to shrink the Windows partitions, so you get enough unallocated space on the hard drive to install Ubuntu. Make sure Windows uses basic partitions, not dynamic partition, or you'll have a problem later.

How have you created the live disk? Don't burn the .iso as a file to the dvd, but burn it as an image. When using a usb, don't copy the .iso into the usb's file system like you do with ordinary files, but "burn" it to the usb drive itself, so that the .iso becomes the usb's filesystem. You need special tools for that, like mkusb or rufus. With some of these tools, you have to specify whether you want to boot it in UEFI or legacy mode. If you choose the wrong option, it won't boot. Most people nowadays use usb. Many computers no longer have a dvd drive. Maybe that all sounds obvious to you, but plenty of new users get this wrong.

You can set usb or dvd before the hard drive in your boot order, or use the boot once option. Some computers don't boot from every usb port. Trying a different port may help.

I read that this computer may come with nvidia graphics. Once it starts booting, you may have to set the nomodeset boot option in the live session, or you may get a black screen. Once Ubuntu has been installed, you can install the proprietary graphics driver.

You didn't mention the release of Ubuntu you attempt to install. 20.04 LTS would be best for a new user.

---

### Post by oldfred on 2021-05-15
Do not turn Legacy on, if Windows is UEFI which it should be.

Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by dave_moran on 2021-05-17
the above mentioned Dell link seems to be telling me that Ubuntu won't work on my XPS8700

when i use the F12 key, it takes me to my BIOS set up. 

i have never seen the Boot Once menu.

---

### Post by oldfred on 2021-05-17
Is this an older system? Sometimes vendors reuse model number.

This is old thread as mentions 12.10, but issues should be similar. 
Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

