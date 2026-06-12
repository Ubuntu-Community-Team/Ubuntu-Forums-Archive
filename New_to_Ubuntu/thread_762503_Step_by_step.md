---
title: "Step by step"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by IzThatHawt7 on 2008-04-22
Hello guys. I have just installed Ubuntu, and, of course, was looking through this forum to find out how to do what i need ) However, these searches were useless, and i have nothing working now. I have reinstalled it, so now I have :

1) A just-installed OS
2) Wine 0.9.58 tar archive
3) Ndiswrapper-1.48 tar archive
4) Ndisgtk 0.72 tar archive

What do I need:

1)Working Windows apps (wine should work, but it is not installing)
2)Working Wi-Fi connection (same: following the instructions leads to errors :\)
What am i doing wrong?
Also i have encountered some problems:

1)External usb HDD (Western Digital) works only one time of ten. Maybe i need some drivers?
2)USB mouse (Logitech G5) is very laggy, and i have to use touchpad. How to cure it?

And a final question: Is it possible to get pen tablet working under ubuntu?

Thanks in advance :)

---

### Post by Paraphysicist on 2008-04-22
I can help with the wine install.  The current version is 0.9.59, so dump that tar file.  

This is a good step by step guide: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#WINE](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#WINE)

Each line that is in the dotted box you just copy and paste into the terminal, press enter, and repeat for the next line.

---

### Post by TenPlus1 on 2008-04-22
Goto [www.getdeb.net](www.getdeb.net) and search for a program called wine-doors, this will simplify your WINE installation and allow you to install win-software a lot easier ...

For wireless troubles, I used this post to help me: [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

Instead of downloading the .gz files, pop into Synaptic Package Manager and do a name search for ndis, then select ndiswrapper-common and utils, and also ndisgtk for installation...  This saves you installing them manually...

Hope this helps with your wine & wireless issues...

---

### Post by PriceChild on 2008-04-22
The above software is available from the ubuntu 'repositories'. These are archives of preconfigured and tested software, ready to work quickly on your machine.

You should only use software from these repositories instead of randomly downloading things from internet sites as is the windows mentality.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) is the guide for setting up ndiswrapper. Are you sure you need it though? Please pastebin the output of lspci and lsusb in a terminal here for me to check. Another note... you should search help.ubuntu.com and wiki.ubuntu.com for guides specific to ubuntu first too ;)

---

### Post by IzThatHawt7 on 2008-04-22
Here you go... 
```
 
@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

```
and
@ubuntu:~$ lsusb
Bus 005 Device 004: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 056a:0065 Wacom Co., Ltd 
Bus 002 Device 003: ID 0e21:0603 Cowon Systems, Inc. 
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c041 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
 
Yes, as i understood, my wireless network card driver can only run with it.

---

### Post by PriceChild on 2008-04-22
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

It *will* work :)

---

### Post by mlentink on 2008-04-22
Wacom supplies linux drivers for their tablets. I just downloaded one for mine, but haven gotten around to trying it. Other priorities... ;-)

---

### Post by Paqman on 2008-04-22
Ah, you have a Broadcom 4318 wifi chipset. I've been there myself.

To be honest, getting this card to work with Linux is more trouble than it's worth. Speaking from personal experience i'd recommend simply swapping the card for one which will work without the ndiswrapper hassle. You can pick up a second hand Intel card very cheaply off eBay.

---

