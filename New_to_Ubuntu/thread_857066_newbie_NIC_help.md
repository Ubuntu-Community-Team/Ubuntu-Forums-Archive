---
title: "newbie NIC help"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by pdorczuk on 2008-07-12
I am brand new to Ubuntu and I cannot find out how to get my NIC card to work. I have a Realtek8139/810x Ethernet NIC. Ubuntu won't autodetect it and I have not been able to find anything online to get it working. I would appreciate any help. thanks.

---

### Post by iaculallad on 2008-07-12
> **pdorczuk said:**
> I am brand new to Ubuntu and I cannot find out how to get my NIC card to work. I have a Realtek8139/810x Ethernet NIC. Ubuntu won't autodetect it and I have not been able to find anything online to get it working. I would appreciate any help. thanks.

Post whatever displays when you issue the command below using your terminal:

```
lspci
```

---

### Post by pdorczuk on 2008-07-12
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


i also have a dual boot with windows xp, i dont know if that changes anything.

---

### Post by hyper_ch on 2008-07-12
what does
```

ifconfig

```
return?

when posting any output enclose it with [noparse]```

```[/noparse] brackets

---

