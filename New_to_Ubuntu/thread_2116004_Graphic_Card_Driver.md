---
title: "Graphic Card Driver"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by daniell59 on 2013-02-14
Tomorrow I plan to do a clean install to 12.04. What would be the best driver that I can download for my video card?

Thanks

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)

---

### Post by Sealbhach on 2013-02-14
Ubuntu will look at your system and suggest the best driver for you once you have the desktop installed. No need to worry about that.

.

---

### Post by daniell59 on 2013-02-14
> **Sealbhach said:**
> Ubuntu will look at your system and suggest the best driver for you once you have the desktop installed. No need to worry about that.

.

Thanks, are there proprietary drivers that are better?

---

### Post by Bashing-om on 2013-02-14
daniell59; Hi !

From your output:
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]and per:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced this summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.(Mark Phelps)Means for now there might be a proprietary driver available for 12.04 version but if you decide to upgrade the operating system, will have to use the open source driver - which I understand works very well.[INDENT][INDENT]hope this helps

[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2013-02-14
> **daniell59 said:**
> Thanks, are there proprietary drivers that are better?

You don't need the proprietary drivers unless you need hardware-based 3D acceleration (for Gaming) or GPU temp control (for overclocking).

The default open-source drivers are quite suitable for everyday use -- and they are installed automatically.

---

