---
title: "Cant install my wireless adapter, may be USB issues"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by ohsnapdragon on 2011-09-20
Hi!
 
I'm having problems installing my wireless adapter, though it may very likely be a USB connection problem.
 
I'm a brand new convert to Ubuntu, after tragically watching my laptop crash AGAIN thanks to windows. While its in the shop, I decided to try Ubuntu out the ol desktop stuffed in the closet. I installed Ubuntu 10.10 with no problems. Then I ran out to staples to get a Wireless Adapter (Netgear WNA3100)
 
And for the life of me, I cant get it to work. Please bear mind that since I have no internet connected computer at home, and am at the library writing this from memory, so some little details may not be 100% accurate
 
Here's what I've done so far:
1) Plugged in the Wireless Adapter, pushed the little button on it, nothing. No recognition on Ubuntu, no light on on the adapter, nothing
2) put in the install CD for Windows, and as expected, it wouldnt run (though it would show)
3) Ran the command "mount", and checked /etc/fstab, nothing
4) Went to the library, checked out a Ubuntu help book, for version 7.?, it told me to go into "Networking Options", find "Wireless Connection" in the drop down menu, and then press Configure. But "Wireless Connection" wasnt there. The only thing was Eth0 or something or other related to ethernet. I tried configuring it anyway as wireless, but it was very apparent it was not my device.
5) Went back to library, printed out 5 different sets of directions for installing a wireless adapter, all from different sources. They basically said the same thing as the book, but also to download NDISwrapper from the Snyaptic Package Manager. 
6) Back to the library, downloaded NDISwrapper onto flash drive from Sourceforge. No problems
7) Plugged flash drive into my computer, and my computer wouldnt acknowledge it, which is the exact problem I was having in the first place with my wireless adapter.
8 )Tried "mount" command again, along with /etc/fstab, and still nothing for either device
9) Thought it was an issue with my USB ports, but then realised my mouse was hooked up via USB, and it was fine. I then searched and searched the book, and found the command "lsusb", which listed both the flash drive and the adapter (and the mouse)!
 
So my wireless adapter and my flash drive (with NDISwrapper on it) are not being read on my computer, except for the command "lsusb", and now I am stuck and have no idea what to do next.
 
Please help!
 
](*,)

---

### Post by anewguy on 2011-09-20
For now, forget the ndiswrapper you downloaded from sourceforge.  *IF* it ends up being needed, the tools are all on the installation CD.

Please do post back the output of lsusb with the wireless adapter (and for that matter, the USB drive) plugged in - it will help us help you.

The first thing we'll want to do is get your wireless working - we'll look at the other after that.

Dave ;)

---

