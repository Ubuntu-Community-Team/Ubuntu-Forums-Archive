---
title: "Pls help!!"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Naraya on 2011-11-09
I am a completly new linux user. I was trying to load Xubuntu 11.04 desktop for X_86 from live CD following the intructions given on the website. The system just freezes leaving the leds on keyboard blinking. The text on screen is as follows:
]
No filesystem could mount root, tried ext3 ext2 ext4 fusebulk
kernel panic-not syncing:VFS:unable to mount root fs on unknown block(8,1)
 
*i tried to use a live USB but the same thing happens.
 
Processor- Intel Pentium 4 @2.66GHz
RAM-512 MB DDR1
Mother board-PI865D7 
 
Full Specifications 
 
CPU LGA775 socket for latest Intel Pentium 4/Celeron D processors/Pentium D processor 
FSB 800/533 MHz 
Chipset Intel 865GV/ICH5 
Graphic Integrated Intel Extreme Graphics II 
Memory • Dual-channel DDR memory architecture 
• 2x 184-pin DDR DIMM socket support up to 2 GB 
• Support DDR400/333/266 2.5V DDR SDRAM 
Expansion Slots • 1 x AGP ultra 
• 3 x PCI 
• 1 x CNR 
LAN Realtek RTL8100C 10/100Mbps Faster Ethernet controller 
 
Audio • RTL ALC655 6-channel audio Codec 
• Compliant with AC'97 2.3 specification 
Storage Support by Intel ICH5
4 x Ultra DMA100/66 devices 
2 x Serial ATA devices 
 
Back Panel I/O Ports • 1 x PS/2 keyboard 
• 1 x PS/2 mouse 
• 1 x Parallel Port 
• 1 x Serial Port 
• 1 x VGA Port 
• 4 x USB 2.0 Ports 
• 1 x RJ 45 Port 
• 1 x Audio I/O (Line-in, Line-out and Mic-in) 
Internal I/O Connectors & Headers • 20-pin ATX Power Supply connector 
• 4-pin ATX 12V Power Supply connector 
• 2 x USB header support additional 4 USB2.0 ports 
• 2 x Serial ATA connectors 
• 1 x Front panel switch/LED header 
• 1 x Front panel audio header 
• CPU / PWR/ SYS FAN headers 
• 1 x IrDA for SIR header 
• 1 x Speaker header 
• 1 x CD in header 
• 1xFloppy connector-support 360K~2.88M Byte, 3 Mode FDDs or LS120 
System BIOS • Award 4Mb Flash ROM 
• Supports Plug and Play 1.0A, APM 1.2, Multi Boot, DMI 
• Full support for ACPI revision 1.0 specification 
 
Form Factor Micro-ATX Form Factor, 244*244mm 
 
 
 
Thank you.

---

### Post by sadaruwan12 on 2011-11-09
Welcome to the forum and to Ubuntu.

Your motherboard chip set is 865D thats a very old P4 chipset if I'm right it was the beginning of the 775 socket painless motherboards.

And it seems like your kernel or the main part of the operating system is panicking in other words want recognize hardware or there's a clash.

I would recommend going with Lubuntu rather than using the Xubuntu version there are some GRUB or very geeky stuff that other forum members will help you with but better to try the Lubuntu version first.

---

### Post by Naraya on 2011-11-09
thanks for the suggestion. 
will try that.

---

### Post by docbop on 2011-11-09
That is a pretty old system and only 512MB RAM and part of that the video is using.   I use old P4's and sometimes have to use older or different versions of Linux.    You might want to try the previous Ubuntu 10.04 LTS . It is a real solid Ubuntu that a lot of the pentest Linux's are based on. You'll probably get better performance with the 10.04 on an older system.

---

### Post by mikewhatever on 2011-11-09
There may be a problem with the installation media. When booting from the CD, hit any key as soon as the purple background appears. You should then get a menu with one of the entries offering to check the CD for errors. In case there are any errors, re-burn the CD at a slow speed, x4 or so.

---

### Post by khelben1979 on 2011-11-09
Hmm.. I just want you to know that I have older PC hardware myself and it manages to boot the latest version of Ubuntu without any serious problems, that indicates that your pc hardware is more than sufficient for any version of Ubuntu, but I would suggest you go for another version of Ubuntu in case the image file which got burnt to disc was corrupted in some way?

As for using GNOME or the KDE desktop with 512 MB of RAM is more than enough, but for faster performance, going with a [XFCE]("http://en.wikipedia.org/wiki/XFCE") or [LXDE]("http://en.wikipedia.org/wiki/LXDE") enviroment would give you more speed.

Also, when burning the Ubuntu installation media on CD, I would recommend low burning speed to avoid any problems during that process, maybe it's worth a try? Or did you purchase the installation discs?

---

### Post by M!K3_$ on 2011-11-09
RAM is looking tight.

---

### Post by ahmed.cnbd on 2011-11-09
> **M!K3_$ said:**
> RAM is looking tight.


I agree with you

---

