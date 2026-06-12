---
title: "HELP ATI HDMI no sound to TV"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Bright Hammer on 2008-11-30
Hi, I am having problems getting my audio working.  I have a Gateway T1620 and everything else works fine. I just got a new HDTV and I hooked it up to my T1620 and it is working trough HDMI  but I dont have any sound please help!!!

T-1620 Notebook Specifications
Part Number: 1014881R Gateway T-1620 Notebook
AMD Turion™ 64 X2 Mobile Technology TL-56
1.8 GHz | 512 KBx2 L2 Cache 
HyperTransport™ technology at up to 1600 MHz) 
Chipset ATI RS690T 
Display panel 14.1-inch WXGA TFT display (1280 × 800) 
Memory 2048 MB 667 MHz DDR2 SDRAM (2 × 1024)
Total slots: 2 DDR2 slots | Available slots: 0 DDR2 slots 
Video controller ATI Radeon® X1270 graphics 
Up to 256 MB of HyperMemory™ 
Webcam 1.3 Megapixel 
Audio High definition audio - 2 channel
Hard drive 250 GB 5400 RPM SATA hard drive 
Optical drive 8X Multi-Format Dual Layer DVDRW with DVD-RAM and Labelflash™ 
Modem Integrated V.92 56K modem 
Network 10/100 Ethernet LAN 
802.11a/b/g Wireless LAN
Memory card reader 5-in-1
Interfaces Three - USB 2.0 ports 
One - VGA port 
One - HDMI connector

I did an  lspci | grep Audio
 and got the following

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller



:confused:

---

### Post by Riffer on 2008-11-30
Some HDMI hook ups require a separate audio cable.  What TV do you have?  I know on mine there are 2 slots for HDMI and only one has audio support.

---

### Post by Bright Hammer on 2008-11-30
I have a new Samsung. I have everything working under vista so that isn't it. I searched the fourms but i just cant find anything that works for me. I even tried to do it via pulse audio so now it might be even harder to fix. Does anyone know a good how to?

---

### Post by markbuntu on 2008-11-30
Get the gnome-alsamixer if you do not have it already.

Open it, open the ATI HDMI tab and click on the IEC958 box.

You may need to update your graphics driver in hardy because HDMI sound support is not avialble in ati drivers before 8.9.

There are sections here about HDMI and digital output in general that may be helpful:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Bright Hammer on 2008-12-06
If anyone else has this problem here is the fix.

Step 1. Follow the instructions on the link below. It will help you configure your settings correctly. When you can here the test audio on your TV then move to step 2

[http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/](http://www.mandladventures.com/2008/11/03/ubuntu-810-hdmi-sound-configuration/)

Step 2. follow the instructions in this link below. Remember always backup your original config file before making changes.

[http://www.benjiegillam.com/2008/10/working-hdmi-audio-on-ati-graphics-card/](http://www.benjiegillam.com/2008/10/working-hdmi-audio-on-ati-graphics-card/)

Reboot and you should have sound trough your HDMI port. XBMC here I come.
:D

---

