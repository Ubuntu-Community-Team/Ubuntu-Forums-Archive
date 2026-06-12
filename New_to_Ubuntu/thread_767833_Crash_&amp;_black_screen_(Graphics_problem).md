---
title: "Crash &amp; black screen (Graphics problem?)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Theo148 on 2008-04-25
I've just done a clean install of Hardy, and everything's working fine with the exception of one issue: I've had my system crash on me three times now. Two of the times were when I was logging out, and the other time I was opening a .wmv file in Totem.

In all three occurrences, my screen suddenly turned black and the computer stopped processing (although it was still on). Ctrl+Alt+Backspace did not work, and neither did the power button, so I had to turn off the power to get it to shut down. On the next boot, the Ubuntu jammed halfway through the initial loading (when it shows the boot splash) and I had to turn off the power again. It only started up properly on the successive reboot.

I'm not sure what the problem is, but it seems graphics related to me (I have an old Intel integrated graphics chipset that hasn't given me any trouble so far). Does anybody know how to resolve this?

---

### Post by Theo148 on 2008-04-25
Well I just got another crash (same symptoms) but I thought this might be helpful: this time I tried booting in recovery mode first, and halfway through a dialog came up and asked if I wanted to try and repair X-server. Does this narrow anything down?

---

### Post by alienexplorers on 2008-04-26
What video card are you using.  Please run the following command and list the output:
> lspci -v

---

### Post by Theo148 on 2008-04-26
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at b0000000 (32-bit, prefetchable) [size=128M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e000 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, fast devsel, latency 0
	Memory at 20000000 (32-bit, prefetchable) [size=128M]
	Memory at 28000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1600 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1700 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at f0080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=32
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: e0000000-efffffff
	Prefetchable memory behind bridge: a0000000-afffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1100 [size=16]
	Memory at 28080000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: medium devsel, IRQ 255
	I/O ports at 1400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Unknown device 0021
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at e100 [size=256]
	I/O ports at e200 [size=64]
	Memory at f0080400 (32-bit, non-prefetchable) [size=512]
	Memory at f0080600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: medium devsel, IRQ 10
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Capabilities: <access denied>

01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, stepping, medium devsel, latency 128, IRQ 10
	Memory at e0001800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at c100 [size=128]
	Capabilities: <access denied>

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 128, IRQ 10
	I/O ports at c000 [size=256]
	Memory at e0001000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation MIM2000/Centrino
	Flags: bus master, medium devsel, latency 128, IRQ 10
	Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 003d
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: a0000000-a3fff000 (prefetchable)
	Memory window 1: e4000000-e7fff000
	I/O window 0: 0000c400-0000c4ff
	I/O window 1: 0000c800-0000c8ff
	16-bit legacy interface ports at 0001
```

---

### Post by Theo148 on 2008-04-26
It doesn't seem like anybody has any ideas for this...

I'm going to try reproducing this by running the shutdown command in terminal so that I can get some error code.

---

### Post by Theo148 on 2008-04-26
Okay, I am now totally stumped as to how to solve this. Help would really be appreciated.

---

### Post by Theo148 on 2008-04-26
Okay, I have a bit more info on the issue that might help. When I boot in recovery mode and run xfix, everything works fine (playing videos, shutting down). However, after the next reboot the problem turns up again, so I suspect that there is some sort of configuration causing xserver to crash. Beyond that, I have no idea. :(

---

### Post by Celauran on 2008-04-26
I am having what appears to be the same problem. I haven't tried any .wmv files yet, but attempting to switch users, restart, or shutdown all fail to a black screen. Laptop stays powered on but there is no display; first happened when rebooting after the initial install.

Don't know if it's a graphics problem or not, but here are the results of ```
lspci -v
```

```

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device 0033
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Toshiba America Info Systems Unknown device 0033
	Flags: bus master, fast devsel, latency 0
	Memory at 20000000 (32-bit, prefetchable) [size=128M]
	Memory at 28000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 18c0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 18e0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at 28080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: cff00000-cfffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 28080400 (32-bit, non-prefetchable) [size=1K]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device 0412
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1000 [size=256]
	I/O ports at 1880 [size=64]
	Memory at 28080800 (32-bit, non-prefetchable) [size=512]
	Memory at 28080a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: medium devsel, IRQ 11
	I/O ports at 1400 [size=256]
	I/O ports at 1800 [size=128]
	Capabilities: <access denied>

01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2741
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cff05000 (32-bit, non-prefetchable) [size=2K]
	Memory at cff00000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at cf00 [size=64]
	Capabilities: <access denied>

01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
	Memory at cff04000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=0
	Memory window 0: 2c000000-2ffff000 (prefetchable)
	Memory window 1: 30000000-33fff000
	I/O window 0: 0000c000-0000c0ff
	I/O window 1: 0000c400-0000c4ff
	16-bit legacy interface ports at 0001

```

You'll notice the graphics controller is the same.

EDIT: Re-reading the initial post, I haven't had the problems on boot. Booting has always been fine, this problem (for me, at least) is limited to shutdowns.

---

### Post by Ombatay on 2008-04-26
I too am having essentially the same problem. Also running an intel 855 graphics processor. I have not had any problems on shutdown or restart, however, only in playing DivX (.avi) files or even DVD files with totem.

I've found this seems to happen at random.
-On initially loading the video file
-On reopening a minimized totem window
-On skipping ahead in the file once playing.

All of these seem to be sporadic at best. Luckily, they're happening at a less than 25% frequency per the initiating event, but as its a total loss of what I was doing, still frustrating none the less.

Any thoughts on what could be causing this would be much appreciated.

It seems that since x 7.3 theres been something different in the i810 driver. I know theres a lot of complaints about slow slow performance from some, and changing XAA vs EXA settings, but as I don't quite know what these affect, I don't quite know what to do with that.

---

### Post by Ombatay on 2008-04-26
Quick update: I experienced the same problem with totem when I tried to use it to play an MP3. Quick black screen and the machine is dead, can't do a thing without a hard reset. A problem with my video drivers made sense before... 

Maybe it still does. I didn't explicitely turn off the visualizer, and I assume its on by default. First time I tried to play music since I installed Hardy (fresh). This ran perfectly with Gutsy.

---

### Post by Theo148 on 2008-04-27
This isn't a 100% occurence for me either, but it still happens and it tends to get rather irritating after a while...

I did hear on another thread that this problem could be solved by disabling desktop effects, but I've yet to try it myself.

---

### Post by Quicky on 2008-04-27
Same problem for me, with Intel graphics. Disabling desktop effects eliminated any crashes I had when playing video, but restarting X with ctrl-alt-backspace produces the unresponsive black screen (of death?) every single time. Never happened in Dapper.

---

### Post by Theo148 on 2008-04-27
I've tried disabling desktop effects - it seems to deal with the video problems for me as well, but I'm still getting the same problems on shutdown/logout.

---

### Post by Arthur Archnix on 2008-04-28
I am not using desktop effects and have irregular irrecoverable crashes when opening a file with totem. I'm not sure what the problem is, but I'm going to remove totem and install mplayer.

---

### Post by Theo148 on 2008-04-28
Okay, scratch my previous post, my system still crashes when opening videos whether desktop effects are enabled or not.

I think this should probably be filed as a bug on launchpad, but I'm new to this and as such have no idea of the proper procedure for bug filing...

---

### Post by twrock on 2008-04-28
Well, if the output of "lspci -v" is any indication, it does seem the graphics are a probable commonality. Here's mine:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
	Memory behind bridge: e0200000-e02fffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Memory at 60000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Dell Inspiron 700m/710m
	Flags: medium devsel, IRQ 10
	I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Inspiron 700m/710m [SigmaTel STAC9750,51]
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Conexant D480 MDC V.9x Modem
	Flags: medium devsel, IRQ 10
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Unknown device 2565
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0206000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0209000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 64000000-67fff000 (prefetchable)
	Memory window 1: 68000000-6bfff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00002800-000028ff
	16-bit legacy interface ports at 0001

02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e020a000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 6c000000-6ffff000 (prefetchable)
	Memory window 1: 70000000-73fff000
	I/O window 0: 00002c00-00002cff
	I/O window 1: 00003000-000030ff
	16-bit legacy interface ports at 0001

02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI])
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0208000 (32-bit, non-prefetchable) [size=2K]
	Memory at e0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e0207000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 700m/710m
	Flags: bus master, fast devsel, latency 32, IRQ 10
	Memory at e0204000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

```
So if someone knows how to properly file a bug, I'd be appreciative.

I haven't done enough boot/shutdown/reboot/anything yet with Hardy, so I can't be overly sure that shutting off desktop effects really did solve my problem or not. If I can come up with any pattern, I'll report back.

---

### Post by Theo148 on 2008-04-28
Yeah, it seems this is almost certainly associated with the Intel Corporation 82852/855GM graphics chipset and a change to the drivers used by xorg. I found a [wiki page]("https://help.ubuntu.com/community/DebuggingXAutoconfiguration") on filing bug reports for xorg, but I don't have the time to go through it at the moment (and I'd probably mess something up anyway).

