---
title: "Audio / Sound Ubuntu Server with Intel D201GLY2"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by gwolfman on 2008-08-29
Hello,

I installed Ubuntu server 8.04.1 (64-bit) and vmware server 1.0.6 but the audio isn't installed so I cannot add a sound card in my XP guest.

I have the Intel D201GLY2 (D201GLY2A) motherboard.

The ouput of "lspci" says:
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
```

Any help would be greatly appreciated.

---

### Post by BDNiner on 2008-08-29
Does the sound work in ubuntu but doesn't work in the virtual machine? or you get no sound at all?

---

### Post by Crafty Kisses on 2008-08-29
How about the results of this > lspci -v

---

### Post by gwolfman on 2008-08-29
> **BDNiner said:**
> Does the sound work in ubuntu but doesn't work in the virtual machine? or you get no sound at all?

I don't think it's installed because I can't select it under the vmware server options (there aren't any sound card options)

> **Codename said:**
> How about the results of this > lspci -v

```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 2400 [size=256]
        I/O ports at 2880 [size=128]
        Capabilities: [48] Power Management version 2

```
If you need the whole output I'll post it.

I think Intel claims it's an ADI AD1888 (SoundMAX?) chip.

---

### Post by BDNiner on 2008-08-29
I checked on intel's site and they don't seem to have a linux driver for the board. from the output of lspci -v it seems like there has been an issue properly detecting what sound card you have.

---

### Post by Crafty Kisses on 2008-08-29
I guess me seeing the whole output wouldn't hurt.

---

### Post by gwolfman on 2008-08-29
> **BDNiner said:**
> I checked on intel's site and they don't seem to have a linux driver for the board. from the output of lspci -v it seems like there has been an issue properly detecting what sound card you have.
What (to you) signifies that it's having issues?

> **Codename said:**
> I guess me seeing the whole output wouldn't hurt.
Here ya go:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 662 Host (rev 01)
        Flags: bus master, medium devsel, latency 32
        Memory at 48000000 (32-bit, non-prefetchable) [size=32M]
        Capabilities: [c0] AGP version 3.5

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 4a000000-4a0fffff
        Prefetchable memory behind bridge: 40000000-47ffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 32
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 2c10 [size=16]
        Capabilities: [58] Power Management version 2

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 2400 [size=256]
        I/O ports at 2880 [size=128]
        Capabilities: [48] Power Management version 2

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at 4a104000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at 4a103000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at 4a102000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 23
        Memory at 4a101000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 2000 [size=256]
        Memory at 4a100000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 4a120000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA (rev 01) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        I/O ports at 2c28 [size=8]
        I/O ports at 2c34 [size=4]
        I/O ports at 2c20 [size=8]
        I/O ports at 2c30 [size=4]
        I/O ports at 2c00 [size=16]
        I/O ports at 2800 [size=128]
        Capabilities: [58] Power Management version 2

00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 3e000000-3e0fffff
        Capabilities: [d0] Express Root Port (Slot+) IRQ 0
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Capabilities: [f4] Power Management version 2

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04) (prog-if 00 [VGA controller])
        Subsystem: Intel Corporation Unknown device d61f
        Flags: 66MHz, medium devsel, IRQ 10
        BIST result: 00
        Memory at 40000000 (32-bit, prefetchable) [size=128M]
        Memory at 4a000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 1000 [size=128]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] AGP version 3.0

```

---

### Post by gwolfman on 2008-08-29
I've been doing some web searching, do I need any special packages installed to get this to work?

Does the "alsa-base" and/or "lib64asound2" packages have to be installed?  Or are there any other specific packages I need to install to get sound working?

Thanks for the help so far!

---

### Post by BDNiner on 2008-08-31
```

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Intel Corporation **Unknown device** d61f

```

this section. I have bolded the error. The same error appears for the SiS graphics card but there is a fix for this that can be found when searching google. I have been unable to find anything about what causes the audio driver error.

---

### Post by gwolfman on 2008-09-01
Humm, that's weird that it says there's an error with the video card.  Maybe I would notice if I tried to install an x-window system, but I'm just using text-based right now without any issues.

---

### Post by cariboo on 2008-09-01
If you are running the server version, the sound modules do load automagically. To check if they are in a terminal type:

```
lsmod | grep snd
```

This should give you a list of all the sound modules that are installed.

To enable the sound install **alas-base** and **asla-utils**, then run:

```
asoundconf list
```

THis will list all the sound cards in your system. The next step is to run:

```
asoundconf set-default-card PARAMETER
```

Where PARMETER is the sound card listed in the previous command.

Next run:

```
alsamixer
```

Turn up the volume and PCM, plug in your speakers, and your ready to play music.

Note: all commands should be run as a normal user.

Jim

---

### Post by gwolfman on 2008-09-01
> **cariboo907 said:**
> If you are running the server version, the sound modules do load automagically. To check if they are in a terminal type:

```
lsmod | grep snd
```

This should give you a list of all the sound modules that are installed.

To enable the sound install **alas-base** and **asla-utils**, then run:

```
asoundconf list
```

THis will list all the sound cards in your system. The next step is to run:

```
asoundconf set-default-card PARAMETER
```

Where PARMETER is the sound card listed in the previous command.

Next run:

```
alsamixer
```

Turn up the volume and PCM, plug in your speakers, and your ready to play music.

Note: all commands should be run as a normal user.

Jim

Hey thanks Jim, sounds good.  I'll give it a shot tomorrow after work if I can't find time tonight to do that.  I appreciate the info.  I'll let you know how it goes. :)

---

### Post by gwolfman on 2008-09-03
It looks good so far, though I'm still running into issues.

I did as you mentioned and everything seems to be ok.  I can now select the audio card in vmware server console though I can't seem to get any sound to play.  I will connect my headphones or speakers directly to the port to see if I can get some audio out of it.

Do I need to rerun "vmware-config.pl" again to get it to work properly?

---

