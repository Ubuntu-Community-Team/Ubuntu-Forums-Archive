---
title: "Problem getting my new Sound card working"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-05-13
this is all I have done so far
lsmod | grep snd_virtuoso
```
snd_virtuoso 10564 0
snd_oxygen_lib 34176 1 snd_virtuoso
snd 70856 16 snd_virtuoso,snd_oxygen_lib,snd_mpu401_uart,snd_hd a_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwde p,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,sn d_timer,snd_seq_device
```

lspci -v

```
03:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [60] Express PCI/PCI-X Bridge IRQ 0

04:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Unknown device 8275
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at a000 [size=256]
	Capabilities: [c0] Power Management version 2
```

and I have added 
snd-virtuoso to /etc/modules
are in audio and pulse groups
onboard audio functions

---

### Post by Shadowmeph on 2008-05-13
I guess that I am totally out of luck then?

---

