---
title: "No Bluetooth w/ Dell E6400 laptop and Ubuntu"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by w.buffalocloud on 2013-12-21
New to Ubuntu with a "new" used Dell E6400 laptop.

Bluetooth states "no bluetooth adapters found"

Since I saw another poster posting these results I will post mine:

rfkill list
```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
reboot@reboot-Latitude-E6400:~$ 

```

lspci
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] (rev 03)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
```

I am able to access wifi okay.
Was unable to connect on Ubuntu 12.10 so I upgraded to 13.04 but that didn't solve anything.
No other (Windows) system software is installed or available

---

### Post by efflandt on 2013-12-22
What makes you think that your laptop has Bluetooth (did it ever work in Windows?). Just because it has an LED for Bluetooth or a Fn key for it does not mean it has that, unless it was included as an option (your lspci does not show any).

I forget if the old Dell I have is a 6400 or 8600, but it even though it looks like it should have Bluetooth from the LED and key, it does not.

---

### Post by w.buffalocloud on 2013-12-22
Thanks efflandt. The computer is new to me so there is no history of bluetooth either way. No doubt your answer is correct and my laptop, in spite of having an led available to light up, did not come with bluetooth.

If it would have had bluetooth would there have been something in the lspci result that said "bluetooth"? (Just thinking about future people searching for answers like this in the forum.

---

