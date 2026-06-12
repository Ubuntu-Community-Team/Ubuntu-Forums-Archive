---
title: "Echoing Sounds. :("
date: 2008-09-22
forum: New to Ubuntu
---

### Post by SavageTendencies on 2008-09-22
I've been looking all over the forums and I've googled as much as I can, to no avail.

Every time there is any sound whatsoever, it echoes. It plays it over and over again until(after a long time depending on the sound played) it fades away.

I have no idea what to do. System sounds, video files, sound files, flash, everything makes a terrible echo. 


I'm sort of a n00b, so any help would be GREATLY appreciated.


By the way. This is on my girlfriends laptop, and all I know about it is that it's a Gateway. :confused::confused::confused:

---

### Post by Crafty Kisses on 2008-09-22
Post the results of this command:
```
lspci
```

---

### Post by SavageTendencies on 2008-09-26
> **Codename said:**
> Post the results of this command:
```
lspci
```
Here are the results.
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

---

