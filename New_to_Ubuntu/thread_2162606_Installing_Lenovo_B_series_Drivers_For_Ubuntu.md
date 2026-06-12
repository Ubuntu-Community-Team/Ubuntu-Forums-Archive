---
title: "Installing Lenovo B series Drivers For Ubuntu"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by karanbpathak on 2013-07-15
I have Lenovo B series All in Desktop Computer, and I have installed Ubuntu on my system,I wanted to installed Bluetooth driver on it.I have Bluetooth Option in System Setting,but it shows No Adapter found,When before i had Windows 7 ,i had a lenovo driver CD so my Bluetooth worked.So for now my Bluetooth is not working in ubuntu? please help ?:(

---

### Post by ricardoeureka on 2013-07-15
Could you please provide what is exactly the model of our PC?

What is the output of the following commands?
# sudo dmesg | grep -i blue
# lspci
# lsusb
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by karanbpathak on 2013-07-17
Output of sudo dmesg | grep -i blue 

root@balkrishna-LENOVO:~# sudo dmesg | grep -i blue
[   14.041151] Bluetooth: Core ver 2.16
[   14.041191] Bluetooth: HCI device and connection manager initialized
[   14.041193] Bluetooth: HCI socket layer initialized
[   14.041194] Bluetooth: L2CAP socket layer initialized
[   14.041199] Bluetooth: SCO socket layer initialized
[   14.058319] Bluetooth: RFCOMM TTY layer initialized
[   14.058325] Bluetooth: RFCOMM socket layer initialized
[   14.058327] Bluetooth: RFCOMM ver 1.11
[   14.058687] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.058690] Bluetooth: BNEP filters: protocol multicast

Output of lspci
root@balkrishna-LENOVO:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Lenovo Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3401
04:00.1 Mass storage controller: VIA Technologies, Inc. Device 401a
04:00.2 SD Host controller: VIA Technologies, Inc. Device 401b

Output of lsusb
root@balkrishna-LENOVO:~# lsusb
Bus 001 Device 003: ID 0ac8:c42d Z-Star Microelectronics Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 0461:4d80 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)

---

### Post by ricardoeureka on 2013-07-17
Well, as far as I can see, the bluetooth device is perfectly recognised and discovered by the system/kernel .  Could you copy and paste what does System Settings -> Bluetooth shows to you? (I mean the screenshot)    Which version of Ubuntu have you installed?

---

### Post by karanbpathak on 2013-07-18
Below is the screenshot of System Setting>Bluetooth

---

