---
title: "linux help!"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by NOTSTAN on 2008-05-17
Hey everyone!  I just recently installed the newest version of ubuntu and deleted vista(YAY!:mrgreen:).  However I only have a 800X600 max screen resolution and i also have no sound. The thing is though i dont know what the exact hardware on the machine is(i inhereted the machine).  How do i look up my hardware?  


Also are their any beginner walkthrough type things any one can recomend me so i can understand linux more?

---

### Post by teaker1s on 2008-05-17
how about a quick spin in terminal?
click 
applications>accessories>terminal
```
lspci -v
```
post output

---

### Post by drsaamah on 2008-05-17
A fifteen twenty minute google search should find the maximum resolution for your computer provided that you have the model number of the laptop available.  I would start with searching the manufacturers website.
As far as beginner walkthroughs go, I would go to the "Absolute Beginner Talk" portion of this very forum and look through the threads that are titled "HOWTO...".  They helped me out a LOT when I started using linux!  And if all else fails, start a thread with a *specifics* of your problem and you'll be surprised by the amount of help you get.  Good luck!

---

### Post by NOTSTAN on 2008-05-18
Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging

---

### Post by perlluver on 2008-05-18
> **NOTSTAN said:**
> Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging

Run lspci -v in the terminal and post that output.

---

### Post by NOTSTAN on 2008-05-18
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e400 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a38
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at d000 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cc00 [size=8]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a54
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fdbff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 200c
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at fdbe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

---

### Post by perlluver on 2008-05-18
Did you enable the restricted drivers, for your video card?

---

### Post by NOTSTAN on 2008-05-18
no, how exactly do i do that?

---

### Post by perlluver on 2008-05-18
> **NOTSTAN said:**
> no, how exactly do i do that?

Go to system>administration>Hardware Drivers, and click enable on any restricted drivers.

---

### Post by NOTSTAN on 2008-05-18
AWESOME!  That fixes that problem. How do i get my sound working?

---

### Post by perlluver on 2008-05-18
> **NOTSTAN said:**
> AWESOME!  That fixes that problem. How do i get my sound working?

That one I am not sure about, I thought Nvidia things worked pretty well with Linux, never had that problem, but my sound is Realtek or Intel.  Your's looks to be Nvidia High Definition Sound. Try googling that sound card in Ubuntu.

---

### Post by NightwishFan on 2008-05-18
My card is realtek but it shows up as a Nvidia.

About the sound issue make sure you check your alsa-mixer to make sure it is configured correctly.

---

### Post by teaker1s on 2008-05-18
most of the time 
double click sound icon
select file change device (allows for alsa or oss)

when you have selected one then

edit tab >preferences and you can enable switches which give you slider options

---

### Post by NOTSTAN on 2008-05-19
I got it figured out! Thanks everyone for your help!

---

