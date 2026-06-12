---
title: "kVM swicht dont work on one of two towers pc, mouse is frozen"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by hectorrr on 2013-06-30
hello, I am new on ubuntu, I got two pcs with ubuntu 12.04 LTS with 64 bits. I got a KVM switch encore for two pcs with usb. When I conmuted from one to another, one works fine and the other just the keybord and the mouse is frozen- dont move at all-.

when a use  lspci  :

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
03:05.0 Ethernet controller: Atheros Communications Inc. AR2417 Wireless Network Adapter [AR5007G 802.11bg] (rev 01)



any idea? thanks

---

### Post by Jonor on 2013-07-01
It may be of use to mention that it is not always necessary to set up the KVM as instructed.
With power hungry wireless keyboards and mice i found that the dedicated keyboard usb 
could be completely ingnored and a powered usb hub put on the other usb and the 
keyboard, mouse and other things put into that.

---

