---
title: "Ubuntu on Acer Netbook."
date: 2012-10-17
forum: New to Ubuntu
---

### Post by Rexysmexy on 2012-10-17
This is my first time trying to install Ubuntu on my Acer Aspire one Netbook. It currently has No OS.

 I downloaded Ubuntu from the Site, Then mounted the ISO onto a usb using unetbootin. Once I booted into my USB stick, my screen changed to show the BIOS settings, Copyright, and Build number.

I've left it on this screen for 10+ Minutes, and nothing changes. Did I possibly download the wrong type? I downloaded the latest version.

Any help is Appreciated.
 
In other due to No "Ubuntu" Prefix.

---

### Post by jspike397 on 2012-10-17
Hello,
Have you downloaded the 32 bit iso?  Also, what you describe does not seem like your system has loaded the image.  Try rebooting and booting from the usb stick again.

Jspike397

---

### Post by Rexysmexy on 2012-10-17
> **jspike397 said:**
> Hello,
Have you downloaded the 32 bit iso?  Also, what you describe does not seem like your system has loaded the image.  Try rebooting and booting from the usb stick again.

Jspike397

I'm currently using the 32 bit is, I've rebooted and tried multiple USB sticks. Nothing wants to work.

---

### Post by will1982 on 2012-10-17
> **Rexysmexy said:**
> I'm currently using the 32 bit is, I've rebooted and tried multiple USB sticks. Nothing wants to work.

Forgive my ignorance, but does that laptop have a CD drive?

---

### Post by Rexysmexy on 2012-10-17
> **will1982 said:**
> Forgive my ignorance, but does that laptop have a CD drive?

Sadly it does not, It would be so much easier if it did..

---

### Post by will1982 on 2012-10-17
> **Rexysmexy said:**
> Sadly it does not, It would be so much easier if it did..

Ah yes, any computer I've tried didn't work on USB either.
I actually had to buy the superdrive or whatever to install it on my Macbook :P

---

### Post by mardybear on 2012-10-17
> **Rexysmexy said:**
> I downloaded Ubuntu from the Site, Then mounted the ISO onto a usb using unetbootin. Once I booted into my USB stick, my screen changed to show the BIOS settings, Copyright, and Build number.

I've left it on this screen for 10+ Minutes, and nothing changes. Did I possibly download the wrong type? I downloaded the latest version.

Hi Rexysmexy.

When you attempt to install, is the computer hanging on the computer's BIOS screen or the Ubuntu installation screen. If it's the BIOS screen, your comptuer has not yet booted the USB stick/Ubuntu install.

Please clarify so people can better assist.

mardybear

---

### Post by Rexysmexy on 2012-10-17
> **will1982 said:**
> Ah yes, any computer I've tried didn't work on USB either.
I actually had to buy the superdrive or whatever to install it on my Macbook :P

I'll have to do that if there aren't any work arounds.

---

### Post by Rexysmexy on 2012-10-17
> **mardybear said:**
> Hi Rexysmexy.

When you attempt to install, is the computer hanging on the computer's BIOS screen or the Ubuntu installation screen. If it's the BIOS screen, your comptuer has not yet booted the USB stick/Ubuntu install.

Please clarify so people can better assist.

mardybear

Its the BIOS screen. Nothing works after many attempts

---

### Post by jspike397 on 2012-10-17
If that is the case, go into the bios settings and somewhere, it depends on the computer, there should be a setting that says boot order.  Switch option 2 to your hard drive and switch option 1 to your USB stick.  Also there should be a place to select a boot selection popup window, or that is what my ASUS netbook calls it. A boot selection popup window is a option to select a boot device.  That will definitively work if you can find it.

---

### Post by Rexysmexy on 2012-10-17
> **jspike397 said:**
> If that is the case, go into the bios settings and somewhere, it depends on the computer, there should be a setting that says boot order.  Switch option 2 to your hard drive and switch option 1 to your USB stick.  Also there should be a place to select a boot selection popup window, or that is what my ASUS netbook calls it. A boot selection popup window is a option to select a boot device.  That will definitively work if you can find it.

I can boot to the USB, but this is what comes up.
[img]http://i852.photobucket.com/albums/ab87/ideject/IMG-20121017-00230.jpg[/img]

---

### Post by mardybear on 2012-10-18
Hi again...

What's the model # of your Acer netbook, the brand name of your USB stick and the version of Ubuntu you're trying to install?

You're not the only one having problems installing Ubuntu onto their netbook. Do any of these links help?