---

### Post by Arthur Archnix on 2008-04-28
> **Theo148 said:**
> Yeah, it seems this is almost certainly associated with the Intel Corporation 82852/855GM graphics chipset and a change to the drivers used by xorg. I found a [wiki page]("https://help.ubuntu.com/community/DebuggingXAutoconfiguration") on filing bug reports for xorg, but I don't have the time to go through it at the moment (and I'd probably mess something up anyway).

I have an intel 955 and similar problem. Install mplayer or vlc to see if the problem disappears.

---

### Post by Bothered on 2008-04-28
I'm having similar symptoms after a clean hardy install: crash with black screen on log out, and no response to cntrl+alt+backspace or cntl+alt+any function key. I'm using the fglx driver, and had no similar issues with previous ubuntu installs.

---

### Post by coreyinprogress on 2008-04-28
OK everybody, so I was running into this as well, the same problem everybody else has been describing.  I think it has something to do with the restricted drivers.  I did

sudo apt-get install ubuntu-restricted-extras

and everything has worked.  I've just played videos with vlc, mplayer, and gxine and they all worked fine.

I'd like to say that in this instance, Ubuntu just kept me from getting laid.  Perhaps the feeling of triumph is better?  No, I dont think so.

---

### Post by spiderbatdad on 2008-04-28
Theo148, if your problem persists, could you please  upload the output of dmesg (run in a terminal) as a zip file?

---

### Post by Theo148 on 2008-04-29
> **coreyinprogress said:**
> OK everybody, so I was running into this as well, the same problem everybody else has been describing.  I think it has something to do with the restricted drivers.  I did

sudo apt-get install ubuntu-restricted-extras

and everything has worked.  I've just played videos with vlc, mplayer, and gxine and they all worked fine.

