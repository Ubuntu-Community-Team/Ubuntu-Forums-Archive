---
title: "problem with camera"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by zhanfei on 2014-07-22
I just installed lubuntu 14. 04 LTS. Obviously it works very smooth with my old laptop. But the system seemingly can not see the camera.

The camera is logitech 1.3m webcam just comes together with the screen.

Skype can't detect the cam, neither can guvcview.

Does this mean webcam driver not installed?

---

### Post by sandyd on 2014-07-22
> **zhanfei said:**
> I just installed lubuntu 14. 04 LTS. Obviously it works very smooth with my old laptop. But the system seemingly can not see the camera.

The camera is logitech 1.3m webcam just comes together with the screen.

Skype can't detect the cam, neither can guvcview.

Does this mean webcam driver not installed?

Hi, can you post the output of
```

lspci
```

That will help us identify the device and the driver needed for the device.

---

### Post by zhanfei on 2014-07-22
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:03.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780M [Mobility Radeon HD 3200]
0e:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
10:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
10:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
10:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
10:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
10:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by zhanfei on 2014-07-28
After near one week study, I finally find out I should first turn on the webcam! Was so stupid!

---

### Post by oldrocker99 on 2014-07-28
These things happen; don't feel like an idiot! We all were newbies once!

---

### Post by zhanfei on 2014-07-28
> **oldrocker99 said:**
> These things happen; don't feel like an idiot! We all were newbies once!
Thanks man!

---

