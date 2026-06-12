---
title: "Login loop when second monitor is plugged."
date: 2024-09-28
forum: New to Ubuntu
---

### Post by jefemaestro6117 on 2024-09-28
Good day everyone.

I'm new using ubuntu.

[COLOR=#000000]My PC:[/COLOR]
[COLOR=#000000]Main OS: Windows 11[/COLOR]
[COLOR=#000000]CPU: Ryzen 5 5600G[/COLOR]
[COLOR=#000000]RAM: 16 GB[/COLOR]
[COLOR=#000000]GPU: RX 6600[/COLOR]
[COLOR=#000000]Motherboard: Gigabyte GA-A320M-S2H[/COLOR]
[COLOR=#000000]Storage: 1x NVMe 1TB, 1x SSD SATA 2TB and 1x HDD 1TB[/COLOR]
[COLOR=#000000]DP Monitor plugged in GPU *used for gaming[/COLOR]
[COLOR=#000000]HDMI Monitor plugged in Motherboard (iGPU) *Used for multimedia and browsing[/COLOR]

Previously I made a post about an issue for a new installation ([https://ubuntuforums.org/showthread.php?t=2501148](https://ubuntuforums.org/showthread.php?t=2501148)), but I realized that the issue stops when I unplug my second monitor.
I have the same issue as the guy in this post. ([https://ubuntuforums.org/showthread.php?t=2361716](https://ubuntuforums.org/showthread.php?t=2361716)).

I use iGPU for my second monitor instead GPU because I want all RX 6600 power for gaming while I watch some stream or video with the highest quality with my second monitor.

I tried to install AMD drivers from official website ([https://www.amd.com/en/support/download/linux-drivers.html](https://www.amd.com/en/support/download/linux-drivers.html)) and these instructions ([https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)). But the issue persist.

---

### Post by QIII on 2024-09-29
Is this a dual boot on bare metal, or are you using a virtual machine?

---

### Post by jefemaestro6117 on 2024-09-29
> **QIII said:**
> Is this a dual boot on bare metal, or are you using a virtual machine?
It's dual boot, but Ubuntu is installed in a second drive.
Ubuntu works if I use only one monitor.

---