Installing the restricted extras package was one of the first things I did after the clean install. Just in case, I've tried reinstalling the restricted extras package, but it doesn't seem to have worked (I still get the problem on shutdown, haven't tried playing videos yet).

> **spiderbatdad said:**
> Theo148, if your problem persists, could you please  upload the output of dmesg (run in a terminal) as a zip file?

You can just call me Theo. :P

The file is attached.

---

### Post by Celauran on 2008-04-29
I have attached the same in case it will be of further help.

By the by, disabling visual effects did drastically reduce the frequency with which this happens, though it has not completely eliminated it.

---

### Post by Arthur Archnix on 2008-04-29
Just out of curiosity, have you guys tried installing VLC or Mplayer and trying to recreate the problem with those programs?

I haven't been able to recreate it since uninstalling totem. I'm using metacity with compositing enabled.

---

### Post by coreyinprogress on 2008-04-29
> **Arthur Archnix said:**
> Just out of curiosity, have you guys tried installing VLC or Mplayer and trying to recreate the problem with those programs?

I haven't been able to recreate it since uninstalling totem. I'm using metacity with compositing enabled.

Yeah - It was happening to me with both VLC, Mplayer, and Totem.  Since I reinstalled the restricted drivers I haven't been having the video problem anymore.

@ Theo, yeah, I didn't realize when I posted but apparently I'm still having the restart problem.  I find that if I boot into a slightly older version of the generic kernel it doesnt get stuck on a reboot.  Still, thats not exactly an ootb solution now is it?

---

### Post by Arthur Archnix on 2008-04-29
> **coreyinprogress said:**
> Yeah - It was happening to me with both VLC, Mplayer, and Totem.  Since I reinstalled the restricted drivers I haven't been having the video problem anymore.?

Nevermind. Just had the xserver crash while using vlc.

---

### Post by Celauran on 2008-04-29
I haven't looked at any video on the laptop that's giving me problems, so while video may indeed cause crashes, it seems unlikely to be the source IMO.

---

### Post by free2useemail on 2008-04-29
Make sure you have all the latest drivers. Go to and upgrade linux. In windows vista, my PC crashed with graphics, same for linux. ALSO! make sure you know what you PC is capable with. Lets say for example, if you have 68mb of graphic memory, you CAN NOT run the effects, so don't even try! it will crash your PC. Just make sure you know what you can and can't do with graphics.

---

### Post by spiderbatdad on 2008-04-29
Theo148, this is from your dmesg:  Local APIC disabled by BIOS -- you can enable it with "lapic"

This is a suggestion to edit the kernel line in /boot/grub/menu.lst to remove --quiet splash and add lapic.

Also:  PCI: Using ACPI for IRQ routing
[    8.724041] PCI: If a device doesn't work, try "pci=routeirq".

this is what my kernel line looks like:```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
``` You can see I have highlighted where I added lapic pci=routeirq to the end of the line beginning with the word kernel. I would then reboot and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then reboot again. Finally on that last reboot, I would press 'e' at the grub menu, then use the arrow key to move to the kernel line...the 'e' again to edit that line. I move to the end (after pci=routeirq) i add a space and the word "profile" So it looks like this:```
kernel/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq **profile**
``` Then hit the enter key and 'b' to boot. This does a one-time profile of the boot...it takes a few seconds longer on this boot, but subsequent boots should be faster. Dont edit /boot/grub/menu.lst to include the word profile, or it will try to profile every time you boot.
Hope this makes sense. Hope it helps.

---

### Post by spiderbatdad on 2008-04-29
Celauran: see the same issue with local apic in your dmesg...do not see any fatal interupts, so perhaps pci=routeirq is unnecessary. You might want to try lapic as described in the above  post. You may want to add pci=routeirq if lapic alone gives no results.

---

### Post by njee on 2008-04-29
I have the same problem as you both and have been playing around with some of the solutions mentioned here. The restricted-extras didn't do anything but removing desktop effects got videos to play.

It definitely seems to be something to do with video though - I only just noticed the problem because I usually have my laptop plugged into an external monitor running at 1280x1024. If I plug in my laptop to the monitor videos will play fine on both the external monitor and the LCD (the output is cloned). However if I restart the computer and unplug the monitor the same video won't play on just the LCD. I was thinking of experimenting with the old i810 driver (on gutsy I had to revert) but the way the new xorg.conf is configured I can't figure out how to do this. Any ideas?

---

### Post by Theo148 on 2008-04-30
> **free2useemail said:**
> make sure you know what you PC is capable with. Lets say for example, if you have 68mb of graphic memory, you CAN NOT run the effects, so don't even try! it will crash your PC. Just make sure you know what you can and can't do with graphics.

My computer is easily capable of running desktop effects (despite its age). It meets the requirements, and the effects ran flawlessly on Gutsy. I've also mentioned that turning off desktop effects did not fix the problem I was having.

@spiderbatdad: Thanks for the suggestions - I'll try it immediately and see if it fixes my boot problem. :) (Am I correct in assuming that it's just a fix for the startup?)

---

### Post by Celauran on 2008-04-30
> **spiderbatdad said:**
> Celauran: see the same issue with local apic in your dmesg...do not see any fatal interupts, so perhaps pci=routeirq is unnecessary. You might want to try lapic as described in the above  post. You may want to add pci=routeirq if lapic alone gives no results.
Thanks, I'll give that a try. Since I'm not real familiar on what that does, do I simply make the changes to menu.lst or do I continue on with dpkg-reconfigure etc and merely omit the pci=routeirq bit?

---

### Post by Arthur Archnix on 2008-04-30
> **Celauran said:**
> Thanks, I'll give that a try. Since I'm not real familiar on what that does, do I simply make the changes to menu.lst or do I continue on with dpkg-reconfigure etc and merely omit the pci=routeirq bit?

Don't make any changes to your menu.lst without testing it first. Instead, call up the grub boot menu (if you've chosen to hide it), select your normal hardy, and press 'E'. Then go to the kernel line, go to the end, and add the pci option. Then press 'Enter' to commit the change, and then 'B' to boot with this new option. If it works then you can add it permanently to menu.lst.

---

### Post by Theo148 on 2008-04-30
Well after testing multiple times my startup problem seems to have vanished for good - I'm still getting the crash when playing video or logging out though.

---

### Post by Arthur Archnix on 2008-05-02
Theo, I'd given up on Hardy for a bit and gone back to Gutsy to get some work done. Since a clean install I've made one change from last time and I haven't been able to reproduce the crash. I know your symptoms are slightly different. But perhaps you could try this for a day or so and see if you can reproduce the problem.

If you simply disable desktop effects you are still using compiz as a window manager. In order to switch back to metacity you need to change a key in gconf-editor. Hit Alt+F2 and type "gconf-editor". Then hit find and search for "window_manager". You'll see a key come up that says /something/something/compiz. There are two keys actually. Default and current. Change the default from "compiz" to "metacity". Leave the rest the same. Now restart 'X'. 

If this gets rid of the problem for you, and (crossing fingers) so far it has for me too, then I think we can say that the problem is likely with the compositing of 'X' and our 'intel' driver. Hard to say more. I'd been using metacity with compositing enabled and still getting the freaky crashes. This time I didn't enable metacity compositing and so far so good.

The next step to take is to figure out what's happening and file a bug report. You should have a system log feature. After the next crash note the date and time. Then go into the logs and look through 'x' and 'dmesg' looking for about that time. Something should jump out at you and you can post it here.

Good luck!

---

### Post by Theo148 on 2008-05-03
That sounds like it would work - I'll give it a try and report back.

Also, I agree with you on the likely cause of the problem.

