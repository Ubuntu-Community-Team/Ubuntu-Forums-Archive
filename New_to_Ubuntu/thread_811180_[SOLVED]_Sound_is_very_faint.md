---
title: "[SOLVED] Sound is very faint"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by azizzle on 2008-05-28
I don't know when or why this happened, sometime in the last few days, but I just tried to play an mp3 with rythmbox and there is hardly any sound coming out. I have to turn it all the way up, and still it is very faint. I know I've done a couple of updates in the last few days, did something happen from that? 
I booted into windows and sound worked fine, so I know it's not a connection issue. I've also searched and can't find anything related. Help!

---

### Post by drs305 on 2008-05-28
Double click on the speaker icon and open up the full volume control panel. Sometimes the master volume or one of the other controls that you don't see on the basic volume control panel is set too low.
 
You can also open alsamixer and check the levels there:
```
alsamixer
```

---

### Post by azizzle on 2008-05-28
No that didn't work, but thanks. I rebooted again. Still nothing (didn't really have high hopes). Here is my lspci -v
code:
andrew@andrew-desktop:~$ lspci -v
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000b0000000-00000000bfffffff
	Capabilities: <access denied>

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: cfd00000-cfdfffff
	Prefetchable memory behind bridge: 00000000cfa00000-00000000cfafffff
	Capabilities: <access denied>

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: cf900000-cf9fffff
	Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=64]
	I/O ports at f800 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at cfffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f0de:0162
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e000 [size=16]
	Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at cc00 [size=16]
	Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfc00000-cfcfffff
	Prefetchable memory behind bridge: cfb00000-cfbfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at cfff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: nVidia Corporation Unknown device 0162
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c800 [size=8]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c624
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at cd000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at ac00 [size=128]
	[virtual] Expansion ROM at ce000000 [disabled] [size=128K]
	Capabilities: <access denied>

04:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Subsystem: Linksys WMP54G ver 4.1
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at cfcf8000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>

04:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Unknown device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at 9c00 [size=32]
	Capabilities: <access denied>

I'm not using the soundblaster, as I have been too lazy to look up the drivers, so I've just been using the onboard.

---

### Post by azizzle on 2008-05-29
Nobody can help?

---

### Post by azizzle on 2008-05-29
bump

---

### Post by drs305 on 2008-05-29
I'm no audio expert so I hesitated jumping back in again. I know pulseaudio is the default in hardy. If you had your system set up with ALSA earlier I guess it's possible it reverted. Check System, Preferences, Sound and see if ALSA is selected for all and you have the proper device selected. It may help, but if it doesn't - remember I'm not solving your problem, I'm just giving your post a bump ;-)

---

### Post by kansasnoob on 2008-05-29
Try installing "gnome-alsamixer" from synaptic. Afterwards you'll be able to open Gnome Alsa Mixer from Sound & Video.

Then try adjusting the toggles while playing your audio. I've found the 3 toggles farthest left and the 4 toggles farthest right to be most useful.

If that doesn't work you might try reinstalling "libao2" in synaptic.

Also, if it still doesn't work, let us know if this sound problem exists with all forms of audio playback. It could be "program" specific.

---

### Post by azizzle on 2008-05-29
> **kansasnoob said:**
> 

Also, if it still doesn't work, let us know if this sound problem exists with all forms of audio playback. It could be "program" specific.

Well I have a starting point for a solution: I have sound on the internet, and with MPlayer only. None of my other apps have sound. Not with vlc, rythmbox, or movie player. So I take it Mplayer commandeered my stuff, how do I go about regaining control?

---

### Post by kansasnoob on 2008-05-29
My only thought is that it has to be a "library" problem. Libraries are generally recognized by "lib" as in "libao2" or "libasound2".

If you're running Hardy (I hope) this is my default list of Hardy alsa apps:

alsa-base
alsa-utils
gstreamer0.10-alsa
libao2
libasound2
libesd-alsa0
libpt-1.10.10-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base
pulseaudio
vlc-plugin-alsa


And I always add either gnome-alsamixer or alsamixergui because I prefer using a gui to using the command line.

So, I'd try searching all of the above in synaptic and "ticking" them for reinstallation, otherwise I'm stymied.

BTW, if you're running anything but Hardy proceed with extreme caution!

---

### Post by azizzle on 2008-05-29
^ ok nice! All of them were already installed, except for the last one. Now vlc works. Now the only thing that's left is rythmbox. Do you know which library I need for rythmbox?

---

### Post by azizzle on 2008-05-30
So somehow my gstreamer properties were changed, or no long valid.

I opened up gstreamer-properties in the terminal, and messed with the settings: changed autodetect to alsa and now it works. Thanks for all your help guys

---