[http://ubuntuforums.org/showthread.php?t=1917099](http://ubuntuforums.org/showthread.php?t=1917099)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

[http://ubuntuforums.org/showthread.php?t=1610031](http://ubuntuforums.org/showthread.php?t=1610031)

mardybear

---

### Post by I2k4 on 2012-10-18
Hi, I have the Acer One.  It does not look like you have gone into BIOS to change the boot order.  This is necessary to boot _any_ operating system from the USB.

1.  Shut down. Remove the Ubuntu USB drive.
2.  Press the power button while _repeatedly_ pressing F2 key.  That will bring you into BIOS adjustment mode.  
3.  Right key over to "BOOT" section at the top.  You'll a stack of boot options with the top being the first. 
4.  Use the onscreen directions to ensure that "USB FDD" is at the very top of the boot order.  
5.  Use screen directions to _Save and Exit_ from BIOS.

Shut down again.  You're now set up to boot from a USB drive.  Insert the Ubuntu USB drive and press the power button as usual.  Instead of  what you now see, you should get an Ubuntu boot screen.  If you leave it alone it will boot into Ubuntu.

(Once the boot order is changed like this, and there is no bootable USB drive in the socket, the netbook will automatically move down that boot order list to boot from the hard drive as usual.  So there's no reason to change BIOS back again after you've installed Ubuntu on the hard drive.)

---

### Post by Rexysmexy on 2012-10-18
> **mardybear said:**
> Hi again...

What's the model # of your Acer netbook, the brand name of your USB stick and the version of Ubuntu you're trying to install?

You're not the only one having problems installing Ubuntu onto their netbook. Do any of these links help?

[http://ubuntuforums.org/showthread.php?t=1917099](http://ubuntuforums.org/showthread.php?t=1917099)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

[http://ubuntuforums.org/showthread.php?t=1610031](http://ubuntuforums.org/showthread.php?t=1610031)

mardybear

I'm going to try just the ISO on the USB. I do not have Ubuntu running on anything else to extract the image onto the usb with.

Is it possible 12.04.1 Doesn't work with it?

Also, Changing the boot order did absolutely nothing, I run into the same problem.

Edit: I have the Acer 532H Model.

---

### Post by mardybear on 2012-10-23
Hi Rexysmexy...

It's been a while. Any luck with your install attempt? I came across an old post regarding an xubuntu install on your laptop model but it's pretty extreme and involved swapping hardware. Suppose it depends on how motivated you are to get it running...not sure i would want to attempt this route.

Here's the poster's quote:
[INDENT][I]I believe I solved my problem. Since my netbook doesn't have a disc drive and the BIOS/EFI thing is weird, I pulled the HDD from it. It was a SATA drive which I knew I could use in my desktop, so I used Windows to burn the 64-bit .iso to a CD. I then pulled the side panel off of my desktop and hooked up the netbook hdd to the mobo and PSU, and disconnected the other hard drives to leave only the netbook HDD and the DVD-RW drive on the MOBO.

I then proceeded to boot from the CD, and installed xubuntu onto the netbook HDD smoothly.

When I reconnected the HDD to the netbook, it fired right up into xubuntu, saw my WiFi network, and when connected, proceeded to download like 200mb of updates. [/I][/INDENT]

Like i said, pretty extreme. Here's the forum link:
[http://ubuntuforums.org/showthread.php?t=1925431](http://ubuntuforums.org/showthread.php?t=1925431)

Hopefully someone else will be able to provide more assistance.

Good luck,

mardybear

---

### Post by mastablasta on 2012-10-23
if it has uefi then you need to create boot partition and also you need to follow instructions for installation on UEFI.: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
 
using DVD or USB doesn't really matter since in both case the OS get's loaded into ram.
 
does the image cretaed on USB boot on another maschine? it oculd be that something is worn gwith downloaded image.

---

### Post by baec539 on 2013-09-15
[BUMP]

My Acer 532h absolutely WILL NOT boot USB sticks... It DOES boot and install from external USB hard drives no problem... 

(I used an old 20GB IDE on a USB adapter cable... the cable was a buck or 2 on ebay... yer local computer shop should have some cheap old drives)

---

### Post by CeejRab on 2013-09-15
Hello rexysmexy,

I have an Acer Aspire as well, and i had a similar issue. I havent had much fortune with unetbootin, so i prefer YUMI Multiboot from [www.pendrivelinux.com]("http://www.pendrivelinux.com") because not only can i use multiple distros from the usb this way but i also prefer the syslinux boot loader with grub chain afterward. But anyhow, first off, if you have an accessible windows computer to make the bootable usb from, download YUMI from the website i mentioned above. Also have your ubuntu iso handy.

Format the usb stick as FAT-32, then open YUMI. Select the ubuntu version that you have an iso for and then locate the file. Tell YUMI to format the drive by clicking the check box for formatting the drive.

When YUMI is done setting up your usb drive, properly remove it, and then shutdown your computer. Plug in the USB stick, then press the power button to turn your computer on again. When the acer splash screen shows, press F12, and use the arrow keys to highlight the USB device. If your usb stick is kingston it might be called USB KINGSTON MICRO or something similar. If Sandisk, it may say SANDISK. Select whatever your USB device is listed as in the list and press enter. There should be no problem from there on, the YUMI screen will pop up and you can use the arrow keys and enter key to choose the ubuntu distro and then select install. Wait for the graphical ubuntu install setup to load and follow the prompts!

PS: as mentioned above, if your iso file is damaged that could be a problem as well. Try to download it again using "Downthemall" download booster addon in firefox, and make sure your internet connection is stable so the file can download properly without being paused.

---

### Post by 1991sudarshan on 2013-09-15
> **Rexysmexy said:**
> This is my first time trying to install Ubuntu on my Acer Aspire one Netbook. It currently has No OS.

 I downloaded Ubuntu from the Site, Then mounted the ISO onto a usb using unetbootin. Once I booted into my USB stick, my screen changed to show the BIOS settings, Copyright, and Build number.

I've left it on this screen for 10+ Minutes, and nothing changes. Did I possibly download the wrong type? I downloaded the latest version.

Any help is Appreciated.
 
In other due to No "Ubuntu" Prefix.

Did you change the boot  device preference in the CMOS menu? Put USB on the top of the boot device list.I use 12.04 (migration from 10.04, to 10.10, 11.04, 11.10) on my Acer Aspire One D257-13478 netbook. By Default Your hard disk is on the top in the Boot devices list. Since there is no OS installed in your Hard disk, you get the black screen. I hope this helps.

---

