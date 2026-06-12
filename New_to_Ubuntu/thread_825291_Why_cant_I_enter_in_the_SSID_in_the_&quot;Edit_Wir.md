---
title: "Why cant I enter in the SSID in the &quot;Edit Wireless Networks&quot; option?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-06-10
I have a laptop with a card built in for wireless. I dont really know what to do, Oh yeah, in that list box to the left, theres nothing in it.

---

### Post by WinterMadness on 2008-06-10
Dell Wireless 1395 802.11g Mini Card

thats my wireless card, is it compatible?

---

### Post by sam_delta on 2008-06-10
my quick response is, plug your internet cable, then go into system>administration>hardware drivers, and check if theres a broadcom wireless listed, if it is, enable and restart your computer, if its not there

post the output of ```
lspci
```

sam

---

### Post by MockY on 2008-06-10
Sorry if I am interpreting the question wrong, but if it's greyed out, then you should probably authorize (give yourself admin rights) by clicking the appropriate button in the bottom of the window before you can enter anything.

---

### Post by WinterMadness on 2008-06-10
> **sam_delta said:**
> my quick response is, plug your internet cable, then go into system>administration>hardware drivers, and check if theres a broadcom wireless listed, if it is, enable and restart your computer, if its not there

post the output of ```
lspci
```

sam


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

I looked in the driver thing, I only have my video card listed

---

### Post by WinterMadness on 2008-06-10
> **MockY said:**
> Sorry if I am interpreting the question wrong, but if it's greyed out, then you should probably authorize (give yourself admin rights) by clicking the appropriate button in the bottom of the window before you can enter anything.

I dont see anything that allows that, I was actually looking for that but theres no options anyway (that I know of) to give myself admit options

---

### Post by sam_delta on 2008-06-10
id try b43-fwcutter,,, with an internet connection, (wired) open a terminal and type
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when prompt if want to fetch the firmware
restart your computer and check if it now works/or apear under system>admin>hardware drivers

also, making all updates might help b43-fwcutter work better, with a wired connection, go into system>admin>update manager, click on check , then install , itll install all updates

tell us if it works
sam

---

### Post by WinterMadness on 2008-06-11
> **sam_delta said:**
> id try b43-fwcutter,,, with an internet connection, (wired) open a terminal and type
```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```
make sure you answer with 'yes' when prompt if want to fetch the firmware
restart your computer and check if it now works/or apear under system>admin>hardware drivers

also, making all updates might help b43-fwcutter work better, with a wired connection, go into system>admin>update manager, click on check , then install , itll install all updates

tell us if it works
sam

worked! thanks!

---

### Post by sam_delta on 2008-06-11
glad its working
enjoy ubuntu :)
sam

---