### Post by Lisiano on 2011-09-20
+1 about forgetting ndiswrapper.
It seems that the WNA3100 is a broadcom (BCM43231) so maybe the repos have the driver. I think the broadcom-sta-common might have the support > Broadcom STA is a binary-only device driver to support the following IEEE
802.11a/b/g/n wireless network cards: BCM4311-, BCM4312-, BCM4313-,
BCM4321-, and BCM4322-based hardware.Wild pick btw. So the links
[http://ftp.estpak.ee/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-source_5.60.48.36-2_all.deb](http://ftp.estpak.ee/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-source_5.60.48.36-2_all.deb)
[http://ftp.estpak.ee/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-common_5.60.48.36-2_all.deb](http://ftp.estpak.ee/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-common_5.60.48.36-2_all.deb)
[http://ftp.estpak.ee/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb](http://ftp.estpak.ee/ubuntu/pool/universe/m/module-assistant/module-assistant_0.11.3ubuntu1_all.deb)
I used the files from my local mirror (ftp.estpak.ee). Now put them on your USB and wait for a while until someone else comes maybe with something better, if not, run home and do this next.
Install them using ```
sudo dpkg -i broadcom-sta-source_5.60.48.36-2_all.deb broadcom-sta-common_5.60.48.36-2_all.deb module-assistant_0.11.3ubuntu1_all.deb
```
Just note it down as ```
sudo dpkg -i Files
```

Note: The files were referenced from the Maverick page on Launchpad.
Note2: I fail today. First mistook for Natty, then Lucid. Finally correct - Maverick.


Edit N: Try looking at the System -> Administration -> Available Drivers. It could help in understanding if Ubuntu knows about the USB, also the CD can be used as a mini-repo of sorts.

---

### Post by walt.smith1960 on 2011-09-20
Is there any chance you could return that adapter?  There are choices that are more linux friendly.  A brief search looks like NDIS wrapper is the only game in town for the WNA3100. You might be able to get it to work but why buy a problem?  The WNA3100 appears to be a Broadcom 43231 chipset powered device which appears to be a problem child.  It looks like Staples favors Netgear & Belkin. I know some Belkin adapter are plug & play as well but I don't know which ones and online guides tend to be a little behind current models.  I believe the Linksys AE1000 has been problematic as well, it may have the same Broadcom 43231 chipset but I'm not certain about that.

 I bought a Netgear WNA1100 (N150 Atheros 9K based) from Staples a few months ago. It's N150 rather than N300 but it's fast enough for my purposes.  The stores around me show it in stock.  It's been plug & play for me in 11.04 & 11.10.  Prior to 11.04 I used an installer found on Source Forge to get it to work.  it's worth spending some time in the wireless & networking forum go get a feel for which devices to avoid.  Good luck on your quest, wireless networking is perhaps the biggest problem area of Linux hardware support.

Edit:  I just saw Lisiano's post.  You can try that, perhaps the newest Broadcom STA drivers will support this chipset.  If it were me though, I wouldn't fight with it too long.  Why spend good money, time & frustration on a problem that you can return?

Edit 2:  I see you're using 10.10.  That's a good solid release.  If you choose the WNA1100, here's the Source Forge file that will get the WNA1100 to light up:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)
Installing this is a little different than most Linux programs.  This is a two step process.  First, download the version 1-0-3 .deb file. I was using version 1-0-1 but I'd expect 1-0-3 to work as well.  A .deb file is self installing, sort of like an .exe file.  In Ubuntu, you should be able to just double click on it and  Ubuntu Software Center should launch and offer to install the package. It may complain about not meeting Ubuntu's standards. I installed it anyway.  There are no nasties in it that I know of and in an open community like this one nasties are found out sooner rather than later.  Once the install is done, go to applications ->system and you should see "Atheros installer" or something like that.  Launch that and be patient, it'll take several minutes.  Once it finishes, restart your machine and you should be in business.  If your Ubuntu updater downloads a new image/kernel your wireless adapter may quit.  With the ath9k installer, you just repeat step 2 and you should be good.  If you compile a driver manually, you'll need to repeat those steps.

---

### Post by ohsnapdragon on 2011-11-08
Sorry I havent responded in so long! blah, blah... long boring personal excuses, blah. Anyway, I now am suddenly living in a new apartment, and have most of my sht straightened out, except of course for my internnnnnnet. 
 
For the future I promise ALL of my responses will be very prompt.
 
 
Lisiano: I tried installing what you suggested, but my flash drive was still undetected, and it wouldn't work
 
Walt.Smith: I actually went out and bought the WNA1100, and the exact same thing happened, nothing. It wouldnt show up anywhere. So i returned it, and am continuing to try with my WNA3100.
 
**I still believe the problem is my usb connections and not the adapter itself.** After testing out the WNA1100 with no results, and then buying another flash drive in hopes it would be recognized (it was not). I still think its a USB problem. I did however found out my _ipod is recognized_ and so I can transfer notes between computers, which means I didnt have to end up handwriting out the following command, thank god. 
 
As a reminder, the Logitech device is my mouse which works, and the ipod works, but the Sandisk device is the flash drive doesnt work, and the Netgear device is my wireless adapter that doesnt work. 
 
> 
 
[FONT=Courier New][SIZE=2]cosmo@Spider:~$ sudo lsusb -v[/SIZE][/FONT]
[FONT=Courier New][SIZE=2][sudo] password for cosmo: [/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 002 Device 002: ID 046d:c064 Logitech, Inc. [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 8[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x046d Logitech, Inc.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0xc064 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 34.01[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 1 Logitech[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 USB Optical Mouse[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 34[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 4 B34.01_B0009[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0xa0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Remote Wakeup[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 98mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 3 Human Interface Device[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 1 Boot Interface Subclass[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 2 Mouse[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]HID Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 33[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdHID 1.10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bCountryCode 0 Not supported[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumDescriptors 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 34 Report[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wDescriptorLength 71[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Report Descriptors: [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]** UNAVAILABLE **[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x81 EP 1 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Interrupt[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0006 1x 6 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Status: 0x0000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 1.10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 9 Hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 Unused[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 Full speed (or root) hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x1d6b Linux Foundation[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0x0001 1.1 root hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 2.06[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 3 Linux 2.6.35-22-generic ohci_hcd[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 OHCI Host Controller[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 1 0000:00:02.0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 25[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0xe0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Self Powered[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Remote Wakeup[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 0mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 9 Hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 0 Unused[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 0 Full speed (or root) hub[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x81 EP 1 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Interrupt[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0002 1x 2 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 255[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Hub Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 11[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 41[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]nNbrPorts 10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wHubCharacteristic 0x0012[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]No power switching (usb 1.0)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]No overcurrent protection[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bPwrOn2PwrGood 1 * 2 milli seconds[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bHubContrCurrent 0 milli Ampere[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]DeviceRemovable 0x00 0x00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]PortPwrCtrlMask 0xff 0xff[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Hub Port Status:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 1: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 2: 0000.0303 lowspeed power enable connect[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 3: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 4: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 5: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 6: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 7: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 8: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 9: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Port 10: 0000.0100 power[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Status: 0x0003[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Self Powered[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Remote Wakeup Enabled[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 001 Device 006: ID 05ac:1205 Apple, Inc. iPod Mini 1.Gen/2.Gen[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x05ac Apple, Inc.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0x1205 iPod Mini 1.Gen/2.Gen[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 0.01[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 1 Apple[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 iPod mini[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 3 000A2700145F88B1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 32[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0xc0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Self Powered[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 500mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 8 Mass Storage[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 6 SCSI[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 80 Bulk (Zip)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x82 EP 2 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x01 EP 1 OUT[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Qualifier (for other device speed):[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 6[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Status: 0x1500[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 001 Device 005: ID 0781:5567 SanDisk Corp. Cruszer Blade[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x0781 SanDisk Corp.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0x5567 Cruszer Blade[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 1.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 1 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 3 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 32[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0x80[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 200mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 8 Mass Storage[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 6 SCSI[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 80 Bulk (Zip)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x81 EP 1 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x02 EP 2 OUT[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]can't get device qualifier: Connection timed out[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]can't get debug descriptor: Connection timed out[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Status: 0x0000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x0bda Realtek Semiconductor Corp.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0x0111 Card Reader[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 11.22[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 1 Generic[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 USB2.0-CRW[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 3 20021111153705700[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 32[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 4 CARD READER[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0x80[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 500mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 8 Mass Storage[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 6 SCSI[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 80 Bulk (Zip)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 5 Bulk-In, Bulk-Out, Interface[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x01 EP 1 OUT[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x82 EP 2 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Qualifier (for other device speed):[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 6[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 0 (Defined at Interface level)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Status: 0x0000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Bus 001 Device 002: ID 0846:9020 NetGear, Inc. [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 18[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 2.00[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 255 Vendor Specific Class[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idVendor 0x0846 NetGear, Inc.[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]idProduct 0x9020 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdDevice 0.01[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iManufacturer 1 Broadcom[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iProduct 2 Remote Download Wireless Adapter[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iSerial 3 113[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Configuration Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wTotalLength 39[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumInterfaces 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bConfigurationValue 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iConfiguration 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 0xa0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2](Bus Powered)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Remote Wakeup[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]MaxPower 200mA[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Interface Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 9[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceNumber 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bAlternateSetting 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumEndpoints 3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceClass 255 Vendor Specific Class[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceSubClass 2 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterfaceProtocol 255 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]iInterface 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x81 EP 1 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 3[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Interrupt[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0010 1x 16 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 4[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x82 EP 2 IN[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Endpoint Descriptor:[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 7[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 5[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bEndpointAddress 0x03 EP 3 OUT[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bmAttributes 2[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Transfer Type Bulk[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Synch Type None[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Usage Type Data[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wMaxPacketSize 0x0200 1x 512 bytes[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bInterval 1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Device Qualifier (for other device speed):[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bLength 10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDescriptorType 6[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bcdUSB 1.10[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceClass 255 Vendor Specific Class[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceSubClass 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bDeviceProtocol 0 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bMaxPacketSize0 64[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]bNumConfigurations 1[/SIZE][/FONT]
 
 


---

