---
title: "External Monitor on Dell Inspiron"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by pgouellette on 2012-02-12
New user
Installed 11.10 Ubuntu
Dell Inspiron 1000
SIS M650 Video 

I have been trying to get an external monitor working so I can use it as an extended desktop like I do in Windows.
When I first plugged it in it was a mirror image of my laptop screen
I have searched and searched the forums and have tried xrander commands, edited monitor.xml, and created an xorg.conf file.
Currently my exernal monitor is only blank not even a mirror image anymore.

Here is some of the information.
My  xorg.conf file
----------------
 Section "Device"
Identifier	"Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
Driver	 "sis"
BusID	 "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier	"Plug and play"
Option	 "DPMS"
HorizSync	30-69
VertRefresh	50-120
EndSection

Section "Screen"
Identifier	"Default Screen"
Device	 "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
Monitor	 "Plug and play"
DefaultDepth	24
SubSection "Display"
Depth	 24
Modes	 "1280x1024" "1024x768" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier	"Default Layout"
Screen	 "Default Screen"
EndSection

Section "DRI"
Mode	0666
EndSection
--------------
I tried running a xrander command but got an error

xrandr --output LVDS --auto --output VGA --auto --right-of LVDS
$: command not found
--------------
I tried running a gnome command but got an error
pgo@pgo-Inspiron-1000:~$ gnome-display-properties
gnome-display-properties: command not found
----------------
 Output of lspci -v

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 64
	Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-sis
	Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: e4300000-e43fffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
	Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
	Flags: medium devsel
	I/O ports at 8100 [size=32]
	Kernel driver in use: sis96x_smbus
	Kernel modules: i2c-sis96x

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 128, IRQ 16
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 2800 [size=16]
	Kernel driver in use: pata_sis

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
	Subsystem: Dell Device 0195
	Flags: medium devsel, IRQ 18
	I/O ports at 1000 [size=256]
	I/O ports at 2400 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 173, IRQ 18
	I/O ports at 1400 [size=256]
	I/O ports at 2480 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at e4000000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at e4001000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at e4002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 173, IRQ 19
	I/O ports at 1800 [size=256]
	Memory at e4003000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 58000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sis900
	Kernel modules: sis900

00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Dell Device 0195
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at e4004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00001c00-00001cff
	I/O window 1: 00002000-000020ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0195
	Flags: 66MHz, medium devsel, IRQ 7
	BIST result: 00
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e4300000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 9000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: sisfb

02:00.0 Ethernet controller: Atheros Communications Inc. AR5513 802.11abg Wireless NIC (rev 01)
	Subsystem: D-Link System Inc DWL-G650M Super G MIMO Wireless Notebook Adapter
	Flags: bus master, fast Back2Back, medium devsel, latency 128, IRQ 17
	Memory at 54000000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
---------------
Output of xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       85.0*    75.0     70.0     60.0     87.0  
   800x600       120.0    100.0     85.0     75.0     72.0     60.0     56.0  
   640x480       120.0    100.0     85.0     75.0     73.0     60.0  
   1024x576       87.0     75.0     60.0  
   960x600        60.0  
   960x540        60.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0     76.0  
   848x480        60.0     76.0  
   800x480        85.0     75.0     60.0  
   720x480        61.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  
----------------
Output of sudo lshw -C display; cat /etc/lsb-release
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:e4300000-e431ffff ioport:9000(size=128)
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
---------------------
Output of lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter



Please advise how I can get this working.

Thanks
Paul

---

### Post by dave0109 on 2012-02-13
I had similar problems on my Dell Latitude.  I think it was because of the graphics requirements demanded by Unity (at least on 11.04).

I managed to resolve it by logging in to basic Gnome 2 mode, without effects.  This allowed me to drive the other monitor and from that point I could login using Gnome 2 with effects.

Since 11.10, I've switched to Xubuntu, so not sure whether it would work for you if you logged in using Unity 2D to set stuff up.

---

