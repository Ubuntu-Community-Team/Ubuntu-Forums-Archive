---
title: "Sound Issues on Startup"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by S1xp4ck on 2008-06-11
Greetings,

I am fairly new to Ubuntu and I am having an issue with sound and looking for direction on how to proceed.

The problem seems to be on startup and so far seems on specific to games.  If I hear the tribal drums right before login prompt, the sound will work properly for games.  When I don't hear this sound and login, I get the login drums and sound will work for the majority off applications except for games withing the Ubuntu menu itself.

I am suspecting it has something to do with pulseaudio or Alsa not playing nice in relation to my sound card or another program but again, I am limited in Linux and need ideas on how to proceed troubleshooting this problem.

I am running Hardy x86 (up to date)
Audigy2 ZS Soundcard
AMD X2 4800+

Thanks in advance.

---

### Post by S1xp4ck on 2008-06-11
lspci info


```
00:00.0 Memory controller [0580]: nVidia Corporation CK804 Memory Controller [10de:005e] (rev a3)
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping

00:01.0 ISA bridge [0601]: nVidia Corporation CK804 ISA Bridge [10de:0050] (rev a3)
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus [0c05]: nVidia Corporation CK804 SMBus [10de:0052] (rev a2)
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at bc00 [size=32]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2

00:02.0 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005a] (rev a2) (prog-if 10 [OHCI])
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller [0c03]: nVidia Corporation CK804 USB Controller [10de:005b] (rev a3) (prog-if 20 [EHCI])
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:06.0 IDE interface [0101]: nVidia Corporation CK804 IDE [10de:0053] (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device [f47b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at d000 [size=16]
	Capabilities: [44] Power Management version 2

00:07.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0054] (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d400 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:08.0 IDE interface [0101]: nVidia Corporation CK804 Serial ATA Controller [10de:0055] (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at e800 [size=16]
	Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:09.0 PCI bridge [0604]: nVidia Corporation CK804 PCI Bridge [10de:005c] (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff

00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at fc00 [size=8]
	Capabilities: [44] Power Management version 2

00:0b.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0c.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0e.0 PCI bridge [0604]: nVidia Corporation CK804 PCIE Bridge [10de:005d] (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3450 [1002:95c5] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Unknown device [174b:e670]
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ac00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
	Subsystem: PC Partner Limited Unknown device [174b:aa28]
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

05:07.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023] (prog-if 10 [OHCI])
	Subsystem: ABIT Computer Corp. Unknown device [147b:1c12]
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

05:08.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
	Subsystem: Creative Labs SB Audigy 2 ZS (SB0350) [1102:2002]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 9c00 [size=64]
	Capabilities: [dc] Power Management version 2

05:08.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
	Subsystem: Creative Labs SB Audigy MIDI/Game Port [1102:0040]
	Flags: bus master, medium devsel, latency 32
	I/O ports at 9800 [size=8]
	Capabilities: [dc] Power Management version 2

05:08.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04) (prog-if 10 [OHCI])
	Subsystem: Creative Labs SB Audigy FireWire Port [1102:0010]
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fdefe000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

```

2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

---

### Post by ukripper on 2008-06-11
> **S1xp4ck said:**
> Greetings,

I am fairly new to Ubuntu and I am having an issue with sound and looking for direction on how to proceed.

The problem seems to be on startup and so far seems on specific to games.  If I hear the tribal drums right before login prompt, the sound will work properly for games.  When I don't hear this sound and login, I get the login drums and sound will work for the majority off applications except for games withing the Ubuntu menu itself.

I am suspecting it has something to do with pulseaudio or Alsa not playing nice in relation to my sound card or another program but again, I am limited in Linux and need ideas on how to proceed troubleshooting this problem.

I am running Hardy x86 (up to date)
Audigy2 ZS Soundcard
AMD X2 4800+

Thanks in advance.

When you don't hear drums at login then can you log in and check the volume icon whether it is mute.

---

### Post by S1xp4ck on 2008-06-11
Volume icon is not muted.   I always get the "login" drums after entering my user name and pw.   What I sometimes do not hear is the "bongo" beat at the login prompt. When that happens, I have no sound in games but most other sound events seem to function.

---

### Post by S1xp4ck on 2008-06-11
I ran the Hardware Testing app and found an interesting result.  

I get no sound on this test and it dectects HDMI as my sound card.  hmmmm

---

### Post by S1xp4ck on 2008-06-11
Running the "Hardware Testing" showed "HDMI" from my audio card instead of Audigy 2.  I also noticed that in Services: Audio Settings Managment was unchecked for some reason.

After I changed and rebooted the Hardware Testing is still showing my sound as HDMI.   I think this is the cause of my sound issues.  Does anyone know how I can force Ubuntu to recognize my card correctly on startup?

---

### Post by Golem XIV on 2008-06-11
Did you disable the on-board sound card on your motherboard?  It should be possible to do it either through the BIOS or via a jumper on the motherboard (or both).

---

### Post by S1xp4ck on 2008-06-11
Ok I got it all sorted out.

The problem was my Radeon HD 3450 has minimal audio support for HDMI to a TV/ HD etc.   Thus I had 2 sound drivers :

Using 

```
cat /proc/asound/modules
```

I referenced my 2 drivers:

snd_hda_intel ( ATI One)
snd_emu10k1 (Audigy2)

The ATI driver was set as default thus causing apps like games to not have sound.

In terminal I used:

```
sudo nano /etc/modprobe.d/alsa-base
``` and added the following at the bottom

```
options snd-emu10k1 index=0
options snd-hda-intel index=1

```

My Audigy2 is now default and all is good.  

This might come in handy for those using the lower end ATI HD cards with a soundcard.

---

