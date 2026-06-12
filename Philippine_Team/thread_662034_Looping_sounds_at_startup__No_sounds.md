---
title: "Looping sounds at startup / No sounds"
date: 2008-01-08
forum: Philippine Team
---

### Post by ayanph on 2008-01-08
Hi I don't know if you've experienced this but when I installed mint on my MSI computer I get this problem where the startup sound keeps on looping.  

There would be times that there's no startup sounds but everything seems to be working when I get to my desktop.

Any suggestions? I'm kinda new to FOSS and would really love to learn.

My computer specs:

MSI (Micro-Star Incorporated) Megabook VR320-K2 Laptop.
* Intel Core 2 Duo Mobile Technology
* Intel Core2 Duo T5200
* (1.60GHz 533MHz 2MB L2 Cache)
* ATI 410ME Chipset
* ATI Mobility Radeon X200 Graphics 256MB Shared
* 1GB DDR2 Memory
* 80GB Hard Disk Drive
* Super Multi DVD+/-RW/Ram Dual Layer Drive
* Super Glare 13.3" Widescreen Display
* 4-in-1 Card Reader
* Firewire port
* 10/100LAN
* 56K Modem
* 6-cell Battery
* 2.1kg


lspci shows:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
04:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
04:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
04:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
04:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
04:09.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

---

### Post by perbiu on 2008-01-09
Subukan niyo ayusin sa Sound Preference, Tanggalin sa Autodetect.

---

### Post by Nhatz on 2008-01-10
Dude pareho tayo ng problem.... ganyan din Laptop ko may problema pa yata sa gutsy (7.10) yan.. naginstall ako fiesty (7.04) yun! naayos yung looping sound problem.... try mo nalang muna install ng fiesty. hehehehehe....

---

### Post by ayanph on 2008-01-10
hehehe! magtitiis na muna siguro ako... hindi naman palagi may problem sana mafix na sa susunod na release.

---

### Post by ayanph on 2008-01-28
It fixed itself... it's no longer looping. I guess they fixed it already... i regularly download updates kasi.

---

### Post by ayanph on 2008-04-28
it came back. anyway i was looking for articles online and saw a number of users with this laptop having the same problem. will either downgrade back to ubuntu 7.04 where it doesn't happen or will try other distos like opensuse or mandriva or gOS.

---

### Post by ayanph on 2008-07-19
I downgraded back to 7.04 and the problem dissappeared

Also found this article on how to resolve this for MSI laptop

[http://blog.xanda.org/?p=437](http://blog.xanda.org/?p=437)

maybe useful for those having the same issue

---

### Post by Nessa on 2008-07-20
Fresh install ba yung Heron mo or upgraded?

---

### Post by Nhatz on 2008-07-20
ayanph... dude solved na yang problem sa MSI notebooks. sa bagong kernel ang problem. install mo yung Linux-386 then ok na sya.

```
sudo apt-get install linux-386
```

ASTIG! :guitar:

---

