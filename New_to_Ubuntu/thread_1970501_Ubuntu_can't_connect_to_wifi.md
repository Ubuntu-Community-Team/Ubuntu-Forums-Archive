---
title: "Ubuntu can't connect to wifi"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by iceman1992 on 2012-05-01
I have been using Ubuntu on my laptop for a few years. But honestly I'm still a beginner on the technical side. 
I was running Ubuntu 11.04 and it worked flawlessly. When 11.10 came out, I upgraded it from the update manager, afterwards my laptop isn't able to connect to my home Wifi anymore. 
I tried searching on the forums but didn't find a solution. I tried installing it fresh, with the "erase ubuntu and install...." option and still won't connect, then when 12.04 came out I did a fresh install again. Still no luck. 
Help please? My laptop is Asus K40IN. If I remember correctly it has an Atheros adapter.

---

### Post by ubudog on 2012-05-01
Hi there, could you post the output of: 
```
sudo lspci -v
```

Edit: Also, is there anything in "Additional Drivers"?

---

### Post by iceman1992 on 2012-05-01
> **ubudog said:**
> Hi there, could you post the output of: 
```
sudo lspci -v
```

Edit: Also, is there anything in "Additional Drivers"?

Hi thanks for the very quick response. This is the output

```
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: 66MHz, fast devsel

00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: 66MHz, fast devsel, IRQ 15
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 14
	Memory at fae80000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=00a0
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 16f3
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: [b8] Subsystem: ASUSTeK Computer Inc. Device 1cf7

00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 40
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=16]
	Memory at fae7c000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
	Capabilities: [8c] SATA HBA v1.0
	Capabilities: [b0] MSI: Enable+ Count=1/8 Maskable- 64bit+
	Kernel driver in use: ahci

00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: faf00000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f9ffffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
	Kernel modules: shpchp

00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Capabilities: [48] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Capabilities: [40] Subsystem: ASUSTeK Computer Inc. Device 1cf7
	Capabilities: [48] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Kernel driver in use: pcieport
	Kernel modules: shpchp

02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce G102M] (rev b1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 19b4
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	Expansion ROM at fafe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop
	Flags: bus master, fast devsel, latency 0, IRQ 41
	I/O ports at e800 [size=256]
	Memory at feaff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at feac0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [84] Vendor Specific Information: Len=4c <?>
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [12c] Virtual Channel
	Capabilities: [148] Device Serial Number 02-00-00-00-68-4c-e0-00
	Capabilities: [154] Power Budgeting <?>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AzureWave AW-NE771 802.11bgn Wireless Mini PCIe Card [AR9281]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

And the Additional Drivers only shows the NVIDIA drivers

---

### Post by ubudog on 2012-05-01
Could you post the output of: 
```
ifconfig
```

---

### Post by iceman1992 on 2012-05-01
The output of ifconfig :
```
eth0      Link encap:Ethernet  HWaddr 00:26:18:22:6f:28  
          inet addr:192.168.6.103  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::226:18ff:fe22:6f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3265134 (3.2 MB)  TX bytes:200324 (200.3 KB)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40000 (40.0 KB)  TX bytes:40000 (40.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:23:06:09:1d  
          inet addr:192.168.6.102  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::224:23ff:fe06:91d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70527 (70.5 KB)  TX bytes:39731 (39.7 KB)

```

---

### Post by ubudog on 2012-05-01
Ok, I think we're getting somewhere.  Assuming you have some form of internet access on the box you're trying to fix, open a terminal and do this: 
```
sudo apt-get update
```
Wait for that to finish, then: 
```
sudo apt-get install bcmwl-kernel-source
```
Wait for that to finish.

Then in Additional Drivers, do you see anything new?

---

### Post by ubudog on 2012-05-01
If that doesn't work, [this]("http://ubuntuforums.org/showthread.php?t=1309072") might.

---

### Post by iceman1992 on 2012-05-01
> **ubudog said:**
> Then in Additional Drivers, do you see anything new?
Yes it has an ethernet connection right now. Nothing new, sadly :(
Still only the nvidia drivers there. I forgot to say that it's the 64bit ubuntu.

---

### Post by iceman1992 on 2012-05-01
> **ubudog said:**
> If that doesn't work, [this]("http://ubuntuforums.org/showthread.php?t=1309072") might.
Okay I am trying this one. Thanks :)

---

### Post by ubudog on 2012-05-01
> **iceman1992 said:**
> Okay I am trying this one. Thanks :)

Best of luck!

---

### Post by iceman1992 on 2012-05-01
YEEEEESSSSSS IT RUNS!! :guitar:

A very big thank you!! Finally after more than 6 months without wifi.

A couple of questions about the madwifi installation :
1. On the second step, 
```
sudo apt-get update && sudo apt-get upgrade
```
I saw some errors and failures, something about CD-ROMs or something, will that be a problem?

2. Do I need to install wicd?

---

### Post by ubudog on 2012-05-01
> **iceman1992 said:**
> YEEEEESSSSSS IT RUNS!! :guitar:

A very big thank you!! Finally after more than 6 months without wifi.


Awesome!  Glad you got it working.  :guitar:

> **iceman1992 said:**
> 
I saw some errors and failures, something about CD-ROMs or something, will that be a problem?


It shouldn't be a problem, you could run apt-get update again and see if you still see it.

> **iceman1992 said:**
> 
2. Do I need to install wicd?

Up to you.  If network-manager (the default) is working for you, then I don't see a reason to.

Best wishes,
ubudog

---

### Post by iceman1992 on 2012-05-01
Oh okay then :) 

I think the network manager will do just fine

Once again many thanks to you, ubudog! :D

---

### Post by Dimatchka on 2012-06-13
Hi guys im having an issue with my wifi.. at home it connects perfectly but at school in the library its detecting the network but cant connect to it. It just keeps tying to connect but to no avail. Also it recognizes the ethernet and doesn't want to connect when i plug in the wire. and one last issue is that when i close the lid of my laptop it doesn't suspend.  Wifi issue is the most important for me right now.

---

