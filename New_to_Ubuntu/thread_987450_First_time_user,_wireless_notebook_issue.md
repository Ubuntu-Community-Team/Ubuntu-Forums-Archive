---
title: "First time user, wireless notebook issue"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by ziokun on 2008-11-19
Ok so I've got this Gateway ***[notebook]("http://support.gateway.com/s/Mobile/2007/Oasis/1014479R/1014479Rsp2.shtml")*** as a gift for college, ripped out vista and installed ubuntu as an experiment and realy enjoy the look and feel of it
only problem is the built in wireless card refuses to work, I kinda know how to navigate the terminal if there is any other info that needs to be posted

---

### Post by LowSky on 2008-11-19
from terminal type ```
lspci
``` and paste what it says here

---

### Post by ziokun on 2008-11-19
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by wolfen69 on 2008-11-19
did you go to system>administration>hardware drivers to see if the driver is there?

---

### Post by ziokun on 2008-11-19
> **wolfen69 said:**
> did you go to system>administration>hardware drivers to see if the driver is there?

Odd I don't have the hardware drivers tab, is there somewhere else I can check?

---

### Post by loboc on 2008-11-19
Find the wireless card driver for a windows system and use the ndiswrapper workaround technique to get your card working 

Search the forums for a ndiswrapper howto

---

### Post by ziokun on 2008-11-19
> **loboc said:**
> Find the wireless card driver for a windows system and use the ndiswrapper workaround technique to get your card working 

Search the forums for a ndiswrapper howto

Problem is all the drivers on the [Gateway site]("http://support.gateway.com/support/drivers/search.asp?st=pn&param=1014479R") are for Vista, which I no longer have

---

### Post by ziokun on 2008-11-27
bump

---

