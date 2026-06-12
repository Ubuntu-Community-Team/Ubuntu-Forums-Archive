---
title: "More then one screen"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by CommanderOne on 2008-07-25
Hey,

I have gotten another monitor here, and was wondering how to install/use an extended desktop sort of thing with Ubuntu. I know how to do it in windows, but I would love to start using it on Ubuntu as well.

Thanks in advance!

---

### Post by SunnyRabbiera on 2008-07-25
Its possible to do though I am aware its a bit rough, I dont know how it works but I do know its possible.

---

### Post by Dylock on 2008-07-25
What kind of video card do you have?

You can find this with the ```
lshw
``` or ```
lspci
```

If you have a nvidia card you can setup dual monitors with the nvidia-settings program.

---

### Post by CommanderOne on 2008-07-25
> **Dylock said:**
> What kind of video card do you have?

You can find this with the ```
lshw
``` or ```
lspci
```

If you have a nvidia card you can setup dual monitors with the nvidia-settings program.

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Thanks.

---

### Post by Dylock on 2008-07-25
Hmmm integrated video, no PCI, AGP, PCIe card?

---

### Post by CommanderOne on 2008-07-25
> **Dylock said:**
> Hmmm integrated video, no PCI, AGP, PCIe card?

Mostly stock Dell Inspiron Laptop, so I'm not too sure really.

---

### Post by Bionic Apple on 2008-07-25
What is the second screens maximum resolution?  If it is too high, you may need to scale it down due to performance issues.

Anyway, I Googled it and this came up: [Link]("http://ubuntuforums.org/showthread.php?t=221174"). And here is the tutorial for Xinerama: [Link]("http://ubuntuforums.org/showthread.php?p=1773624")

---

### Post by CommanderOne on 2008-07-25
> **Bionic Apple said:**
> What is the second screens maximum resolution?  If it is too high, you may need to scale it down due to performance issues.

It's actually an older CRT monitor xD

So does anyone have any idea how I can do this?

---

