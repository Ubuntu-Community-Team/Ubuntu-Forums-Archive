---
title: "getting sound card working"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by trigsenior on 2008-10-18
**********  moved to [http://ubuntuforums.org/showthread.php?p=5988865#post5988865](http://ubuntuforums.org/showthread.php?p=5988865#post5988865) ********************




hello!

I m having sound card problems , Its integrated into mother board which is unusual , it came with windows driver but alas no linux  :mad:
oh well hope you can help many many thanks =) 

using ubuntu Intrepid Ibex Beta

here is lscpi

```
#
00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
#
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
#
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
#
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
#
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
#
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
#
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
#
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
#
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
#
00:08.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
#
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
#
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
#
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
#
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
#
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
#
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
#
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
#
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
#
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
#
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
#
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
#
04:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
#
05:05.0 PCI bridge: Texas Instruments PCI2250 PCI-to-PCI Bridge (rev 02)
#
05:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
#
05:07.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
#
06:00.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
#
06:01.0 USB Controller: NEC Corporation USB (rev 41)
#
06:01.1 USB Controller: NEC Corporation USB (rev 41)
#
06:01.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
```

and 

aplay -l

```
  32.
      **** List of PLAYBACK Hardware Devices ****
  33.
      card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  34.
        Subdevices: 0/1
  35.
        Subdevice #0: subdevice #0
  36.
      card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  37.
        Subdevices: 1/1
  38.
        Subdevice #0: subdevice #0
```

many thanks.

---

### Post by Ryadt on 2008-10-18
Please post in the Intrepid sub-forum. 
[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by trigsenior on 2008-10-18
moved to 

[http://ubuntuforums.org/showthread.php?p=5988865#post5988865](http://ubuntuforums.org/showthread.php?p=5988865#post5988865)

---

