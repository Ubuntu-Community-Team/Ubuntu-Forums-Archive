---
title: "Bluetooth adapters not found"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by geo5 on 2014-02-23
Hi all.
I have installed Ubuntu 12.04 in dual-boot alongside Windows 8.1 on my HP Envy 15 J-080ez Touchsmart.
I have a problem with the bluetooth adapter, i use a Logitech bluetooth mouse with the internal adapter but now in Ubuntu in the settings of Ubuntu it show me that: "No bluetooth adapters found".
I write in the Terminal *"rfkill list"* but it shows me off only the Wireless adapter.
What do I do to activate the bluetooth adapter?
Thank you for the support and sorry if i make some mistakes but i do not speak english so good.

---

### Post by Vladlenin5000 on 2014-02-23
Hi, welcome!

Just searching I couldn't find any info regarding the Bluetooth hardware included in the HP Envy 15 J-080ez. As such I would like to ask you to run a couple of commands in order to get detailed info about your hardware:
```
sudo lspci
sudo lsusb
```

(Considering it's internal your Bluetooth should show up in the first list but there's also the possibility of it being connect via USB bus - memory card readers and embedded webcams in notebooks are also internal and usually in the USB bus, not PCI)

In your next post please pay attention to the following: Click on "Go Advanced" and in order to post the results click on # and paste inside.

---

### Post by geo5 on 2014-02-24
Hi Vladlenin5000,
Thank you for the replie, I wrote the command in the terminal and that is what it shows me:
```
sudo lspci
```
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
08:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
08:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)

```
And:
```
sudo lsusb
```
```
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 0eef:a103 D-WAV Scientific Co., Ltd 
Bus 003 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```
Thank you!

---

### Post by Vladlenin5000 on 2014-02-24
Here's your Bluetooth (and it's PCI after all):
```
08:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
```

It is a WiFi+Bluetooth integrated solution, apparently. There are proprietary drivers for Linux (and surprisingly for Linux only) at Mediatek's website -> [http://www.mediatek.com/en/downloads/rt3290-pcie/](http://www.mediatek.com/en/downloads/rt3290-pcie/)
But the surprises don't end here, oh no... Even more surprising the RT3290 is an **Ubuntu certified** hardware - [http://www.ubuntu.com/certification/catalog/component/pci/1814%3A3298/](http://www.ubuntu.com/certification/catalog/component/pci/1814%3A3298/) - and it wasn't detected in your installation?!? :confused::confused::confused:

We have a (huge) thread already about it. Read it and good luck (you'll need it): [http://ubuntuforums.org/showthread.php?t=2166311](http://ubuntuforums.org/showthread.php?t=2166311)

---

### Post by geo5 on 2014-02-24
Hi Vladlenin5000,
Thank you so much for your support. 
Now i go to watch the links you wrote.
Thank you!
Bye

---

