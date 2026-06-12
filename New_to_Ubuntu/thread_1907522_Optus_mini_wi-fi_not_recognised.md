---
title: "Optus mini wi-fi not recognised"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by Cryptic57 on 2012-01-11
[FONT=Verdana][SIZE=2]Greetings to all, I am very new to Ubuntu with installation happening just days ago.

I wish now to connect to the net but the installer files for my Optus mini wi-fi can not be  opened. The *Disk Utility* recognises the device but cannot read any files on it. It is not seen under the *Computer* heading in *Places*.

I want to have the connection as part of Ubuntu not opened through *Wine* or similar emulator.

What do I need to do? Any pointers appreciated.[/SIZE][/FONT]

---

### Post by gandaran on 2012-01-11
hi,
what exactly is Optus mini wi-fi?
mobile broadband wireless network router? or wireless adapter?
how do you connect the device? ethernet or usb?

---

### Post by Cryptic57 on 2012-01-12
Sorry, it's a wireless/USB internet stick that acts as a wi-fi hot spot for up to 5 connections.

I have gone through the connection wizard routine but no luck. Also I haven't been able to find any drivers for it either from Optus - mobile provider - or Huawei - the device maker 
(Huawei E583C-2)'

My reading yesterday seemed to find that the device should be automatically recognised by all OSs, as it was with Mac OSX and Windows XP.

---

### Post by gandaran on 2012-01-13
> **Cryptic57 said:**
> Sorry, it's a wireless/USB internet stick that acts as a wi-fi hot spot for up to 5 connections.

I have gone through the connection wizard routine but no luck. Also I haven't been able to find any drivers for it either from Optus - mobile provider - or Huawei - the device maker 
(Huawei E583C-2)'

My reading yesterday seemed to find that the device should be automatically recognised by all OSs, as it was with Mac OSX and Windows XP.
if it is a mobile broadband wireless hotspot you don't need any drivers for the device, all you have to do is configure the internet provider connection using firefox while the device is connected with cable but if you have already done that in windows then it should work on any system including Linux/Ubuntu without doing anything more.

or if the problem is connecting to the hotspot using wireless then you must check if your PC wireless card is working or needs to install drivers for, the Optus device doesn't need drivers only your wireless card or usb wireless adapter may need if they are not supported.

so if the problem is with wireless connection find out the PC wireless card brand and model, post the details here then we will figure out what you need to install.
this terminal command shows all the details about wireless card and driver in use
```
sudo lshw -C network
```

edit:

is this the same device?
[http://www.cnet.com.au/optus-mini-wifi-modem-339308582.htm](http://www.cnet.com.au/optus-mini-wifi-modem-339308582.htm)

quote from the same link
>  If you're working from a system that lacks Wi-Fi, it's also possible to use the Mini WiFi Modem as a tethered USB modem from the unit's mini-USB port.
well again no need for drivers if you want the USB connection, look/click the panel network icon, the connection may even work automatically but most likely you will have to set it up in 'edit connections'.

---

### Post by Cryptic57 on 2012-01-14
Thank you, and yes it's the same device. I have no wireless connection so have been using it tethered to my PC. 

I was about to clean up the Windows side of things when, you guessed it - Crash! So I've been doing some reinstalling and now Windows won't recognise my other hard disk - which had Ubuntu on it. 

So I am about to re-format all disks and start again and this may see the device being recognised by Ubuntu. I may even use this opportunity to get rid of Windows and have a few Linux OSs happening.

So, that's all for now. If the difficulty remains after a new format I'll be back.

thanks, cheers

---

