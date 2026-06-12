---
title: "Sound Problem fix request [Ubuntu 14.04] [HP Pavilion G6]"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by P_sarkar on 2014-06-22
Dear Ubuntu experts,

I am finding following problem,

Internal laptop speakers are working but Headphone & External speakers are not working through front audio output.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Sound card info:
ps@ps-HP-Pavilion-g6-Notebook-PC:~$ lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
    Subsystem: Hewlett-Packard Company Device 3567
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
--
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 3567
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I have tried variuos fixes mentioned in the forum, however none-of-them applies for my machine [HP G6 Pavilion g] & [ Ubuntu 14.04] combination.
Kindly help.

---

### Post by lidex on 2014-07-01
From your description, I would guess those channels may be muted.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