Edit: Well, the new configuration seems to have fixed my video playback problem (several minutes of opening videos and jumping back and forth did not cause any crashes). However, the shutdown crash still turns up. I have checked several dmesg and Xorg logs after the crashes, but they seem to only be covering the events during the startup of the computer.

---

### Post by rootie on 2008-05-04
Hi everyone,

I'd like to raise the possibility that this may be an audio problem rather than a video problem. I run totem-xine, and I can't watch videos on it while downloading something on YouTube (either the system crashes, or the audio dies). Do you get this problem as well? I've tried spiderbatdad's lapci fix, and Arthur's compiz->metacity fix. No visual effects or anything.

---

### Post by Celauran on 2008-05-04
Mine is solely a shutdown problem, not video related at all. I think we may be looking at various issues here. I don't think the shutdown problem that some people are having is actually related to these video problems.

---

### Post by phoenix_abhi on 2008-05-04
Now What is the real pending problem ? Theo overcame the reboot/shutting down one. Those who facing video one for .wmv, Have they installed win32 codecs or other required proper codecs Coz if u were upgraded from Gutsy to Hardy it has removed a lot of stuffs while installing. Anyway try to install all codecs and disable the gnome compiz manager or GL desktop. It is not working fine with Hardy. Please reply how u people solving it out

---

### Post by rootie on 2008-05-04
Theo mentioned three problems, the startup freeze, the video problem, and the shutdown problem. While I sometimes get the shutdown problem, the video problem is more important for me to solve.

I'm convinced that the video problem is actually an audio problem. I have all required codecs installed, and although I haven't specifically tried to play WMV files, I get a crash when, for example, I run Pidgin (with sounds) before I play a video file, the computer either crashes or plays the video without sound for a few seconds before totem freezes. I'm not sure if Theo and I are getting the same problem, so I want to confirm.

---

### Post by Theo148 on 2008-05-04
Hmm... well with metacity as my window manager, I don't get the video crashes at all (at least I haven't had any yet). However, with Compiz running I do get similar symptoms with video playback. So yes, I'd say the problems are similar.

And I did mention earlier that I was still encountering the freezes on shutdown.

@Celauran: The reason I believe that the video and shutdown issues are related is because in both cases, the result is exactly the same - a totally unresponsive computer with a blank screen.

---

### Post by snap on 2008-05-05
To try to get a baring on what is actually happening I set up a fresh 8.04 install dual booting with and upgraded 8.04 install from 7.10.

In 7.10 I had issues with the "intel" driver, specifically Blank screen when switching VTs irrespective of the VT resolution, I then switched to "i810" driver and was happily running with below grub line, notice the "vga=773"
```

/boot/vmlinuz-2.6.22-14-generic root=UUID=972018f5-311c-4612-a293-be9ca1430423 ro rootflags=data=writeback **vga=773** splash quiet
```


Now my upgraded 8.04 install will not show correct resolution after a resume from hibernate, which was not a problem with 7.10, as this install still had my old xorg.conf file I switched to "intel" driver and had the blank scree freeze at logout and at VT switch (Ctrl+Alt+[F1-F8])

So I set up a fresh 8.04 installation to dual boot and I had the same blank screen freeze issues as all the other people here.
This 8.04 install has the "intel" driver with a very barren looking xorg.conf that was automatically created by the installation, so i have read somewhere that X 7.3 can do without a config file maybe thats why it is so empty. 

I finally switched back to "i810" driver in my upgrade 8.04 installation running XFCE and no problems atleast with the freeze at VT switching.
plus my grub looks like this now

```
/boot/vmlinuz-2.6.24-16-generic root=UUID=972018f5-311c-4612-a293-be9ca1430423 ro rootflags=data=writeback quiet
```

I still have to check if shutdown/logout and resume work properly.


--cheers! :)

---

### Post by jon435@gmx.net on 2008-05-06
i agree on the fact, that under gutsy the intel experimental driver had some issues so i also switched to the i810 driver which worked perfectly.

now here comes the noobish question: how the hell do i switch the driver in hardy? i am pretty new to the command line layer of linux so in gutsy i did change it with the "screens & graphics" gui tool. my fresh hardy install lacks this gui tool. so how do i change the driver using gui or cl?

thanks in advance...

jon435

---

### Post by jon435@gmx.net on 2008-05-06
and i hereby reply to my own question. problem solved. had to turn on "screens & graphics" in the main menu. kind of embarassing for myself:)

solution for my problem: i switched back to the i810 driver as i did on gutsy. works... however "screens & graphics" still has some issues regarding SELECTING the darn thing at all... in the end i did it a couple of times until it did switch to the driver.

p.s.: i also got the i855gm chipset. so this should also work for the thread owner.

jon435

---

### Post by snap on 2008-05-06
> **jon435@gmx.net said:**
> how the hell do i switch the driver in hardy? 
jon435

Good question :)
I use XFCE but I was able to confirm default Hardy install does not contain such a tool, maybe because the new X 7.3 manages all settings without needing a config file anymore.

I am using my xorg.conf from 7.10 you can try the same if u have a copy. 

I don't know how to generate a usable xorg.conf in hardy to override X auto detected defaults, maybe someone else on this forum can help

---

### Post by snap on 2008-05-06
jon

I couldn't find such a tool in gnome, but anyways glad to see it worked for you.

Are you able to log in fine? especially after a hibernate and resume and then a logout?

I have two further issues

After a resume the screen resolution is stretched and moving the mouse to the edge of the screen scrolls the desktop.

a subsequent logout and login leaves me at a blank and colored desktop with nothing else, the mouse is responsive and i can switch VTs

the second problem is gone after i switched to "slim" from GDM as the display manager.

---

### Post by jon435@gmx.net on 2008-05-06
> **snap said:**
> 

I couldn't find such a tool in gnome, but anyways glad to see it worked for you.

snap, i found the "old" gutsy tool which is still installes by default but also hidden by default. you can turn it on using System->Preferences->Main Menu. Then check the box near Other->Screens & Graphics. et voila, you got the old tool which at least lets you switch drivers.

greetings
jon

---

### Post by Theo148 on 2008-05-07
Well I'll give the old i810 driver a shot when I get back home. The experimental intel driver did work fine for me on Gutsy though, so I'm not sure if switching drivers will fix the problem for me - I'll report back in about half an hour.

