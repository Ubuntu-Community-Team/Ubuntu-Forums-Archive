---
title: "sound"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-28
Somehow some process has deleted the /proc/asound/card0 directory and now I have lost sound on my laptop.
Help me.
I was getting sound a little while ago just before i restarted.

---

### Post by gjoellee on 2008-07-28
put this line in to terminal:
> sudo apt-get install alsa

---

### Post by sameer.india on 2008-07-28
It says alsa is installed.
lspci shows the card but the computer is unable to load it on boot

sameer@sameer-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by caljohnsmith on 2008-07-28
You would first need to uninstall ALSA before reinstalling it:
```
sudo apt-get remove alsa-base alsa-utils alsa-oss
sudo apt-get install alsa-base alsa-utils alsa-oss

```

---

### Post by sameer.india on 2008-07-28
All this did was change my default display manager

---

### Post by sameer.india on 2008-07-28
in fact it removed gdm but my sound card is still not being detected.
It worked fine till today morning.
It works fine in windows but ubuntu can't detect it at all.

---

### Post by sameer.india on 2008-07-28
It is an intel hda sound card.
ALC262

---

### Post by sameer.india on 2008-07-28
any ideas??????????

---

### Post by sameer.india on 2008-07-28
i did some update about X.Org server before this happened

---

### Post by sameer.india on 2008-07-28
noone???????????

---

### Post by markbuntu on 2008-07-28
There is some info about your sound card here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

