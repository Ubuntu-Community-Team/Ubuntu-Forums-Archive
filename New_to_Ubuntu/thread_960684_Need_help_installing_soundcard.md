---
title: "Need help installing soundcard"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by USA Gold on 2008-10-27
I need help getting my sound blaster audigy card installed. I already have alsa installed but it says there are not any devices to control.

---

### Post by john_spiral on 2008-10-27
open a terminal and type:

lspci

post the results

---

### Post by USA Gold on 2008-10-27
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
01:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
06:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
06:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
06:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

Thanks just let me know where to go from here.

---

### Post by john_spiral on 2008-10-28
got the below solution from the forum:

"I fixed the volume control by simply changing the "visible tracks" (sound manager->preferences) to the one that my sound was running through. Silly me." [[COLOR="Blue"]_link_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=927174&highlight=sound+blaster+audigy")

give it a try

or

"It worked as far as driver installation, etc. but the settings were off and rendered the sound card useless for a while. It turned out that the default output for a Linux installation was the soundcard's DIGITAL output, not analog. So, for those using the ANALOG output, open a terminal window and type 'alsamixer'. Use the right arrow to move all the way to the 'Audigy Analog/Digital Output Jack' (keep an eye on the Item value in the top left of the window). Now, hit the 'M' key to toggle the value between On and Off. This switches the digital output on and off. Since I was using the Analog output, I needed to have this OFF so I could listen to stuff. Worked like a charm!"

[http://www.linuxcompatible.org/Soundblaster_Audigy_c10028.html](http://www.linuxcompatible.org/Soundblaster_Audigy_c10028.html)

---

### Post by USA Gold on 2008-10-28
Thanks I got my onboard sound working last night, I will work some more on my sound blaster when I get home from work.

---

