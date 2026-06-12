---
title: "[SOLVED] No sound and no wireless"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by transi3ntb3ing on 2008-10-11
Ok so i just got a new (old) computer and decided to try ubuntu...but i have two major problems!! 1.) no sound 2.) no wireless internet (wired works though). i know i have a working wireless and sound card because both work in win xp pro (i set my comp up to dual boot that and ubuntu 8.04). i think i found the linux driver for my wireless card, but its a tar.gz file and i have no idea what to do with that. somebody please help!!

---

### Post by Pro-reason on 2008-10-11
For your sound, try [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

For your wireless, try the [Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336").

Files ending in .tar.gz are like .zip files.  They have stuff inside.  You can open them with “file-roller”.

---

### Post by transi3ntb3ing on 2008-10-11
ok so for the sound, i don't know how to find the alsa driver (as instructed in the webpage u gave me). this is the output when i put in lspci -v:

---------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: IBM Thinkpad T40 series
	Flags: bus master, fast devsel, latency 0
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 96
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
	I/O behind bridge: 00004000-00008fff
	Memory behind bridge: c0200000-cfffffff
	Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: IBM ThinkPad
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1860 [size=16]
	Memory at 60000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: IBM ThinkPad
	Flags: medium devsel, IRQ 11
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: IBM ThinkPad T41
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
	Memory at c0000800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
	Subsystem: IBM ThinkPad T41
	Flags: medium devsel, IRQ 11
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA controller])
	Subsystem: IBM Unknown device 0530
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
	Subsystem: IBM ThinkPad T30/T40
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: e8000000-ebfff000 (prefetchable)
	Memory window 1: c4000000-c7fff000
	I/O window 0: 00004000-000040ff
	I/O window 1: 00004400-000044ff
	16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
	Subsystem: IBM ThinkPad T30/T40
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: ec000000-effff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00004800-000048ff
	I/O window 1: 00004c00-00004cff
	16-bit legacy interface ports at 0001

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
	Subsystem: AIRONET Wireless Communications Unknown device 5000
	Flags: bus master, fast devsel, latency 64, IRQ 11
	I/O ports at 8000 [size=256]
	Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
	[virtual] Expansion ROM at c0800000 [disabled] [size=2M]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
	Subsystem: IBM ThinkPad R40
	Flags: bus master, medium devsel, latency 66, IRQ 11
	Memory at c0204000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 8400 [size=64]
	Capabilities: <access denied>
-----------------------------------------------------------------------

looks to me like the soundcard was detected, but as mentioned before i'm a noob so i could be wrong!

---

### Post by Nxion on 2008-10-11
Ok so do you get an error when you try to play a audio file?

As for the wireless, Go to System > Administration > Hardware Drivers. What shows up in there?

Regards,
Beau

---

### Post by Nxion on 2008-10-11
> **transi3ntb3ing said:**
> ok so for the sound, i don't know how to find the alsa driver (as instructed in the webpage u gave me). this is the output when i put in lspci -v:

---------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
    Subsystem: IBM Thinkpad T40 series
    Flags: bus master, fast devsel, latency 0
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 96
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM ThinkPad
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM ThinkPad
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
    Subsystem: IBM ThinkPad
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
    Subsystem: IBM ThinkPad
    Flags: bus master, medium devsel, latency 0, IRQ 11
    Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
    I/O behind bridge: 00004000-00008fff
    Memory behind bridge: c0200000-cfffffff
    Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
    Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
    Subsystem: IBM ThinkPad
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1860 [size=16]
    Memory at 60000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
    Subsystem: IBM ThinkPad
    Flags: medium devsel, IRQ 11
    I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
    Subsystem: IBM ThinkPad T41
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at c0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
    Subsystem: IBM ThinkPad T41
    Flags: medium devsel, IRQ 11
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA controller])
    Subsystem: IBM Unknown device 0530
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 3000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
    Subsystem: IBM ThinkPad T30/T40
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: e8000000-ebfff000 (prefetchable)
    Memory window 1: c4000000-c7fff000
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
    Subsystem: IBM ThinkPad T30/T40
    Flags: bus master, medium devsel, latency 168, IRQ 11
    Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
    Memory window 0: ec000000-effff000 (prefetchable)
    Memory window 1: c8000000-cbfff000
    I/O window 0: 00004800-000048ff
    I/O window 1: 00004c00-00004cff
    16-bit legacy interface ports at 0001

02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
    Subsystem: AIRONET Wireless Communications Unknown device 5000
    Flags: bus master, fast devsel, latency 64, IRQ 11
    I/O ports at 8000 [size=256]
    Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
    Memory at c0400000 (32-bit, non-prefetchable) [size=4M]
    [virtual] Expansion ROM at c0800000 [disabled] [size=2M]
    Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
    Subsystem: IBM ThinkPad R40
    Flags: bus master, medium devsel, latency 66, IRQ 11
    Memory at c0204000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 8400 [size=64]
    Capabilities: <access denied>
-----------------------------------------------------------------------

looks to me like the soundcard was detected, but as mentioned before i'm a noob so i could be wrong!


Where did you get the wireless driver from?

---

### Post by transi3ntb3ing on 2008-10-12
well after doing lspci -v i found the name of my wireless card (cisco airo or something, see above) so i pretty much googled cisco linux driver and downloaded the tar.gz driver from here:

[http://www.cisco.com/en/US/products/hw/wireless/ps4555/products_tech_note09186a00800c6a9c.shtml](http://www.cisco.com/en/US/products/hw/wireless/ps4555/products_tech_note09186a00800c6a9c.shtml)

i tried using the little installation guide they have there but to no avail so i'm pretty lost as to how to get my wireless working.

as for the sound, i don't get any error message when i play audio files, it's just that there is no sound. however when i click on volume control i get the following message:

---------------
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
----------------

as for hardware drivers, it simply says "no proprietary drivers are in use on this system." and the list is also blank.

any help, really any help at all is much appreciated!!

---

### Post by transi3ntb3ing on 2008-10-14
ok guys so i got both sound and wireless working!! i've been scouring these forums every spare moment and i finally got my answer-

In a terminal:
Code:

 gksudo gedit /etc/modprobe.d/blacklist

and add these two lines to the end of the file...
blacklist padlock_aes
blacklist geode_aes

thank you guys for your help anyways 8-)

---

### Post by Nxion on 2008-10-14
> **transi3ntb3ing said:**
> ok guys so i got both sound and wireless working!! i've been scouring these forums every spare moment and i finally got my answer-

In a terminal:
Code:

 gksudo gedit /etc/modprobe.d/blacklist

and add these two lines to the end of the file...
blacklist padlock_aes
blacklist geode_aes

thank you guys for your help anyways 8-)

I'm glad its all working for you. :)

---

