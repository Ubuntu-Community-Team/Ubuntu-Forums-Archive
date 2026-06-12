---
title: "Ubuntu 12.04 recognize desktop PC  as laptop"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Gonzaki on 2012-10-16
Hi all,
I have desktop PC but Ubuntu 12.04 recognize it as laptop ?
I can't change Launcher size, I can't setup my Samsung SyngMaster 730 bf monitor... 
My Motherboard: D2700MUD Intel Corporation,
My CPU: Intel(R) Atom(TM) CPU D2700   @ 2.13GHz.
I am very beginner in linux. Can somebody help me ?

---

### Post by dim459 on 2012-10-16
Well, looks like we need a bit more information about your hardware.
Post the output of the command 
```
lspci -nn
```

Since I'm not using unity, I THINK the laucher size changes by the settings of compiz config settings manager, but you better wait for another reply about that.

---

### Post by Gonzaki on 2012-10-16
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf3] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be2] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]

---

