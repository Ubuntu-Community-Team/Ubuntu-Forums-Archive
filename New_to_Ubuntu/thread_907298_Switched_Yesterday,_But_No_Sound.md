---
title: "Switched Yesterday, But No Sound"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by zeroxb on 2008-09-01
My friend showed my Ubuntu the other day after school and I literally fell in love with it. He gave me his Ubuntu 8.04.1 LTS Desktop Edition disc and I sped home to install it. The installation went off without a hitch, but when it booted up there was no sound. No system sounds or application sounds. I am used to debugging Windows problems and have yet to understand how to fix problems such as this. After moving around google for a while, I figured out that my problem may be my specific onboard card (snd_via82xx).

Has anyone had the same problem and has a fix they know of?

---

### Post by halitech on 2008-09-01
sounds like a matter of loading the correct modules. can you post the output of```
lspci -v
```

---

### Post by zeroxb on 2008-09-01
Thank you for such a quick reply!
Here you go.


00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: e8000000-e9ffffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Capabilities: <access denied>

00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs SB0090 Audigy Player
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at b000 [size=32]
	Capabilities: <access denied>

00:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs SB Audigy MIDI/Game Port
	Flags: bus master, medium devsel, latency 32
	I/O ports at b400 [size=8]
	Capabilities: <access denied>

00:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at ea004000 (32-bit, non-prefetchable) [size=2K]
	Memory at ea000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at b800 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c800 [size=16]
	I/O ports at cc00 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 17
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at d000 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d400 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at dc00 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at e000 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at ea005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: Elitegroup Computer Systems Unknown device 1899
	Flags: medium devsel, IRQ 21
	I/O ports at e400 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at ec00 [size=256]
	Memory at ea006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Unknown device 0200
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at a000 [size=256]
	Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e8000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
	Subsystem: PC Partner Limited Unknown device 0201
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

---

### Post by james_vanb on 2008-09-01
You may have already done this, but open a terminal and type alsamixer - unmute everything and see if you have sound.

---

### Post by zeroxb on 2008-09-01
Yes, I've double checked. Nothing is muted.

---

### Post by halitech on 2008-09-01
it looks like its being seen no problem. post the output of```
aplay -l
```

---

### Post by zeroxb on 2008-09-01
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by halitech on 2008-09-01
do you have onboard sound on your system as well as an add-on card?

---

### Post by zeroxb on 2008-09-01
Yes I do.

---

### Post by halitech on 2008-09-01
try plugging your speakers into your on-board jack and see if you have sound. I'm thinking it may have defaulted to them instead of the add-on card

---

### Post by zeroxb on 2008-09-01
Nope, still nothing :/

---

### Post by halitech on 2008-09-01
speakers are working? do you have a set of headphones to test with just in case something happened to the speakers?

---

### Post by zeroxb on 2008-09-01
Yes I checked my speakers then plugged in 2 pairs of headphones just in case.

I was reading over my previous replies and noticed that half of my pci has Capabilities: <access denied>.

Could this be the problem?

---

### Post by halitech on 2008-09-01
I think its just because we ran lspci instead of sudo lspci.

---

### Post by Elfy on 2008-09-01
just a maybe here - double click the volume icon so that you get the mixer panel, there should also be a switch tab - if there is check that the analog/digital switch is disabled. 

Audigy cards (at least all I have had anything to do with) appear to default to digital on which can result in no sound.

---

### Post by zeroxb on 2008-09-01
Nope, unchecked everything. Still no sound.

---

### Post by zeroxb on 2008-09-01
Sound issue solved!

Uninstalled and reinstalled my alsa drivers, then reboot.

Thanks to everyone for replying so quickly. I really appreciate it!

---

### Post by halitech on 2008-09-01
glad to hear you got it working. Don't forget to mark the thread as solved so others will know for searching

---

