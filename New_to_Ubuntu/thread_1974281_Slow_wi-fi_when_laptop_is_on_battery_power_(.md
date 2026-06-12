---
title: "Slow wi-fi when laptop is on battery power :("
date: 2012-05-05
forum: New to Ubuntu
---

### Post by steviematt on 2012-05-05
When a laptop is running from a battery in windows many power saving schemes come on. One of these slows your wi-fi down to a crawl, but you can configure these power saving settings somewhere within the control panel.

I'm new to Ubuntu and don't know how to configure these settings, i know there will be something i could bash into the command line, but i don't know what and it's difficult to find the specific commands i need. 

So my question is: **How do i stop Ubuntu slowing down my wi-fi when i run my laptop on battery power?**

My laptop is a Samsung SF310 and i have the proprietary broadcom driver enabled with all updates installed on 12.04LTS 64-bit.

---

### Post by Crafty Kisses on 2012-05-05
Can I get the results of

```
lspci
lspci | grep -i wireless
```

---

### Post by steviematt on 2012-05-06
> **Crafty Kisses said:**
> Can I get the results of

```
lspci
lspci | grep -i wireless
```

```
 steven@Steven:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 3D controller: NVIDIA Corporation GT218 [GeForce 310M] (rev a2)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
 
``````
 steven@Steven:~$ lspci | grep -i wireless
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
 
```

---

