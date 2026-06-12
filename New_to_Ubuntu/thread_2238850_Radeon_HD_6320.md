---
title: "Radeon HD 6320"
date: 2014-08-10
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2014-08-10
[COLOR=#000000]I ran "lspci -v" from a terminal and I'm posting the results below. How can I determine what graphics I have and what drivers are best for it. Im into gaming and data collecting and analysis.

[/COLOR]wyatt@wyatt-HP-2000-Notebook-PC:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
	Subsystem: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
	Flags: bus master, 66MHz, medium devsel, latency 32


00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=256]
	Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: radeon


00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 4118 [size=8]
	I/O ports at 4124 [size=4]
	I/O ports at 4110 [size=8]
	I/O ports at 4120 [size=4]
	I/O ports at 4100 [size=16]
	Memory at f0449000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci


00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f0448000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at f0447000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: 66MHz, medium devsel
	Kernel driver in use: piix4_smbus


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64


00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f0446000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0300000-f03fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Prefetchable memory behind bridge: 00000000f0100000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f0200000-f02fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
	Memory at f0445000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
	Memory at f0444000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
	Flags: fast devsel


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
	Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
	Flags: fast devsel


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k10temp


00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
	Flags: fast devsel


00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
	Flags: fast devsel


00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
	Flags: fast devsel


00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
	Flags: fast devsel


02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: rtsx_pci


06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 3577
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 2000 [size=256]
	Memory at f0104000 (64-bit, prefetchable) [size=4K]
	Memory at f0100000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169


07:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2800pci


wyatt@wyatt-HP-2000-Notebook-PC:~$

---

### Post by grahammechanical on 2014-08-10
> [COLOR=#000000]00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])[/COLOR]

[http://www.notebookcheck.net/AMD-Radeon-HD-6320.54746.0.html](http://www.notebookcheck.net/AMD-Radeon-HD-6320.54746.0.html)

[http://www.game-debate.com/hardware/?gid=631&graphics=Radeon%20HD%206320](http://www.game-debate.com/hardware/?gid=631&graphics=Radeon%20HD%206320)

What drivers does Additional drivers offer you?

Regards.

---

### Post by Bashing-om on 2014-08-10
wyattwhiteeagle; Hi Welcome to the forum ;

OK, for graphics you have:
```

0:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])
Subsystem: Hewlett-Packard Company Device 3577
Flags: bus master, fast devsel, latency 0, IRQ 45
Memory at e0000000 (32-bit, prefetchable) [size=256M]
I/O ports at 4000 [size=256]
Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: radeon

```
- Observe how I used "code tags" now is not that much easier to read ?-

The graphics card is an ATI card 
> 
 [AMD/ATI] Wrestler [Radeon HD 6320]
 and
the driver is open source
> 
Kernel driver in use: radeon


Now IF that open source driver - radeon - does not perform to your expectations there is the option to install and try the ATI provided driver(s):
From the "Additional Drivers" utility ( Software Sources, Proprietary drivers option checked, and system fully updated) select the option "Additional Drivers", see what the system can find for you, and install the recommended driver. This option has system support.

Now for those who are knowledgeable about this our operating system by choice there are 2 additional options. These options require that you are subject to manually maintaining them.
There is the bleeding edge experimental PPA;
and also obtaining a driver direct from ATI  .

It is possible that the performance will be better, but may also introduce some compatibility issues. Best done by those who know how to deal with breakage issues - or are willing to invest the time and effort to learn.

[INDENT][INDENT]seek and ye shall find
[INDENT][INDENT][INDENT]ask and it shall be given
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wyattwhiteeagle on 2014-08-10
> **grahammechanical said:**
> [http://www.notebookcheck.net/AMD-Radeon-HD-6320.54746.0.html](http://www.notebookcheck.net/AMD-Radeon-HD-6320.54746.0.html)

[http://www.game-debate.com/hardware/?gid=631&graphics=Radeon%20HD%206320](http://www.game-debate.com/hardware/?gid=631&graphics=Radeon%20HD%206320)

What drivers does Additional drivers offer you?

Regards.




Additional Drivers
-*Advanced Micro Devices, Inc. [AMD/ATI]: Wrestler [Radeon HD 6320]
--This device is using the recommended driver.
---*Using X.Org X server-AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
----Using Video driver for AMD graphics accelerators from fglrx (proprietary)
----Using Video driver for the AMD graphics accelerators from fglrx-updates (proprietary)


No proprietary drivers are in use.

What exactly am I looking for at the 2 links you have provided?

---

### Post by wyattwhiteeagle on 2014-08-10
> **Bashing-om said:**
> wyattwhiteeagle; Hi Welcome to the forum ;

OK, for graphics you have:
```

0:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] (prog-if 00 [VGA controller])
Subsystem: Hewlett-Packard Company Device 3577
Flags: bus master, fast devsel, latency 0, IRQ 45
Memory at e0000000 (32-bit, prefetchable) [size=256M]
I/O ports at 4000 [size=256]
Memory at f0400000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: radeon

```
- Observe how I used "code tags" now is not that much easier to read ?-

The graphics card is an ATI card 
 and
the driver is open source


Now IF that open source driver - radeon - does not perform to your expectations there is the option to install and try the ATI provided driver(s):
From the "Additional Drivers" utility ( Software Sources, Proprietary drivers option checked, and system fully updated) select the option "Additional Drivers", see what the system can find for you, and install the recommended driver. This option has system support.

Now for those who are knowledgeable about this our operating system by choice there are 2 additional options. These options require that you are subject to manually maintaining them.
There is the bleeding edge experimental PPA;
and also obtaining a driver direct from ATI  .

It is possible that the performance will be better, but may also introduce some compatibility issues. Best done by those who know how to deal with breakage issues - or are willing to invest the time and effort to learn.
[INDENT][INDENT]seek and ye shall find[INDENT][INDENT][INDENT]ask and it shall be given
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Code Tags??? What are "code tags"???

Sorry for being ignorant and all as I am new to this ubuntu stuff...I need a Ubuntu 14.04 lts 101 for beginning dummies and an exhaustive glossary for the technical stuff where the definitions are written for the primetime dummy. Again, sorry for being so ignorant.

---

### Post by Bashing-om on 2014-08-10
wyattwhiteeagle; Hey !

Not to know is not a sin .

[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) <-The ubuntu_guide

Read the stickies available in each subforum;
See the link in my sig; ( there is a link for the glossary);
I often use Google for defines:
example " define: AHCI".

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

You are in ubuntu forums, there is no such thing here as a "dumb question" .

[INDENT][INDENT]seek and ye shall find
[INDENT][INDENT][INDENT][INDENT]ask and it shall be given
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mastablasta on 2014-08-11
> **wyattwhiteeagle said:**
> Additional Drivers
-*Advanced Micro Devices, Inc. [AMD/ATI]: Wrestler [Radeon HD 6320]
--This device is using the recommended driver.
---*Using X.Org X server-AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
----Using Video driver for AMD graphics accelerators from fglrx (proprietary)
----Using Video driver for the AMD graphics accelerators from fglrx-updates (proprietary)


No proprietary drivers are in use.

What exactly am I looking for at the 2 links you have provided?


select: ----Using Video driver for AMD graphics accelerators from fglrx (proprietary)

enjoy.


you will need the proprietary driver to play games.

---