---

### Post by jon435@gmx.net on 2008-05-07
> **Theo148 said:**
> Well I'll give the old i810 driver a shot when I get back home. The experimental intel driver did work fine for me on Gutsy though, so I'm not sure if switching drivers will fix the problem for me - I'll report back in about half an hour.

i hope it did work for you... i know how annoying this can be...

good luck!

---

### Post by Theo148 on 2008-05-07
Hmm... it seems that either due to my own tweaking or some default configuration, I was actually running the i810 driver all along. So it's not exactly like I can fix the problem by switching drivers. :P

Also, if anybody wants to try switching drivers and doesn't want to bother adding the 'Screens & Graphics' launcher to their main menu, you can start it by running:

```
gksu displayconfig-gtk
```

---

### Post by Arthur Archnix on 2008-05-07
Theo, I did that and saw that I was using i810 too. That's wrong. I was using intel on Gutsy, and it should be intel here. It could be that the fact that we were using the wrong driver is what's causing the problem.

I've changed mine to intel, and now I'm restarting my compositing. I'll let you know how it goes.

---

### Post by jon435@gmx.net on 2008-05-07
> **Arthur Archnix said:**
> Theo, I did that and saw that I was using i810 too. That's wrong. I was using intel on Gutsy, and it should be intel here. It could be that the fact that we were using the wrong driver is what's causing the problem.

I've changed mine to intel, and now I'm restarting my compositing. I'll let you know how it goes.

now as i am reading this something comes to my mind. you're right. in gutsy i also had to use the intel driver... nut nonetheless... its the i85x driver that causes trouble. play with the two drivers and find the one that fits your needs...

jon

---

### Post by Theo148 on 2008-05-08
Well the thing is that while I was also using the 'intel' driver in Gutsy, when I select the driver and test it in Hardy, all I get is a screen filled with mangled graphics. I guess the i810 driver was set as the default for the Intel 85x chipset for a good reason...

---

### Post by Arthur Archnix on 2008-05-08
> **Theo148 said:**
> Well the thing is that while I was also using the 'intel' driver in Gutsy, when I select the driver and test it in Hardy, all I get is a screen filled with mangled graphics. I guess the i810 driver was set as the default for the Intel 85x chipset for a good reason...

No, I disagree. I think it's a bug. It should have selected the intel driver for both me and you. When I manually changed it the screen went all crazy on me too. Distorted graphics. I was worried, but I knew that was the right driver. So I confirmed and applied changes anyway. And so far so good. I've not had x crash since re-enabling compositing.

I've got through the pages on your card at intel: [Here]("http://www.intel.com/products/chipsets/852gm/index.htm")

Intel is the correct driver. Unfortunately, because of the changes made from gutsy to hardy, I don't know how to revert the changes from the command line should this for some reason fail. It used to be that you just popped into xorg.conf and changed the driver back. They no longer put this information in xorg, and I can't find any documentation telling me where it is now.

---

### Post by Theo148 on 2008-05-08
Well I'm pretty sure xfix (in recovery mode) resets xserver back to its default state, so that would be one way of reverting any mistakes. Anyway, going on your advice I'll give the intel driver a shot.

---

