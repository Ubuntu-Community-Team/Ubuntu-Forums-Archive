---
title: "Is HP Deskjet 3055A All-in-One Wireless Printer supported?"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by resander on 2013-06-14
My old HP DeskJet D1470 is not working any more, so need to get another HP in a hurry. An All-in-One.

Does HP Deskjet 3055A work with Ubuntu 12.04 LTS? or what other HP all-in-one printers models would?

Ken

---

### Post by BioHazardTM on 2013-06-14
Hi, HP printers and scanners are supported by HPLIP proyect (HP Linux Imaging and Printing), here there are the supported devices: [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

The HP Deskjet 3055A is supported and recommended in the HPLIP page: [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050a_j611_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3050a_j611_series.html)

In Ubuntu the HPLIP drivers are installed by default.

---

### Post by resander on 2013-06-14
Brilliant!

Will order right away and report back here when I have tried it.

Many thanks BioHazardTM

---

### Post by resander on 2013-06-17
I am using Ubuntu 12.04 LTS on a 64-bit desktop PC.

The HP 3055A printer has arrived and wired connection worked fine with USB cable between the PC and the printer. Black and white mode and colour mode worked very well and the speed of printing is a lot faster than my old HP Deskjet D1470.

Next step is to use the scanner in the 3055A all-in-one, initially using wired connection.
The 3055a printer has a small LCD touch-screen control panel for initiating Copy, Scan and setting options. Pressing Scan on the control panel generates error message 'Computer Not Found'.

Q1. how do I tell the printer about my PC?

Before getting the 3055a I had an Epson scanner connected to the PC and used Ubuntu applications Simple Scan and Xsane to initiate scans, crop etc.

Q2. how do I enable scannning from the PC using SimpleScan and/or Xsane with the 3055a?

Q3. it would be convenient to be able to initiate scanning from the printer control panel and also from the computer using Simple Scan and/or Xsane. Is that possible? Or would I have to disable one of them first?

The 3055a came with an install disk for Windows and Mac. There is no install disk for Linux distros and the help files that I installed on Windows 7 dual-booted on this PC contains no information for Ubuntu. 
   
Would be most grateful for advice how to use the scanner of the 3055a all-in-one with my desktop PC.

Ken

---

### Post by resander on 2013-06-18
Answer to Q2: how to prepare for Xsane and Simple Scan for the HP 3055A?

No action needed. Xsane and Simple Scan work with the HP 3055A with Ubuntu 12.04 using wired connection. 
Good quality scan.

Have not tried to get wireless connection yet for scanning and printing. Don't know how to...
Hints welcome.

Ken

---

### Post by BioHazardTM on 2013-06-27
Hi Ken, sorry for the delay.

Well, about Q1: I don't know if you can use the physical buttons of the printer in Linux, I have a HP Laserjet, but doesn't have a Scan button, so I can't tell you.

About Q3: First you'll have to connect it to your network, look at the LCD panel if there is any network configuration, so you can connect the printer to the WiFi, after that, open a browser and write the printer IP showed in the LCD and you should see something like this [http://img443.imageshack.us/img443/862/rkh9.png](http://img443.imageshack.us/img443/862/rkh9.png)

After that, you go to System configuration, Printers, Add, Network printer, wait a bit and it should appear.

---

