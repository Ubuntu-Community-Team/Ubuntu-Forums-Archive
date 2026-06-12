---
title: "Notebook setup (Sound / Screen Resolution)"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by umopapisdn on 2008-06-17
Okay, I have installed Ubuntu (newest version) on the below specs notebook computer.

I can't seem 1) to get any sound and 2) to get the screen to resize -- right now in order to use it I have plugged in an external monitor and so my laptop screen is blank (I am wholly using the external monitor which resizes itself) -- I at first tried just changing the resolution within System/Preferences/Screen Resolution but it just gets all wonky and I have to reboot.

help? (and speak baby talk, I am a newbie)



Processor 	Intel® Celeron® M Processor 370
1 MB L2 Cache | 1.5 GHz | 400 MHz FSB
Display Screen 	14-inch Widescreen Ultrabright WXGA TFT
Chipset 	Via VN800
Memory 	256 MB DDR2 (1 × 256 MB) SODIMM
EXPANDED to 1 GB
Video 	S3 UniChrome™ Pro integrated graphics processor
Up to 64 MB shared video memory
Audio 	AC '97 2.3 Compliant audio
Hard Drive 	40-GB 4200 RPM hard drive
Optical Drive 	CD-RW / DVD Combo

Write maximum: 24x CD-R/CDRW
Read maximum: 24x CD-ROM, 8x DVD-ROM
Media Reader 	4-in-1 Digital Media Manager
Secure Digital, Memory Stick, Memory Stick-Pro, and MMC
Modem 	56K ITU V.92 ready Fax/Modem (RJ-11 port)
Network 	10/100 Mbps built-in Ethernet
802.11g integrated Wireless (up to 54 Mbps) SecureEasySetup™
Interfaces 	

    * 2 - USB 2.0 Ports
    * 1 - VGA External Connector
    * 1 - RJ11 (Modem)
    * 1 - RJ45 (Ethernet LAN)
    * 1 - Microphone In
    * 1 - Headphone / Audio Out

---

### Post by KenBW2 on 2008-06-17
Sound:
Try System > Preferences > Sound and changing all the dropdown boxes to ALSA.

Resolution:
Try
```

sudo dpkg-reconfigure xserver-xorg

```

These are just guesses, but they may work

---

### Post by umopapisdn on 2008-06-17
No sound still -- if I use the sound "dial" on the front of my notebook a sound icon pops up on the screen and if I hit the button for mute there is a mute icon.. but there is no sound coming out of the speakers (or external speakers if I attach them).

for the resolution -- when I boot up, my screen size is larger than my actual screen by about four times (so I can only see/scroll around the top left corner of the desk top). If I use an external monitor and select it as primary before ubuntu loads, then the screen is fine (but the one on the notebook is blank). Tried your suggestion and it didn't change anything. If I change the screen resolution in preferences then it gets weird (as if its all overlayed on top of itself).

shrug.

---

### Post by KenBW2 on 2008-06-18
Ah, I had that problem, but I forget what I did to fix it...
Try just typing you username and password in, wait for it to log in and then change the resolution then and see if that helps.

---

