---
title: "help with 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by beany1 on 2008-11-02
hi, been using hardy heron since its release, decided to upgrade to 8.10, which once finished presented me with the desktop, both gnome pannels, etc, and about 30 seconds of usability before the system froze with no activity, i just assumed this was a bad installation, so then downloaded the live cd, after using the cd checker i was reported to have a working cd, so began to load live cd, to which my system froze, so instead i tried booting just to install this also just froze both at the point were the "desktop" is loading, so i then tried installing 8.10 from the text alternative cd, which half way through install asked me to insert the cd, that was already in but wouldnt let me eject or anything, tried with all the usual noapic nolapic apci=off etc, to no avail, so assumed i had a cd drive problem, so i tried to reinstalled hardy heron, from cd which installed perfectly fine, and then for some reason i tried to upgrade again, lol, to which i was presented to the frozen desktop after 30 seconds once again, it also frezes after about 30 seconds on the login screen, iv tried bootin with the apci options aswell, and i am unable to switch to the full screen console thing with alt and the f keys, hardware: amd x2 4400+, 2gb ram, m2n32-sli deluxe, I havnt plugged in any new hardware, and all the current hardware works fine with hardy heron....
cheers for reading! lol

---

### Post by stephanvaningen on 2008-11-02
fff that's not an easy one... Did you look for system logs? A thing to get a step closer could be to install 8.10 and after a freeze, boot from liveCD of 8.04 and mount the '/' of the Intrepid and look through the system log files...

---

### Post by beany1 on 2008-11-02
hi, cheers for the speedy reply, well I assume u mean like the logs in /var/log/ and then messages, iv attached the file in a zip, im really clueless to what to look for (or what to do), just before each supposed restart there is entries about my wireless card, that worked in heron, and also pulseaudio? cheers once again

---

### Post by bscbrit on 2008-11-02
I agree with your interpretation of the messages.  It is the wireless driver that seems to be dragging the system down.  I would recommend that you go back to 8.04 for a week or two until 8.10 stabilises.  Quite a few are having problems and it will take a while to sort them all out.  

One way to prove that it is the wireless driver would be to remove the wireless card from the system (if you are able and confident enough to do that) and reinstall 8.10 again.  Of course, if it was successful you would have a computer without a network connection but it would indicate fairly decisively where the problem lies in 8.10.  As you point out, it all worked fairly well under 8.04.

I've got to start converting 4 computers back to 8.04 tomorrow because 8.10 has proven to be unstable for the time being.  Good Luck.

---

### Post by beany1 on 2008-11-03
cheers guys, yeah its screwed to the mobo, plus i need the wireless cards i have for my degree, and i use them in windows, so will wait a while till 8.10 many thanks!

---

### Post by stephanvaningen on 2008-11-06
Can you dump the result of this command in this thread:
 ```
lspci
```
(This will give information on the wireless card too)

---

### Post by beany1 on 2008-11-07
hi sorry about delay, im assuming u mean from 8.04? here goes:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:07.0 Multimedia audio controller: Creative Labs SB X-Fi
02:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
02:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

many thanks!

---

### Post by beany1 on 2008-11-11
any ideas? or am i just playing the waiting game, hoping 8.10 will be OK in a while? 

oh just realised, i posted lspci for you, which iv just realised only displays PCI :| lol i believe the wireless card that is causing me trouble is not the PCI card but is a RTL8187 which is screwed to the mobo, off a USB header, which only started to work in newer releases of linux,  but either way I do require them for uni, so cant really remove!

many thanks!

---

