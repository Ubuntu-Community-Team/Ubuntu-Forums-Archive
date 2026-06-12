---
title: "[SOLVED] No sound, no wireless on hardy"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-11-22
I have a Lenovo Ideapad Y530 and installed Ubuntu 8.04 for a double boot with vista.

After the successful installation, have found that I have no sound at all and no wireless.

The wireless device is: Intel Wireless WiFi Link 5100
The audio device is: (there are several) Intel High Definition Audio HDMI
Realtek High Definition Audio
Unimodem Half-Duplex Audio Device

This is what i see at the device manager on vista.

Please help!

---

### Post by roger_1960 on 2008-11-22
Hi

For sound, have you checked that the master vol and the PC speaker vol are turned up in alsamixer?  Often installs set them to zero.  Run 'alsamixer' in terminal and adjust with arrow keys.

---

### Post by arashiko28 on 2008-11-22
The master sound and the PCM are set to 100. When I try to test them, I have about 5-6 channels, none of them gives a hint, it's completely mute.

---

### Post by arashiko28 on 2008-11-22
This is the lspci output:
> lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: [COLOR="Red"]**Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)**[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
02:00.0 [COLOR="Red"]**Network controller: Intel Corporation Unknown device 4237**[/COLOR]
06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
06:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


I don't get this, according to the Intel's web page, the drivers are included in the kernel 2.4.6 and up.

---

### Post by arashiko28 on 2008-11-22
for iwconfig: 
lo        no wireless extensions.

eth0      no wireless extensions.

For ndiswrapper -l i get no output, only shows next line ready for command.:confused:

My kernel is 2.6.24, does the 8.10 have and updated Kernel? I have found that it will be available on kernel 2.6.26.

---

### Post by roger_1960 on 2008-11-22
Hi again

Did you check the PC Speaker vol in alsamixer, its at the far right, seen by using the right arrow to scroll across..

---

### Post by arashiko28 on 2008-11-22
Everything is at 100%, only IEC958 is turned off and don't know how turn it on.

---

### Post by braacken on 2008-11-22
> **arashiko28 said:**
> I have a Lenovo Ideapad Y530 and installed Ubuntu 8.04 for a double boot with vista.

After the successful installation, have found that I have no sound at all and no wireless.

The wireless device is: Intel Wireless WiFi Link 5100
The audio device is: (there are several) Intel High Definition Audio HDMI
Realtek High Definition Audio
Unimodem Half-Duplex Audio Device

This is what i see at the device manager on vista.

Please help!

On my laptop there are 3 volume control channels: Master, PCM, and Front. I was not getting any sound out of mine until Front was increased in volume.

You may also want to try messing around with switches to see if it is needed...such as right click speaker, Open Volume Control, Preferences, select radio for Analog Loopback...

The only way I was able to get a wireless connection was to upgrade to Ubuntu Intrepid.

---

### Post by igknighted on 2008-11-22
> **braacken said:**
> On my laptop there are 3 volume control channels: Master, PCM, and Front. I was not getting any sound out of mine until Front was increased in volume.

You may also want to try messing around with switches to see if it is needed...such as right click speaker, Open Volume Control, Preferences, select radio for Analog Loopback...

The only way I was able to get a wireless connection was to upgrade to Ubuntu Intrepid.

Yeah, that wifi card is newer than Hardy IIRC.  It work perfectly out of the box on all fall release distributions (Mandriva 2009, Fedora 10, Ubuntu 8.10, etc.) - I have the same one.

---

### Post by Lazy-buntu on 2008-11-22
If possible I would get a wired internet connection and update your install. If that doesn't resolve your problem, check your hardware drivers under system > administration > hardware drivers.

---

### Post by arashiko28 on 2008-11-22
As I said before, all the volume controls are at 100%.
 I already did the upgrade and have a huge problem with onlt command prompt screen, no boot to graphic mode.

---

### Post by shoot2kill on 2008-11-22
and to answer your previous question. my 8.10 is running kernel 2.6.27-8-generic

---

### Post by arashiko28 on 2008-11-22
I know that already, I did an upgrade, but now it stays only in command prompt screen, no X, I typed startx and it gave mile long message and fisnished with fatal error.
something about VESA not working and screen found but no configuration good for it.

---

### Post by aut-omatic on 2008-11-22
yes, get a wired connection with your computer to get the updates.

then for the wireless install wine and ndiswrapper.

insert the CD with your windows **XP** driver, install it with ndiswrapper.

then it should work.. at least it worked with my belkin n adapter like that.

Other than that I can't really help you.

---

### Post by arashiko28 on 2008-11-22
windows XP doesn't have these drivers. Anyway, problem solved, the main issue is the next: 8.04 is no good for Ideapad new models because these were sold after the release of 8.04. If you ask me, they had such a big secret about the release date for sale, that not even employees of the company new nor were authorized to say it.

The drivers for intel's wireless link (the latest models) are included in kernel 2.6.26 and above, anything previous to that will be unknown devices.

The same goes for the audio.

for the hour I have now on Ubuntu, havn't found any other error. Now, the last to kick vista out of my machine would be to start a campaign for lenovo making a veriface software compatible with Linux:lolflag:

Thanks to all of you for your help.

---

