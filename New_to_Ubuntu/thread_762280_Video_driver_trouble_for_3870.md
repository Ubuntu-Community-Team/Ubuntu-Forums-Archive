---
title: "Video driver trouble for 3870"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by Shnooky on 2008-04-21
In display manager it says that my onboard nvidia was my primary display but i have a 3870 in the m/o. Also under restricted drive management it shows the integrated not the after market card. 

Can anyone refer me to an installation guide for my graphics card, its a 64 bit.

Advice is appreciated, thx

---

### Post by Shnooky on 2008-04-22
plz reply

---

### Post by subzero316 on 2008-04-22
Installing the nvidia card is very easy. there is a s/w called envy it ll take care and do the installation .Read a bit about it and do the installation. Download it here.  [<---Click---->]("http://linux.softpedia.com/get/System/Software-Distribution/Envy-36960.shtml"). Also i suggest you check if you have plugged the add-on card properly and connect the monitor to it also paste the output of          ' lspci -v '  here

---

### Post by Shnooky on 2008-04-22
I dont want the nvidia drivers becasue that is oboard, the 3870 by ati is what I want and what do I do with "lspci -v"

---

### Post by subzero316 on 2008-04-22
IN the terminal window(find it in the applications menu on top Terminal) type lspci-v  in the  prompt

---

### Post by Shnooky on 2008-04-22
This is what I got using that text

shnooky@shnooky:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: fd800000-fd8fffff
        Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2) (prog-if 00 [VGA])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        [virtual] Expansion ROM at 98000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f400 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at e000 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at cc00 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fdc00000-fdcfffff
        Prefetchable memory behind bridge: fdb00000-fdbfffff
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
        Subsystem: Foxconn International, Inc. Unknown device 0d00
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c800 [size=8]
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

03:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501 (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 2542
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=256]
        [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.1 Audio device: ATI Technologies Inc Unknown device aa18
        Subsystem: ATI Technologies Inc Unknown device aa18
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

04:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 9c00 [size=32]
        Capabilities: <access denied>

it shows that the ATI device is unidenified

---

### Post by subzero316 on 2008-04-22
Good, See  the monitor is connected to ati card n itz displaying trou it jus that a generic driver is utilized due to unavalibilty of ati driver .Download that Envy (link i posted b4) it ll do the installtion for your ati card. youll get an option for it.

---

### Post by subzero316 on 2008-04-22
Also ensure that you do it in the terminal. Cause The gui did not get the drivers intalled for me. Follow the steps below . I suggest you browse a bit about envy text-manual installation.
Enter the following commands:
> 
Press ctrl+alt+F1
$sudo /etc/init.d/gdm stop
$envy -t

from there on ull get it

---

### Post by Shnooky on 2008-04-22
thank you for the info

---

