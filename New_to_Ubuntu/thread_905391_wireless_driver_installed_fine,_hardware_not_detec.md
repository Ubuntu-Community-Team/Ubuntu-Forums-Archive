---
title: "wireless driver installed fine, hardware not detected"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by univremonster on 2008-08-30
I'm sure there's an easy fix to this and it may well have even been posted on the fora before, but here's my problem.

I bought a wireless card to stick on my computer.  I put it in, downloaded the driver and installed ndisgtk, ndiswrapper-common, and ndiswrapper-utils-1.9.  If I go to System -> Administration -> Windows Wireless Drivers, the correct driver appears as installed, but says "Hardware present: no".  The rub is that the hardware is present.  Is there some way I add this hardware so Ubuntu can "see" it?

---

### Post by gmxgeek on 2008-08-30
make and model of the card?

---

### Post by univremonster on 2008-08-30
The card is a Netgear Wireless-G WG311.  The driver is wg311v2.

---

### Post by gmxgeek on 2008-08-30
post output of 
```

lspci

```
please

---

### Post by univremonster on 2008-08-30
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc 437A Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6200] (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
03:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
03:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by univremonster on 2008-08-30
A note on this that may be helpful - it seems since I plugged in the wireless card the computer thinks I have two floppy drives.  Is there a way to tell the computer that what it is looking at is a wireless card and not a floppy?

---

