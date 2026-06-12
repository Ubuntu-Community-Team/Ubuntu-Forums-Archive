---
title: "No sound in V11.10 [64bit and 32bit, tried both]"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by Copperfield on 2012-01-13
I recently installed V11.10 64bit on my computer, however I do not get any sound output. I know my speakers/cables are okay, as the sound works fine in windows (I'm dual booting). I've run through the help files with regards to sound troubleshooting, so I've eliminated all the basic issues. I believe the issue is that my sound card is not being detected properly?
I have on-board sound, the motherboard is: ASUS M3N78-VM, with the sound chip being: VT1708B (high-definition audio 8 channel CODEC, supports jack-detect... etc).

Note that this is a fresh install, with the only change being enabling the 'additional drivers' specifically NVIDIA accelerated graphics driver (post-release updates) (version current-updates). Initially it had 'version 173' activated.

In the sound settings panel, under hardware it lists 1 entry:
[I]Internal Audio
1 Output / 1 Input
Analog Stereo Duplex[/I]
(note I tried the other profiles as well, analog stereo output, etc.)

And in termina when I run 'lspci -v | grep -A7 -i "audio"' I get the following:
[I]00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8345
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fce78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel[/I]

and 'aplay-l' gives:
[I]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]

Any suggestions on how to proceed on this one?

---

### Post by ubiquitin.jf on 2012-01-13
How are your speakers attached? If they're hooked up by HDMI you need to install your proprietary graphics card drivers.

---

### Post by Copperfield on 2012-01-13
Just the standard out port on the motherboard (green connector, marked 'front').

---

### Post by Bara84 on 2012-02-05
Same here... did you find a solution?

---

