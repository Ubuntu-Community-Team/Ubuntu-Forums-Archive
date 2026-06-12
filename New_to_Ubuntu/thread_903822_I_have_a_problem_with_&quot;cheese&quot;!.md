---
title: "I have a problem with &quot;cheese&quot;!"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by crimesaucer on 2008-08-28
The cheese program will not record real sound from a microphone, it also will only playback video in fast motion.

---

### Post by Crafty Kisses on 2008-08-28
For video try this:

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

Also post the ouput of > lspci

---

### Post by crimesaucer on 2008-08-28
The picture shows with ekiga, but still no real sound.

lsusb:

```

$ lsusb
Bus 004 Device 003: ID 064e:a110 Suyin Corp. 
Bus 004 Device 001: ID 1d6b:0002  
Bus 003 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 001: ID 1d6b:0002  
Bus 001 Device 001: ID 1d6b:0001  

```

lspci:

```

$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```


Thanks for the info on ekiga, hopefully I'll fix this driver issue with the hp microphone and cam.

---

### Post by Crafty Kisses on 2008-08-28
Have you tried the Ekiga method yet?

---

### Post by crimesaucer on 2008-08-28
> **Codename said:**
> Have you tried the Ekiga method yet?

After installing it and configuration... still no sound... checked all of the audio codecs... tried both the hda NVIDIA and the default... both alsa and oss... still no sound... only video.


Sound does not work in either webcam apps. Video record/playback in cheese does not work correctly... streaming of webcam is normal... just no sound and cheese problems with recording.

Sound & Video-->-- Sound Recorder also does not work with embedded microphone.

(both microphone and webcam work in Vista...)

---

