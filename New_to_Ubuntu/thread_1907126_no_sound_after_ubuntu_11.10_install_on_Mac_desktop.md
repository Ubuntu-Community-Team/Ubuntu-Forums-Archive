---
title: "no sound after ubuntu 11.10 install on Mac desktop"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by nyx14850 on 2012-01-10
Hi, I just installed ubuntu on my Mac desktop as a dual boot and there is no sound when i boot the ubuntu partition. The volume and sound preferences are set correctly. The sound card is also recognized. Any ideas or help? Thanks!

There is no sound when I do: aplay /usr/share/sounds/alsa/Front_Center.wav

when i type 
lspci -v | grep -A7 -i "audio" i get:
00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
    Flags: bus master, fast devsel, latency 0, IRQ 57
    Memory at 90b04000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09) (prog-if 00 [Normal decode])

---

