---
title: "Old PC with ATI Radeon 9200 SE"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by NeverUsedItBefore on 2011-10-02
Hi,
I have an old PC (with old architecture, meaning new graphics cards are not compatible with it) , circa 10 years old, apparently it has an ATI Radeon 9200 SE graphics card.
I am having problems with sound:
 - The 'Front Left' speaker appears to be working OK.
 - The 'Front Right' speaker appears not to work.

I've seem on other (rather old, e.g. 2007) posts that my graphics card is supported for using the non-proprietary drivers.
Additional, the screen itself works OK, and in the past I played a game or two, and the graphics in the game seemed to be OK.
Finally, plugging e.g some headphones into the socket in the front of the computer, left and right seem to work OK, and I'm pretty sure the same would be the case with the speakers.
The speakers or like, one has controls on it such as on/off volume, pretty sure it's got some kind of amplifier in there as well. The left one is very light and is sort of run of a wire from the right hand one.

When installing the latest update (I'm on Natty), I did vaguely see something about obsolete drivers being removed? To be honest, I'm not sure it's ever worked tho, it's probable I just didn't notice !

It's not a massive deal, but it would be nice if both speakers worked - any ideas?

I did find some commands like this. Mostly the output is nonsense to me tbh!
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
***********

lspci -v
***************************
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: e8000000-e9ffffff
    Prefetchable memory behind bridge: d8000000-e7ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:0d.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 03) (prog-if 00 [Generic])
    Subsystem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem
    Flags: bus master, stepping, medium devsel, latency 32, IRQ 17
    Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Giga-byte Technology GA-7VM400AM(F) Motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 20
    I/O ports at b400 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at bc00 [size=8]
    I/O ports at c000 [size=4]
    I/O ports at c400 [size=16]
    I/O ports at c800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at cc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology GA-7VAX Mainboard
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at ea001000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: Giga-byte Technology GA-7VT600 Motherboard
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
    Flags: medium devsel, IRQ 22
    I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at e800 [size=256]
    Memory at ea002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology GA-7VT600-1394 Motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at ea003000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited Device 7ca6
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at d8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at a000 [size=256]
    Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
    Subsystem: PC Partner Limited Device 7ca7
    Flags: bus master, 66MHz, medium devsel, latency 32
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at e9010000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
******************

---

### Post by atomizer on 2011-10-02
First of all: your audio output has nothing to do with your video drivers.
You use the VIA 82xx Audio driver for your audio.

I think it is a broken cable, because the headphones work. Try your speakers on your phone or mp3player to see if the problem still exists.

---

### Post by NeverUsedItBefore on 2011-10-02
It seems you have a point:
 - Plugged into the same socket some different speakers, test left and right and it works OK.
Gonna have a look at the cable etc.

---

### Post by NeverUsedItBefore on 2011-10-02
Thread solved. New speakers are required.

---

