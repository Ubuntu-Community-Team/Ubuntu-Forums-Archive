---
title: "Can my Mustek PVR-H140 be connected to Ubuntu 8.04LTS?"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-30
Ubunteros,

I have Linux Ubuntu 8.04LTS. I was curious to know if my Mustek PVR-H140 can be connected to my machine??? I did connect my PVR but Ubuntu only recognized the USB connection and nothing else.

Would be great to get this working so that I can see what's on the hard drive of my PVR.

Maybe one of you can tell me how it's done?

Thank You!

---

### Post by phidia on 2008-10-30
Take a look at the wiki [here]("https://help.ubuntu.com/community/PortableDevices"). After plugging it in with file sharing on what output do you get in "dmesg" & "lsusb"?

---

### Post by suomalainen on 2008-10-30
Thanks Phidia!
Can you please explain what means:

"After plugging it in with file sharing on what output do you get in "dmesg" & "lsusb"?"

Thank You

---

### Post by phidia on 2008-10-30
after you plug the device in (is this a video camera or recorder?) open a terminal from Applications > Accessories and enter > dmesg Note/copy the output.
The enter > lsusb same as before copy the output. Post that here as an attachment.

---

### Post by suomalainen on 2008-10-30
Phidia,

Here is the output you requested.

---

### Post by suomalainen on 2008-10-30
Additional info on the device I'm trying to connect can be found here:

[http://www.mustek.com.tw/html/prod_pmc/PVR-H140.html](http://www.mustek.com.tw/html/prod_pmc/PVR-H140.html)

I also attached a pic to this post.

[COLOR="Black"]**Mustek Model: PVR-H140**[/COLOR]

*  Up to VGA 30 fps AV recording (MPEG 4 compatible file format) through AV In with timer record feature
* 3.6" Color TFT LCD; Adjustable LCD brightness
* Up to 40GB HDD storage capacity allows users to back up files from memory cards
* Multi-language user interface
* Stand design allows users to enjoy the multimedia comfortably
* TV playback through AV Out
* High speed USB 2.0 supported


**Specifications**

Product Function 	Digital Video Player . Digital Video Recorder / Digital Photo Player / Music Player / USB Pocket Drive / SD/MMC Card Reader / Digital Voice Recorder
Display 	3.6" Color TFT LCD
Microphone 	Built-in
Speaker 	Built-in
Hard Disk 	40 GB HDD
DPS Support 	Yes
Interface 	AV in / AV Out / Earphone / DC-in / USB 2.0
Memory Card Slot 	SD/ MMC
Power Source
Internal 	Rechargeable Li-ion Battery (1000 mAh) x 2
External 	Power Adapter
Dimensions
	110 x 80 x 30 mm (L x W x H)
Weight 	290 g (with Battery)

System Requirements
For PC

    • Pentium 500 MHz processor or higher
    • Microsoft Windows 98SE / Me / 2000 / XP
    • Available USB port
    • Super VGA card and color monitor
    • CD-ROM or DVD-ROM drive
    • At least128 MB RAM
    • 200MB available HD space

Mass Storage

    • Win98SE, Me, 2000, XP
    • Mac OS 9,X and 10.1 above

---

### Post by phidia on 2008-10-30
I see from a brief google search that sellers of your media device claim it has linux support: > OS compatibility: Windows 98SE/Me/2000/XP; Mac OS 9.X and 10.1 above; Linux 2.4.X above 

There must not be a lot of people using it in linux though since I didn't see a howto anywhere.

You can look carefully through the link I previously supplied. That link is for pluggable devices.

---

### Post by suomalainen on 2008-10-30
There are a number of plugable devices but none that I recognize supporting the Mustek. Perhaps I'm over looking something?

---

