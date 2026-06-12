---
title: "no sound after wow and vlc at the same time"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Bentenrai on 2008-10-01
I just had wine running world of warcraft and vlc media player playing the office at the same time. i was only pdating a fresh wow install so i figured id watch something. then i lost sound and now i have no sound whatsoever. i rebooted once and it came back but then quit again. now it won't come back..

an ideas?

---

### Post by Crafty Kisses on 2008-10-01
What are the results of this command?
```
lspci
```

---

### Post by Bentenrai on 2008-10-01
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)


That's it.

---

### Post by Bentenrai on 2008-10-01
bump...

 please help!!!

---

### Post by Bentenrai on 2008-10-01
Fixed it... Downloaded also mixer.

---

### Post by Crafty Kisses on 2008-10-01
I was about to suggest that, alright then please mark the thread solved. :D

---

