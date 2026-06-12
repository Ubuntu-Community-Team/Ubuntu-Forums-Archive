---
title: "Boot loader error /casper/vmlinuz:read error@0"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by ShirakFaeryn on 2014-06-12
Windows XP crashed and is unusable or salvageable on my old computer, unfortunately I do not have a disc to reinstall. I figured this would be a good time to try something new so I set out a couple days ago to install linux instead. 
I've tried using LinuxLive, UUI, and IsoToUSB as well as downloading the iso for ubuntu 14.04 desktop 32bit many times and trying each one. To clarify I am using a USB stick with 8gb of total space for the install drive. I've configured the BIOS to use it as the primary boot drive. At this point I'm not sure what's left to try, nor are any of my friends.

---

### Post by Bashing-om on 2014-06-12
ShirakFaeryn; Hello,

What pops to mind is to question how you are burning the .iso file to the usb device . The burn must be done as an "image" not as data.
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Next; is this a "modern" machine such that UEFI, SSRT, and/or secure boot factors in the booting process ?

Edit: Hey, how much ram is onboard ? ubuntu wants 2 gigs for a good experience.
 
What we can do to help, we do. Just a matter of identifying where in the process is the failure.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ShirakFaeryn on 2014-06-12
I'm not just  drag and dropping the iso onto it, i'm using linuxlive or uui to create a bootable usb drive....or i thought that's what i was doing with the software. has 2gigs of ram. BIOS has no problem identifying the usb stick as the primary drive and trying to use it. My head hurts with the amount of reading i've been doing the past couple of days so I'm actually going to take a nap for a bit and my turn on the PC is up. Thank you for the links, when I get back on later I'll read through them and see if I can use the info to solve the problem.

---

### Post by Bashing-om on 2014-06-12
ShirakFaeryn; Understandable that the head hurts !

There is an option to verify the burn.

Boot the liveUSB, as soon as the bios screen clears depress the right shift key -> language screen, escape key to accept the default -> boot options screen.
In the boot options screen is the option " check disk for defects" .... select it and see if the usb drive passes.
Reboot to that same screen and this time choose "try ubuntu" ...I all your devices work and you like what you see, then try and install ubuntu.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-06-12
May I add something? You do not actually explain what is happening when you boot from the USB memory stick. Please describe what you see on the screen. It will help us to identify the point at which the loading of the live session goes wrong. And from that we might be able to suggest a workaround.

Regards.

---

