---
title: "audio/sound output"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by maddave2008 on 2008-08-25
i'm in the process of trying ubuntu,but i cant seem to get any sound from the line out jack,i installed the codecs to play the files but still no sound,when back on vista plenty of music comes from my pc,i was hoping that linux would be better than vista(the devils work)but if i have to do what is in the help files(inputing lines of code) then i dont think this is for me,am i wrong to think this or is it just one setting that needs adjusting,i hate MS and would welcome a fast pc,any help is welcome.

thank you for your time

pentium 4 3ghz
1 gb ram
onboard sound

---

### Post by Cypher on 2008-08-25
You booted Ubuntu from a LiveCD I presume? Did you try the latest Hardy version?

---

### Post by maddave2008 on 2008-08-25
> **Cypher said:**
> You booted Ubuntu from a LiveCD I presume? Did you try the latest Hardy version?

yes booted with the livecd,would the hardy version be more aplicable?and would a link for this be anywhere near here

---

### Post by Cypher on 2008-08-25
Hardy Heron 8.04 is the latest version of Ubuntu and you can download it [here]("http://www.ubuntu.com/getubuntu/download"). Just choose your mirror and off you go..

---

### Post by maddave2008 on 2008-08-25
thank you cypher but this is the one i am trying to use.

---

### Post by maddave2008 on 2008-08-25
got sound now,but it's very low,hardly hear it any ideas.

---

### Post by Cypher on 2008-08-25
Ahh, well it's good that you are using the latest version of Ubuntu and yet strange that your onboard audio wasn't detected as it is likely to be realtek or something based device.

Either way, please boot back into the LiveCD and open up a Terminal by going to Applications->Accessories->Terminal, type the command below and show us the output
```

sudo lspci -v
sudo lshw

```

Nevermind the above..:)

As far as the volume goes, you can tweak the volume bar like in Windows on the top right of the panel.

---

### Post by maddave2008 on 2008-08-25
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 8
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [80] AGP version 3.5
	Capabilities: [50] Power Management version 2

00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
	Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [70] Power Management version 2

00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8800000-fe8fffff
	Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [68] Power Management version 2
	Capabilities: [70] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable+
	Capabilities: [88] HyperTransport: MSI Mapping
	Capabilities: [98] Subsystem: VIA Technologies, Inc. Unknown device c323

00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [68] Power Management version 2
	Capabilities: [70] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable+
	Capabilities: [88] HyperTransport: MSI Mapping
	Capabilities: [98] Subsystem: VIA Technologies, Inc. Unknown device c323

00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5337 (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e000 [size=256]
	Capabilities: [c0] Power Management version 2

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: [c0] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at dc00 [size=32]
	Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at d880 [size=32]
	Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at d800 [size=32]
	Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d480 [size=32]
	Capabilities: [80] Power Management version 2

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at febffc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
	Flags: medium devsel
	Capabilities: [c0] Power Management version 2

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Subsystem: VIA Technologies, Inc. Unknown device 337e
	Flags: bus master, medium devsel, latency 128
	Capabilities: [58] HyperTransport: Interrupt Discovery and Configuration

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at d000 [size=256]
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [70] Subsystem: Unknown device 2bcb:424f

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [70] Subsystem: Unknown device 1cfc:5121

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	Expansion ROM at fe8e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7255
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 255d
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at feaef800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at c880 [size=128]
	Capabilities: [50] Power Management version 2

05:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
	Flags: bus master, medium devsel, latency 64, IRQ 25
	I/O ports at c800 [size=32]
	Capabilities: [dc] Power Management version 1

05:04.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
	Subsystem: Creative Labs Gameport Joystick
	Flags: bus master, medium devsel, latency 64
	I/O ports at cc00 [size=8]
	Capabilities: [dc] Power Management version 1

05:05.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: Belkin Root Hub
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

05:05.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
	Subsystem: Belkin Root Hub
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 2

05:05.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Belkin Root Hub
	Flags: bus master, medium devsel, latency 64, IRQ 24
	Memory at feafdc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2

ubuntu@ubuntu:~$ sudo lshw

Criky what a lot of info,sound level real low.

---

### Post by gentlejunk on 2008-08-25
hi! i have a problem with jack, pls help:
when jack is:
creating alsa driver ... hw:0|hw:0|64|3|44100|0|0|nomon|hwmeter|-|32bit

**** alsa_pcm: xrun of at least 4.101 msecs

if i want to run real time:

 /usr/bin/jackd -R -P70 -dalsa -r44100 -p64 -n3 -D -Chw:0 -Phw:0 -m -M

cannot use real-time scheduling (FIFO at priority 10) [for thread -1210063184, from thread -1210063184] (1: Operation not permitted)
cannot create engine

i have been to 'ubuntu studio controls' and enabled memlock 95% of system

what else can i do?

my soundcard:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30a2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4580000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

---