### Post by Theo148 on 2008-05-10
Well there seem to be some problems with the configuration program, as when I hit 'Keep Configuration' after testing the intel driver, it just reverts back to the old i810 driver (although it doesn't say so until I close displayconfig and open it again).

---

### Post by spudratic on 2008-05-10
I have the intel 845g chipset running hardy.I have the same problem with compiz running cpu is very high around 80% just watching a video.I tried to change the driver from i810 to the intel driver like I did in gusty.No luck natulis  won't start with the intel driver.So i enabled proposed repo and downloaded the proposed intel driver and tried again to use the same error.Any one have any other info on this intel driver problem.

---

### Post by WishMaster on 2008-05-11
I confirm this too... I'm also using the Intel i855GM chipset.

After a clean install (dual boot with WinXP), I had trouble when exiting Ubuntu: I got a black screen while the cpu/disk was still running. The only thing I could do, was a hard reboot. When rebooting, I fell back to a root terminal, where I had to manually type 'fschk'.
That problem was fixed when there was an update of HAL.

Now I also have the problem of a crashing Ubuntu when playing a video (avi in Totem and wmv in Firefox). Crashes are appearing to happen randomly....

---

### Post by Arthur Archnix on 2008-05-15
It turns out that the intel driver didn't fix my problems. Still suffered random freezes and lockups requiring hard-reboots. 

I've reverted to Gutsy which is rock solid for me. problem solved.

---

### Post by quasimodo69 on 2008-05-16
> **Arthur Archnix said:**
> It turns out that the intel driver didn't fix my problems. Still suffered random freezes and lockups requiring hard-reboots. 

I've reverted to Gutsy which is rock solid for me. problem solved.
I too had these hard lockups that shut down my computer.I was running 6.4 on a box dual booted with Micro$oft.the Windows ran great on that box for 3 years.Installed 6.4 and it ran great-upgraded to 7.10 and it hit the fan.Random,black screens that took a restart of the power supply to restart computer.
After awhile my solution was to build another new computer soley for Ubuntu and relegate my windows box to the corner for guests.So far it has run great.AMD x2-nVidia 6100 onboard and the MoBo I used is an Abit ns-f5v...I think..sorry.
Being a noob my next task is to get wireless running and staying up!

---

### Post by jou770d on 2008-05-16
Add me to the list.
I have the same chipset and the same problems and maybe a couple more. My device is Toshiba Satellite A30-303 laptop. I have the resticted extras installed (and also using medibuntu). Tried both enabling and siabling desktop effect to no avail.
The crash also happens on restarts and shutdowns not only when loging out, switching to a terminal or playing videos.

The funny thing is that when I opened the screen and graphics' settings to check what driver is being used I found out that "none" is being used. :)
I tried using i810 but it only made things worst. I rebooted to a shaky blurry screen and there was two graphics cards listed in screen and graphics.
As for the experimental, it works but I still get the crashes.

Edit: I should probably mention that this same laptop was running gutsy with no problems (graphic-wise) using the i810 driver. But I'm not that eager to revert to gutsy cause I was having tons of other problems and hardy fixed them for me.

Edit-2: Something weird, but nevertheless great, just happened! I tried switching to the i810 driver again and I got the same result so I switched back to the experimental driver and the crashes were gone!! (I can't confirm if playing videos still crashes or not cause my vids are on my external which is with a friend).

---

### Post by Theo148 on 2008-05-17
It might not necessarily be relevant to this, but there was a recent update to GDM to fix some exit crashes...

---

### Post by moschops on 2008-05-18
Add me to the black screen of death victims here...

Using an Inspiron 700m with the Intel 855GM (I think) - worked fine with Gutsy although I did have to use the 915resolution hack to get the proper resolution.  I upgraded to Hardy and removed 915resolution but have been suffering from the shutdown/hibernate/suspend black screen of death problem since the upgrade.

I haven't yet tried any of the fixes - there seems to be many and I haven't exactly been able to sumize from the discussion which if any worked other than regressing to Gutsy.  

I did make a change to add some compositing option to xconf for the advanced desktop effects - otherwise all my windows would come up with out frames (just as in Hardy).  I haven't tried removing that.

I haven't realy noticed problems with playing videos though - I don't recall installing any extra codecs, assuming what I had before would have been removed  or upgraded appropriately during the update.

---

### Post by jon435@gmx.net on 2008-05-19
can anyone confirm the update fixing the exit crashes?

---

### Post by Theo148 on 2008-05-20
I wouldn't say confirm, but seeing as I haven't gotten any crashes on shutdown/logout yet, I'm hopeful.

---

### Post by WishMaster on 2008-05-21
The 'recent' updates for GDM and intel-video etc. MADE THINGS WORSE
Before, I had a 50/50 chance of crashing; now it crashes ALWAYS on shutdown.

On every reboot, I have to put my backup back.
Also, compiz-borders are gone on reboot.

8.04 sucks seriously hard, even Warty ran better...

---

### Post by vjsimon on 2008-05-22
> **alienexplorers said:**
> What video card are you using.  Please run the following command and list the output:

Hey,

I am experiencing the same problem too. Only difference is that my screen goes blank and I can't get it back up again. After I do a force shutdown and start the computer again, I go to recovery mode and no errors are reported. Strange but I did the command line and am listing the output here. Hope you guys can help.

home@BenQ:~/Desktop$ lspci -v 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <access denied>

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Benq Corporation Unknown device 500c
        Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Benq Corporation Unknown device 500c
        Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Benq Corporation Unknown device 500c
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at b0000000 (32-bit, prefetchable) [size=128M]
        Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, fast devsel, latency 0
	Memory at 20000000 (32-bit, prefetchable) [size=128M]
	Memory at 28000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1600 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=09, sec-latency=32
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: e0000000-efffffff
	Prefetchable memory behind bridge: a0000000-afffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1100 [size=16]
	Memory at 28080000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: medium devsel, IRQ 10
	I/O ports at 1400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at e100 [size=256]
	I/O ports at e200 [size=64]
	Memory at f0080400 (32-bit, non-prefetchable) [size=512]
	Memory at f0080600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: medium devsel, IRQ 10
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Capabilities: <access denied>

01:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation MIM2000/Centrino
	Flags: medium devsel, IRQ 10
	Memory at e0009000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 128, IRQ 5
	Memory at e0008000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c0c0 [size=64]
	Capabilities: <access denied>

01:09.0 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: a0000000-a3fff000 (prefetchable)
	Memory window 1: e4000000-e7fff000
	I/O window 0: 0000c400-0000c4ff
	I/O window 1: 0000c800-0000c8ff
	16-bit legacy interface ports at 0001

01:09.1 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: a4000000-a7fff000 (prefetchable)
	Memory window 1: e8000000-ebfff000
	I/O window 0: 0000cc00-0000ccff
	I/O window 1: 0000d000-0000d0ff
	16-bit legacy interface ports at 0001

01:09.2 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
	Subsystem: Benq Corporation Unknown device 500c
	Flags: medium devsel, IRQ 255
	I/O ports at c000 [size=128]
	Capabilities: <access denied>

01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Benq Corporation Unknown device 500c
	Flags: bus master, medium devsel, latency 128, IRQ 11
	Memory at e0000000 (32-bit, non-prefetchable) [size=2K]
	Memory at e0004000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by Theo148 on 2008-05-22
Well it seems like we are all having the same problem...

No dice on the update I'm afraid - I recently got a crash on shutdown again, although it doesn't happen as often to me as it does to WishMaster.

---

### Post by jon435@gmx.net on 2008-05-23
for me the recent update(s) made things worse. now i can't even shutdown nicely using ```
shutdown -p now
```. i am really getting frustrated. gutsy ran so much more stable for me than hardy...

---

### Post by In-flux on 2008-05-23
I seem to be having a very similar problem, but I have an NVidia graphics card.

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at b000 [size=32]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f8102000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Giga-byte Technology Unknown device ae01
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at bc00 [size=256]
	I/O ports at c000 [size=256]
	Memory at f8105000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f458:5002
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at f8100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at e800 [size=16]
	Memory at f8101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: f8000000-f80fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8103000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: f0000000-f7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
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

01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f8004000 (32-bit, non-prefetchable) [size=2K]
	Memory at f8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology GV-NX66128DP Turbo Force Edition
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0000000 (32-bit, non-prefetchable) [size=64M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: <access denied>
```

Crashes as soon as I login to my session. I can run in failsafe mode, except cannot play videos

---

### Post by Theo148 on 2008-05-26
Hmm... I was just wondering if what I encountered recently on [this topic]("http://ubuntuforums.org/showthread.php?t=800895") might be a clue to what's going on. I originally thought it was unrelated, but seeing as I had exactly the same symptoms as I encountered here, minus the blank screen, I suppose they might be connected somehow.

---

### Post by soro2005 on 2008-05-27
I think we'd be talking about something like [this bug here](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316). There are a few more bug reports with similar symptoms. I guess there are several problems, but some people seem to have had success by installing the newest xserver-xorg-video-intel from Debian Sid. But my impression is that that's not really what I want. Seems to use a lot of CPU here. In the meantime, using mplayer instead of totem seems to do the job for me. Or run gstreamer-properties and change Video Output to X Window System (no Xv). That's friggin ugly, though.

Also, I have found that my gdm was probably borked and cluttered by old config files picked up while upgrading from Feisty to Gutsy to Hardy. Completely uninstalling and reinstalling gdm might have solved the logout issue: Grab the package from [here](http://packages.ubuntu.com/hardy/gdm) and deposit it in your Home directory (that's just in case you find yourself without internet along the way and don't have the package in your chache). Save and close all your open work. Then go to a command line terminal (with ctrl+alt+f1, for instance), kill gdm (this will end your Gnome session, and not restart gdm) with
```
sudo killall gdm
```
Completely remove gdm:
```
sudo apt-get --purge remove gdm
```
This will remove a few more packages which depend on gdm. Take a note so you can reinstall them later. Then reinstall gdm:
```
sudo apt-get install gdm
```
Then try to start gdm with:
```
sudo gdm
```
Should gdm not start for whatever reason, startx might get you back to a graphical interface. Your wireless internet connection should stay alive as long as you don't shut down or reboot. But once it's down, you won't get it back up if you cannot log into a gnome session. For that case, and if sudo apt-get install doesn't work without connection
```
sudo dpkg -i gdm_whatever-the-current-number.deb
```
in your Home directory might get your gdm back to life. On the assumption that the package is deposited there, that is.

No guarantees that this doesn't cause major breakage. Perhaps, using Synaptic to "completely uninstall" gdm and install it anew does the same job.

---

### Post by Theo148 on 2008-05-29
Okay, I've found a workaround for this problem (suggested on the bug) that seems to be working. According to the information on the bug that soro2005 linked to, using xorg.conf to override the automatic detection settings and switch from the 'intel' driver (which is used by default - the gui tool is incorrect) to the older 'i810' driver will get rid of the problem, as the bug only exists in the 'intel' driver.

So first, I backed up my existing xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then I opened the file with
```
sudo gedit /etc/X11/xorg.conf
```

And scrolled to the following section:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

I added one line of text (shown in bold):
```
Section "Device"
	Identifier	"Configured Video Device"
	**Driver		"i810"**
EndSection
```

And then saved it and restarted.

I tested the new configuration with repeated logouts, shutdowns, and restarts, and have yet to encounter the crash (haven't tried video playback yet), so I'm relatively sure this will work. However, I'm not sure if there are any major issues with the 'i810' driver that anybody else might have - you could always run "sudo dpkg-reconfigure -phigh xserver-xorg" to reset things if anything blows up.

---

### Post by WishMaster on 2008-05-29
> **Theo148 said:**
> However, I'm not sure if there are any major issues with the 'i810' driver that anybody else might have 
My resolution (1400*1050) fell back to 1280*1024 (that looks fuzzier).
Video playback doesn't crash !
(resolution can be fixed with '915resolution' )




An alternative: if you want to log out, hit ctrl+alt+F1  (this will bring you to a terminal-like screen).
Type "killall -9 gdm"
Nest, it asks you if you want to boot in normal mode, or fix X-server,...
just type "sudo shutdown -h now"

It's very ugly, but it saves you from crashing. Video playback will still crash though.

Also, an ext3 partition can handle the crashes 'better'. An ext2 partition gave me lots of corrupted inodes, ext3 "fixes" them better, I have no loss of data with ext3.

---

### Post by unhot on 2008-06-10
I have had the same problem, with all the symptoms, for awhile now and I would highly recommend using theo148's method of going with the i810 driver until this is sorted. I have had no problems since adopting the i810 driver.

There have been times in the recent past of data loss where I have been unable to boot into Ubuntu that thankfully I was able to recover from. This bug should be taken very seriously as the hard crashes CAN be destructive, never mind annoying. I believe others have reached the same conclusion.

For the record, the bug was experienced on a Toshiba M35X-S149, running 8.04 upgraded from a Feisty / XP dual boot.

---

### Post by unhot on 2008-06-11
Oh and btw [THIS]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316")
works also, if you want to go back to the intel driver. Well at least so far it does.

---

### Post by Theo148 on 2008-06-12
Interesting... I'm on another computer right now (and I won't be able to get back onto mine for a while), but I'll try that fix when I can.

By the way, has any of the recent driver upgrades done anything to help?

---

### Post by WishMaster on 2008-06-16
> **unhot said:**
> Oh and btw [THIS]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/221316")
works also, if you want to go back to the intel driver. Well at least so far it does.
It works indeed... video crashes and logout crashes are as good as gone (in about 10% of the cases, it can crash)
scrolling in firefox is much slower, as said in that post

---

### Post by toddr on 2008-06-17
I have had the same "black screen of death" problem on my intel graphics laptop. This is what worked for me:
At the end of each kernel line in my menu.lst file I added "acpi=force" like this:
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=876b757d-2d8e-4b2a-9f3b-aeb31a30c5f9 ro single acpi=force

---

### Post by toddr on 2008-06-18
check out this post:
[http://ubuntuforums.org/showthread.php?t=623237&highlight=shutdown+problem&page=2](http://ubuntuforums.org/showthread.php?t=623237&highlight=shutdown+problem&page=2)

---

### Post by rybaxs on 2008-07-22
I got problem with my screen..

When I change the Model manufacturer with the same type of my monitor,
the screen distorted..

System -> Administration -> Screen and Graphics

What should i do to set the screen and graphics into its default, with out entering the Ubuntu desktop 7.10 gutsy gibbon..

---

### Post by Theo148 on 2008-07-22
> **rybaxs said:**
> I got problem with my screen..

When I change the Model manufacturer with the same type of my monitor,
the screen distorted..

System -> Administration -> Screen and Graphics

What should i do to set the screen and graphics into its default, with out entering the Ubuntu desktop 7.10 gutsy gibbon..
Once Ubuntu finishes loading, press Ctrl+Alt+F1 to get to a terminal screen. Login from there and run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I'm pretty sure that should reset xorg.conf to its default values. :)

---

### Post by Dodominyk on 2008-07-30
I had the "black screen when you log out" problem, and my hardware has an intel G35 chipset. I also had the problem that I could only have one application using an xv overlay at the same time, which did not happen in fedora 9, which I was using until recently.

All my problems got fixed after I installed a debian package of xserver-xorg-video-intel with version 2.3.2 (versus 2.2.X in the Hardy repositories) patched for ubuntu, which I found on the comment 19 of this webpage: [http://telperion.wordpress.com/2008/06/24/xserver-xorg-video-intel_232-su-ubuntu-hardy-heron/]("http://telperion.wordpress.com/2008/06/24/xserver-xorg-video-intel_232-su-ubuntu-hardy-heron/") . It's in italian, but a google translation made it understandable. With this, all the problems are gone! :) I can open 8 instances of mplayer at the same time with the -vo xv option and no slowdown!

Intel just released the version 2.4.0 of the drivers, which apparently is a significant improvement, so hopefully a Hardy package for that will appear soon. Or maybe someone here understands how to make a Hardy package out of the Debian experimental repositories: [http://packages.debian.org/experimental/x11/xserver-xorg-video-intel]("http://packages.debian.org/experimental/x11/xserver-xorg-video-intel") . That would be sweet.


I hope this fixes the problem for someone else

---

### Post by rybaxs on 2008-08-11
> **Theo148 said:**
> Once Ubuntu finishes loading, press Ctrl+Alt+F1 to get to a terminal screen. Login from there and run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I'm pretty sure that should reset xorg.conf to its default values. :)

Thanks! I've just copy the default configuration from another ubuntu xorg.conf. It Works!..

---

### Post by Theo148 on 2008-08-16
> **Dodominyk said:**
> Intel just released the version 2.4.0 of the drivers, which apparently is a significant improvement, so hopefully a Hardy package for that will appear soon. Or maybe someone here understands how to make a Hardy package out of the Debian experimental repositories: [http://packages.debian.org/experimental/x11/xserver-xorg-video-intel]("http://packages.debian.org/experimental/x11/xserver-xorg-video-intel") . That would be sweet.

Version 2.4.0 of the Xorg intel driver is available in Intrepid's repositories.

For i386: [http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0-1ubuntu1_i386.deb)

For amd64: [http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0-1ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.0-1ubuntu1_amd64.deb)

I have no idea if this fixes the problem, or how stable it is for that matter, but I'll download it and try it out.

Edit: There are some dependencies and package conflicts which I don't think I can resolve, so for now it's still i810 for me.

---

### Post by shane2peru on 2008-08-18
I'm not alone on this issue!!!  Wow.  I have narrowed mine down to strictly logging out issue.  (I haven't done and don't do many videos though).  I too have the intel 855GM graphics card.  So two questions.  1.  Has anyone found a fix?  2.  Has anyone reported a bug?

Shane

---

### Post by Theo148 on 2008-08-19
> **shane2peru said:**
> 1.  Has anyone found a fix?
The problem mentioned here is a bug in Xorg's 'intel' driver. It can be worked around by using xorg.conf to force the use of the older 'i810' driver, which does not have the bug but may have some other minor issues. There is a post with instructions on reverting to the i810 driver [here]("http://ubuntuforums.org/showpost.php?p=5068804&postcount=74").

> 2.  Has anyone reported a bug?
The bug has been reported and apparently fixed in newer versions of the intel driver (xserver-xorg-video-intel). Unfortunately, the new driver isn't in the Hardy repositories, and I haven't been able to figure out how to install the package from Intrepid.

Hope that helped. :)

---

### Post by shane2peru on 2008-08-19
> **Theo148 said:**
> The problem mentioned here is a bug in Xorg's 'intel' driver. It can be worked around by using xorg.conf to force the use of the older 'i810' driver, which does not have the bug but may have some other minor issues. There is a post with instructions on reverting to the i810 driver [here]("http://ubuntuforums.org/showpost.php?p=5068804&postcount=74").


The bug has been reported and apparently fixed in newer versions of the intel driver (xserver-xorg-video-intel). Unfortunately, the new driver isn't in the Hardy repositories, and I haven't been able to figure out how to install the package from Intrepid.

Hope that helped. :)

Thanks Theo!  I read a few of the pages of this thread, but not all of them.  Nice to know it has been reported!  Terrible to know that it will be fixed in Intrepid, but seems as though it will not be fixed in Hardy?!?  Thanks for the link for a work around, I will have to take a look at that.

Shane

---

### Post by gaminggeek on 2008-08-24
I'm having the same problem with blender on an intel X3100

---

### Post by SoliDphantoM on 2008-09-17
> **Theo148 said:**
> The problem mentioned here is a bug in Xorg's 'intel' driver. It can be worked around by using xorg.conf to force the use of the older 'i810' driver, which does not have the bug but may have some other minor issues. There is a post with instructions on reverting to the i810 driver [here]("http://ubuntuforums.org/showpost.php?p=5068804&postcount=74").

Hope that helped. :)

If this solves my problems I will blow my wad...I've been dealing with this for months and kept reading it was a driver issue, but was never quite sure how to switch the driver with the new xorg.conf setup. I kick myself now that it was that easy.

Thank you Ubuntu Community!!
(Also I have converted a Vista lover to our cause, he loves Ubuntu \\:D/)

---

### Post by mbturner on 2008-10-26
I have had this frustrating problem with Hardy Heron as well. I have a Dell Inspiron 700m, and the same crappy integrated video that all 700m's have - not sure if that's the problem or not - When I try shutting down, Hardy will get ALMOST there, but it never actually seems to turn all the way off. I can hear a fan going and the power light is still on. I have to hold the power button down for 5 secs to turn off, and that's bad for my HD! SO, anyone solved this? Any help would be very... helpful! thanks
-mt

---

### Post by mbturner on 2008-10-26
Ok, nvm, i will try the above.
THANKYOU

---

### Post by moschops on 2008-10-26
I can report my Inspiron 700m now works just great with Intrepid Ibex - suspend, hibernate etc. all appear to work.  It even powers off correctly before the battery is dead which it never did with Hardy!

---

### Post by alperyilmaz on 2008-11-11
I have Inspiron 700m and I'm having lots of difficulties with Hardy. Although I was planning not to do dist-upgrade every six months, I think I have to, so that all of problems vanish (hopefully) with new Ibex.

---

