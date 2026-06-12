---
title: "Not recognizing anything plugged in"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by ALUKARDH3LLS1NG on 2012-05-01
Hello community I'm a 2nd time poster here because usually a Google search gets all the answers i need. I have Ubuntu 11.10 installed on my machine and everything works flawlessly (HP Pavillion elite m9715f). 
 
My problem is my wife is used to windows and my labtop is also using a Linux variant, me being smart thought "hey why don't I install windows xp on a micro sd card and dual boot that way" thinking at boot I'd choose my/her destiny. So decided to go about it on my desktop (m9715f). Restart, booted from disk, install windows xp to micro sd card and all went well, untill I rebooted.

First there was no grub so I repaired that, I can get into ubuntu now but the problem is it won't read anything plugged in so no usb, no micro sd, no bluray drive, no external hdd just nothing. I tried a certain command that tells me what is plugged in and it is all detected from what I can tell but not mounted I guess. I need help getting this functionality back and was hoping you Linux gurus can lend me a hand. Please advise what I can try since allot of my important documents are on my external drive.

Please advise what other information you might need and thanks in advance!

edit: lspci output

alukard@m9715f:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 0f)

---

### Post by Dngrsone on 2012-05-01
Is the SD card bootable?  Why not boot straight from the SD card instead of relying on grub?

---

### Post by ALUKARDH3LLS1NG on 2012-05-02
> **Dngrsone said:**
> Is the SD card bootable?  Why not boot straight from the SD card instead of relying on grub?

Sorry I didn't make it clear, Ubuntu is natively installed on my hard drive and the experiment was to install windows on the sd card which didn't work out too well. So every time I boot its from my hard drive and at this point I have no interest in installing windows natively on my computer. 

Booting to a working OS is not a problem it's everything that is connected to it that won't get read and mount. Luckily I still have ethernet working so I can get online. Thanks for the reply let me know what else I can provide to help solve this issue.

---

