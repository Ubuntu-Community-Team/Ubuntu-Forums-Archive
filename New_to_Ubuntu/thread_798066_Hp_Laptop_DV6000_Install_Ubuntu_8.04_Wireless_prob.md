---
title: "Hp Laptop DV6000 Install Ubuntu 8.04 Wireless problem"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Habaneroman on 2008-05-17
Ihave a Hp Laptop, and can not fiqure out how to set up the ubuntu wireless, I am dual booting with windows vista (Caution-I may need step by step help)

---

### Post by sam_delta on 2008-05-17
can you post the output of the command
```
lspci
```
so we can know your wireless card model

thx, sam

---

### Post by Habaneroman on 2008-05-17
Yea Be right back!

---

### Post by Habaneroman on 2008-05-17
f

---

### Post by Habaneroman on 2008-05-17
habaneroman@habaneroman-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
habaneroman@habaneroman-laptop:~$

---

### Post by Ayuthia on 2008-05-17
> **Habaneroman said:**
> 
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

This is your wireless card.  If you have a working internet connection in Ubuntu, you can enable it by going to System->Administration->Hardware Drivers and check the box for the Broadcom card.

---

### Post by sam_delta on 2008-05-17
first of all, try checking into hardware drivers, go into system>administration>hardware drivers,, and check if theres a wireless drivers listed, if they are, just click to enable them, if there is nothing listed, proceed with installing b43-fwcutter

plug a wired connection into your ubuntu machine, and try installing b43-fwcutter drivers for your wireless card, you can do this, by going into the terminal (aplications>accessories>terminal) and typing the following command
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
It will ask if you want to fetch a firmware, make sure you answer with YES.
restart pc, and check if it works/appear under system>administration>hardware drivers

if it dosnt work, report back here, ill give you instructions on how to install ndiswrapper

sam

---

### Post by Habaneroman on 2008-05-17
ok

---

### Post by Habaneroman on 2008-05-17
You made my weekend!! Thanks Sam

---

### Post by sam_delta on 2008-05-17
no problem, im glad i could help
enjoy ubuntu!!!!!!

sam

---

