---
title: "xubuntu 12.04 will not wol"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by klein de usa on 2013-04-11
i have a computer that has ubuntu 10.04 installed on it and i installed xubuntu 12.04 on it as well as a dule boot system. when trying to set up wol, sudo ethtool eth0 tells me it is wol ready: 

```
klein@lg1:~/Desktop$ sudo ethtool eth0
[sudo] password for klein: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```

but it will not wol, if ubuntu 10.04 is the last os that was used and shut down wol works fine. but if you boot into xubuntu 12.04 and shut down you can't restart the computer through wol. 
 i even tryed creating the wol script in /etc/init.d/ and xubuntu 12.04 still doesn't wol.
am i missing something ????

---

### Post by Toz on 2013-04-12
Make sure that acpi is also configured to allow wakeups from the network card. You can display whats enabled for wakeups via:
```
cat /proc/acpi/wakeup
```
...and
```
lspci | grep -i network
```
...will show you the PCI addresses so that you can match them up.

If it is not enabled, you can enable it via:
```
echo DEVICE | sudo tee /proc/acpi/wakeup
```
...where DEVICE is the actual name of the device.

---

### Post by klein de usa on 2013-04-12
Toz you helped me out sum some of the commands didn't work like tee, but this is what i found i did the commands in ubuntu 10.04 and xubuntu 12.04 witch are install on the same computer:

 ubuntu 10.04 64bit witch will wol:
```
klein@lg1:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P1	  S3	 disabled  pci:0000:00:01.0
PS2K	  S3	 disabled  pnp:00:04
PS2M	  S3	 disabled  pnp:00:05
UAR1	  S4	 disabled  pnp:00:07
P0P2	  S4	 disabled  pci:0000:00:1e.0
USB0	  S3	 disabled  pci:0000:00:1d.0
USB1	  S3	 disabled  pci:0000:00:1d.1
USB2	  S3	 disabled  pci:0000:00:1d.2
USB3	  S3	 disabled  pci:0000:00:1d.3
EUSB	  S3	 disabled  pci:0000:00:1d.7
MC97	  S4	 disabled  
PEX0	  S4	 disabled  pci:0000:00:1c.0
PEX1	  S4	 disabled  pci:0000:00:1c.1
PEX2	  S4	 disabled  
PEX3	  S4	 disabled  
SLPB	  S4	*enabled   
PWRB	  S4	*enabled
   
klein@lg1:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
klein@lg1:~$ 
```


 xubuntu 12.04 64bit witch will not wol:
```
klein@lg1:~/Desktop$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
P0P1	  S3	*disabled  pci:0000:00:01.0
PS2K	  S3	*enabled   pnp:00:04
PS2M	  S3	*disabled  pnp:00:05
UAR1	  S4	*disabled  pnp:00:07
P0P2	  S4	*disabled  pci:0000:00:1e.0
USB0	  S3	*enabled   pci:0000:00:1d.0
USB1	  S3	*enabled   pci:0000:00:1d.1
USB2	  S3	*enabled   pci:0000:00:1d.2
USB3	  S3	*enabled   pci:0000:00:1d.3
EUSB	  S3	*enabled   pci:0000:00:1d.7
MC97	  S4	*disabled  
PEX0	  S4	*disabled  pci:0000:00:1c.0
PEX1	  S4	*disabled  pci:0000:00:1c.1
PEX2	  S4	*disabled  
PEX3	  S4	*disabled  
SLPB	  S4	*enabled   
PWRB	  S4	*enabled 
  
klein@lg1:~/Desktop$ lspci 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

also on the xubuntu 12.04 computer i did:
```
klein@lg1:~/Desktop$ hwinfo

28: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.86TQ5HioEd4
  Parent ID: qTvu.TCusF8v8hPE
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0xd608 
  Revision: 0x01
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xe000-0xefff (rw)
  Memory Range: 0xff820000-0xff820fff (rw,non-prefetchable)
  Memory Range: 0xff800000-0xff81ffff (ro,non-prefetchable,disabled)
  IRQ: 43 (2715 events)
  HW Address: 00:1c:c0:43:38:76
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00008086sd0000D608bc02sc00i00"
  Driver Info #0:
```


so after compairing the two and hwinfo :
this is the ethnet controler 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
in hwinfo :
i'm not sure witch it the pci i'm looking for:
 SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
 SysFS BusID: 0000:03:00.0
one looks to be a shorter version of the other and in cat /proc/acpi/wakeup i have this line :
PEX1	  S4	*disabled  pci:0000:00:1c.1

it just seems to be this should work in 12.04 if it works in 10.04, does anyone have any other ideas?

---

