---
title: "Mint - Belkin Wireless G Network Card Installation"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by ShooterKI on 2008-10-07
I am a complete nub when it comes to linux. I have spent very little time with it and am in need of assistance. I have purchased a Belkin Wireless G Network Card and need help installing it.

---

### Post by talsemgeest on 2008-10-07
Ok, I had a problem like this a little while ago. I am guessing that you are using linux mint. Try installing it WITH a wired connection. That worked for me.

---

### Post by ShooterKI on 2008-10-07
what do you mean by install it with a wired connection? like what commands and such? im really at a lost for knoledge.

---

### Post by spiderbatdad on 2008-10-07
```
dmesg | tail
```

```
lspci
```
```
lspcmcia
```
```
pccardctl status
```

Possible fixes:```
sudo modprobe pcmcia && sudo modprobe pcmcia_core
```reboot

---

### Post by talsemgeest on 2008-10-07
Sorry, I was in a rush so I didn't explain it properly. Actually, probably best to just go with spiderbatdads suggestion.

---

### Post by ShooterKI on 2008-10-08
ok so i did what he you said spider and um how do i know if it did anything. i cant seem to see any difference.

---

### Post by ShooterKI on 2008-10-08
this is what it said when i entered lspci
-------------------------
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. Unknown device 001d (rev 01)
--------------------------------------
and it didnt do anything that i can tell when i input the modprobe line

---

