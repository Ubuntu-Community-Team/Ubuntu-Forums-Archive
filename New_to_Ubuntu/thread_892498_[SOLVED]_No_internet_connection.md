---
title: "[SOLVED] No internet connection"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by speedzor on 2008-08-17
hi,

Suddenly, the internet on my laptop with ubuntu 8.04 (Gnome) is gone.
No internetconnection at all available.
When i left-click on the icon in the taskbar, I can only see a (non-clickable) button with wired network on it, and one with Manual configuration.
When clicking on manual, the option for wireless networking dissappeared.

When rightclicking on the icon, I see the option 'Enable networking', but no longer 'wireless networking'.
Though there is still an option to edit the wireless networks.

has anyone got an idea?

---

### Post by speedzor on 2008-08-17
I tried to restart the network service, it didn't work either.
```
sudo /etc/init.d/networking restart
```

---

### Post by phidia on 2008-08-17
Have you accidentally turned off your card? Some wireless cards are controlled by function keys and others have a little switch check how your's is activated and shut off and try that.

---

### Post by speedzor on 2008-08-17
hi,

I tried the following commands:
```
ifconfig -a
```
he only finds a eth0 and lo device.

after that I did ```
iwconfig
```:
lo     no wireless extensions
eth0   no wireless extensions

after that:
```
sudo apt-get install wireless-tools
```
it was alrready updated.

after that:
```
lspci 
```, and it returned the following values:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

I got told he can't find my wlan interface.
how can I make him find it?

---

### Post by speedzor on 2008-08-17
oh ffs.
switch was turned wrong.
even though I turned the internet back now, it still gives a red light, that's why I though it was enabled...
thanks for helping me :p

---

