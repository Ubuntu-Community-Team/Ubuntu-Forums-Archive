---
title: "Decent webcam software?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Cam on 2008-08-12
Hiya, I have been an on-again off-again Ubuntu user for a few years now, but I think it has finally found a permenent spot on my laptop. I am looking for some decent software to use with my laptops inbuilt webcam. The internet in general recommends Cheese, which I downloaded and works fine, except for 2 main points:

-No sound in recorded video [I do have a mic there]
-After recording a video, webcam shuts down and program needs to be restarted.

Is there any other software out there that is good to use with my webcam, that will record sound as well as video?

Cheers :-)

---

### Post by Crafty Kisses on 2008-08-12
Post the following outputs:
```
lspci
```
The the last one:
```
lsusb
```

---

### Post by Cam on 2008-08-12
lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

lsusb:
```
Bus 007 Device 003: ID 064e:a101 Suyin Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by Crafty Kisses on 2008-08-12
From the looks of it, this list may help you.

There are a number of possible solutions....

Palantir:
[http://www.fastpath.it/products/palantir/](http://www.fastpath.it/products/palantir/)

Camsource:
[http://camsource.sourceforge.net/](http://camsource.sourceforge.net/)

These are just two examples. For home security, you could use ZoneMinder:

Zoneminder:
[http://www.zoneminder.com/](http://www.zoneminder.com/)

or Motion:
[http://www.lavrsen.dk/sources/webcam/motion_guide.htm](http://www.lavrsen.dk/sources/webcam/motion_guide.htm)

I hope this is useful information.

There's also a lot more like Skype, Ekiga and Cheese.

---

### Post by Cam on 2008-08-12
> **Codename said:**
> From the looks of it, this list may help you.

There are a number of possible solutions....

Palantir:
[http://www.fastpath.it/products/palantir/](http://www.fastpath.it/products/palantir/)

Camsource:
[http://camsource.sourceforge.net/](http://camsource.sourceforge.net/)

These are just two examples. For home security, you could use ZoneMinder:

Zoneminder:
[http://www.zoneminder.com/](http://www.zoneminder.com/)

or Motion:
[http://www.lavrsen.dk/sources/webcam/motion_guide.htm](http://www.lavrsen.dk/sources/webcam/motion_guide.htm)

I hope this is useful information.

There's also a lot more like Skype, Ekiga and Cheese.

Thanks for all those solutions, but it seems that most of those revolve around streaming content directly online, and I think my head exploded while reading about Camsource :lolflag:

---

### Post by Crafty Kisses on 2008-08-12
> **Cam said:**
> Thanks for all those solutions, but it seems that most of those revolve around streaming content directly online, and I think my head exploded while reading about Camsource :lolflag:

Haha, then Ekiga will probably work for you.

---

### Post by Cam on 2008-08-12
> **Codename said:**
> Haha, then Ekiga will probably work for you.

Had a look at Ekiga, sound wouldn't work on that either [and couldn't find any options for recording audio]. Looks like I'll leave video recording to my Windows PC - thanks anyway ;)

---

### Post by Crafty Kisses on 2008-08-12
> **Cam said:**
> Had a look at Ekiga, sound wouldn't work on that either [and couldn't find any options for recording audio]. Looks like I'll leave video recording to my Windows PC - thanks anyway ;)

Have you tried messing with alsa?

---

### Post by Cam on 2008-08-12
[QUOTE=Codename;5572310]Have you tried messing with alsa?[/QUOTE

alsa 101 if you please good sir, you are talking to the biggest n00b on here ;)

---

### Post by Crafty Kisses on 2008-08-12
Run this command:
```
alsamixer
```
Just mess with the volumes and see what you can come up with, if still no luck post back.

---

### Post by Cam on 2008-08-12
Turns out my mic gains were all the way down... but even though i turned them up, now when i try to record video using cheese (none of the other programs let me record video), all i get is faint hissing static and no voice :(

---

### Post by Crafty Kisses on 2008-08-12
Try a couple of things for both the Cam and the Mic.

Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

Now for the mic, I'm not sure if the mic requires drivers, but that's very weird, you could always try the following, go into Gnome-Volume-Control and:

1) Open Edit>Preferences and check everything
2)Under the Playback tab, unmute everything and make sure everything is turned up (adjust PCM and Front to control volume and bass to your taste)
3)Under Recording tab, unmute everything and turn up everything
4) Under the Switches tab, check everything EXCEPT FOR Mic as Output which should remain unchecked
5) Under the Options tab, Input Source should be set to Mic

---

### Post by ellankavi on 2008-08-12
i think u have the exact problem as i did. well, my purpose was for webchat. Try skype if that's  the case.

---

### Post by Crafty Kisses on 2008-08-12
> **ellankavi said:**
> i think u have the exact problem as i did. well, my purpose was for webchat. Try skype if that's  the case.

Skype is really great for webchat, but the mic should work after this, if not just let me know and I'll look into it further.

---

### Post by Cam on 2008-08-12
> **Codename said:**
> Try a couple of things for both the Cam and the Mic.

Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

Now for the mic, I'm not sure if the mic requires drivers, but that's very weird, you could always try the following, go into Gnome-Volume-Control and:

1) Open Edit>Preferences and check everything
2)Under the Playback tab, unmute everything and make sure everything is turned up (adjust PCM and Front to control volume and bass to your taste)
3)Under Recording tab, unmute everything and turn up everything
4) Under the Switches tab, check everything EXCEPT FOR Mic as Output which should remain unchecked
5) Under the Options tab, Input Source should be set to Mic

Once again, nothing
/cry

---

### Post by Cam on 2008-08-12
I don't think I'll worry too much about this dudes... last time I became obsessed with fixing something Ubuntu related I cracked the poo and just installed Windows again. I don't want to do that this time so I won't worry about it ;)

Thanks for your help though Codename :)

---

### Post by Crafty Kisses on 2008-08-12
> **Cam said:**
> I don't think I'll worry too much about this dudes... last time I became obsessed with fixing something Ubuntu related I cracked the poo and just installed Windows again. I don't want to do that this time so I won't worry about it ;)

Thanks for your help though Codename :)

I'm still looking for fixes, I might have something, try Audacity for your Mic, and mess with the preferences, that could very well work and if that works from there, I have some ideas.

```
sudo apt-get install audacity
```

---

### Post by Cam on 2008-08-12
audacity produces only static when I use OSS to capture audio, and loud crackling that leaves a continuous popping in my speakers when I use alsa.

---

### Post by Crafty Kisses on 2008-08-12
Not sure who makes your Mic, from the results of "lsusb" it looks like AuthenTec, if that's the case this link may help you > [http://mediakey.dk/~cc/bisoncam-ali-m5603c-linux-driver-round-up/](http://mediakey.dk/~cc/bisoncam-ali-m5603c-linux-driver-round-up/)

I've also read up on some of the AuthenTec Mics, and you might have to alter the kernel a little bit, but here is a great link over at Fedora > [http://forums.fedoraforum.org/showthread.php?t=160290](http://forums.fedoraforum.org/showthread.php?t=160290)

This should help you a little. Any more questions just ask I'll be glad to help.

---

