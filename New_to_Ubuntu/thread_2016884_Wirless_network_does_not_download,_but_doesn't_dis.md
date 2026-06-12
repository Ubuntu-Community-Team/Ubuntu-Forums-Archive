---
title: "Wirless network does not download, but doesn't disconnect"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by Subcomfreak on 2012-07-04
The problem is as wierd as it sounds. It connects to the network fine. It downloads fine (up to 300kb/s says the system monitor). But the, all of a sudden it stops downloading. It doesn't disconnect, it just simply doesn't download anything. reconnecting to the network resumes downloading for a little bit, but it is inevitable that it will "freeze" again soon.

lspci displays this:
02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R

in "-v" mode:

02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Flags: bus master, slow devsel, latency 64, IRQ 19
    Memory at f8fe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

Also worth noting that I have an old modem connected as well:

02:09.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
    Subsystem: 3Com Corp, Modem Division Device 00c2
    Flags: medium devsel, IRQ 10
    Memory at f001fc00 (32-bit, prefetchable) [size=64]
    Memory at f0000000 (32-bit, prefetchable) [size=64K]
    Memory at f0010000 (32-bit, prefetchable) [size=32K]
    I/O ports at cc40 [size=64]
    Capabilities: <access denied>

Also, this card is NOT a USB card. It is an actual card that I bought and installed inside of my tower. It did not come with a wireless card (machine is at least 10 years old. Worth noting that unbuntu runs crisper than it's native windows 2000!!!)

I will boot to windows later (or find the box that the card came in :P ) to find out if it is in fact a Ralink card. I have my suspicions that the information is inaccurate, meaning that I *think* my card may be of a differnt brand. I will see later when I have an opportunity to boot to windows (or find that ever illusive box) and tell you what windows 2000 spits out. 

Sorry that I can't get you more information, I'm new to unbuntu so I simply don't know how. And the 4th of July ( a Holiday in America) demands a lot of my attention. Sorry that I can't be more descriptive right now.

---

### Post by GreatDanton on 2012-07-04
Could you please post the output:
```
lspci
```

Thanks

---

### Post by anewguy on 2012-07-04
Your card may have a different brand name - what the list is showing is the actual chipset used on the card.

---

### Post by Subcomfreak on 2012-07-04
lspci:
```
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200] (Secondary) (rev 01)
02:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
02:09.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R
02:0e.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
03:05.0 USB controller: ALi Corporation USB 1.1 Controller (rev 03)
03:05.1 USB controller: ALi Corporation USB 1.1 Controller (rev 03)
03:05.2 USB controller: ALi Corporation USB 1.1 Controller (rev 03)
03:05.3 USB controller: ALi Corporation USB 2.0 Controller (rev 01)
03:0a.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
03:0a.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
```

lspci -v

```
00:00.0 Host bridge: Intel Corporation 82840 840 [Carmel] Chipset Host Bridge (Hub A) (rev 01)
    Subsystem: Dell Device 0096
    Flags: bus master, fast devsel, latency 0
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation 82840 840 [Carmel] Chipset AGP Bridge (rev 01) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fc000000-fdffffff
    Prefetchable memory behind bridge: e0000000-efffffff
    Kernel modules: shpchp

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=64
    I/O behind bridge: 0000c000-0000dfff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: f0000000-f00fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Intel Corporation 82801AA IDE Controller
    Flags: bus master, medium devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 USB controller: Intel Corporation 82801AA USB Controller (rev 02) (prog-if 00 [UHCI])
    Subsystem: Intel Corporation 82801AA USB Controller
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
    Subsystem: Intel Corporation 82801AA SMBus Controller
    Flags: medium devsel, IRQ 10
    I/O ports at bcd0 [size=16]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: Advanced Micro Devices [AMD] nee ATI Device 2002
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at ec00 [size=256]
    Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at fc000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200] (Secondary) (rev 01)
    Subsystem: Advanced Micro Devices [AMD] nee ATI Device 2003
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at fcfe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

02:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
    Subsystem: Dell Device 0096
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at cc80 [size=128]
    Memory at f8fffc00 (32-bit, non-prefetchable) [size=128]
    Expansion ROM at f9000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: 3c59x
    Kernel modules: 3c59x

02:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
    Subsystem: Dell Device 0096
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f8ffe000 (32-bit, non-prefetchable) [size=4K]
    Memory at f8e00000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_cs46xx
    Kernel modules: snd-cs46xx

02:09.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
    Subsystem: 3Com Corp, Modem Division Device 00c2
    Flags: medium devsel, IRQ 10
    Memory at f001fc00 (32-bit, prefetchable) [size=64]
    Memory at f0000000 (32-bit, prefetchable) [size=64K]
    Memory at f0010000 (32-bit, prefetchable) [size=32K]
    I/O ports at cc40 [size=64]
    Capabilities: <access denied>

02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Flags: bus master, slow devsel, latency 64, IRQ 19
    Memory at f8fe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

02:0e.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, medium devsel, latency 64
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
    Capabilities: <access denied>
    Kernel modules: shpchp

03:05.0 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fafff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:05.1 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at faffe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:05.2 USB controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
    Subsystem: ALi Corporation ASRock 939Dual-SATA2 Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at faffd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

03:05.3 USB controller: ALi Corporation USB 2.0 Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: ALi Corporation Device 5272
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at faffcc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

03:0a.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
    Subsystem: Dell Device 0096
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    BIST result: 00
    I/O ports at dc00 [disabled] [size=256]
    Memory at faffb000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at fb000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: aic7xxx
    Kernel modules: aic7xxx

03:0a.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
    Subsystem: Dell Device 0096
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    BIST result: 00
    I/O ports at d800 [disabled] [size=256]
    Memory at faffa000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at f8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: aic7xxx
    Kernel modules: aic7xxx

```

---

### Post by Subcomfreak on 2012-07-05
Did I get the correct info?

Also, I noted that given enough time it will eventually disconnect and automatically reconnect. But the download spped has been at zero for a long time.

---

### Post by Subcomfreak on 2012-07-06
So am I basically stuck with this problem?

---

### Post by Subcomfreak on 2012-07-06
I found that my wireless card does have linux drivers for it:
[http://www.rosewill.com/products/1698/ProductDetail_Download.htm](http://www.rosewill.com/products/1698/ProductDetail_Download.htm)

Being a 100% noob I don't know which one to pick, nor how to install them. Any help in installing this/ getting it to work would be very much appreciated!

I heard that you can some how "wrap" or "convert" a windows driver to linux. If the linux driver is too old (2010 by the looks of it) then maybe we could make use of the windows 7 driver.

I just have this one last kink to work out before I have unbuntu completely "tricked out" for my needs.

---

