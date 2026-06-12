---
title: "Ubuntu 14.04 Desktop - no audio at all in headphones and speakers"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by annismonadjem on 2017-02-16
[COLOR=#333333][FONT=Ubuntu]_1) Originally - **everything is working fine**:_
Ubuntu 14.04 desktop
uname-r: 3.13.0-109-generic

[U]2) Changed hardware (motherboard, processor, ram, monitor) - **sound/audio is NOT working**:
[/U]System: Kernel: 3.13.0-109-generic i686 (32 bit, gcc: 4.8.4)
Desktop: Gnome (Gtk 3.10.8) Distro: Ubuntu 14.04 trusty
Machine: System: Gigabyte product: N/A
Mobo: Gigabyte model: H110M-S2PH-CF version: x.x Bios: American Megatrends version: F2 date: 03/16/2016
CPU: Dual core Intel Pentium CPU G4400 (-MCP-) cache: 3072 KB flags: (lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13243.8
           Clock Speeds: 1: 3300.00 MHz 2: 3300.00 MHz
Graphics: Card: Intel Device 1902 bus-ID: 00:02.0
           X.Org: 1.15.1 drivers: fbdev,intel (unloaded: vesa) Resolution: 1366x768@76.0hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.3 Direct Rendering: Yes
Audio: Card: Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3 Sound: ALSA ver: k3.13.0-109-generic

How can I regain sound/audio ?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]


[/FONT][/COLOR]

---

### Post by Perfect Storm on 2017-02-16
you may try with the latest alsa driver,it may be your soundcard is so new - [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by annismonadjem on 2017-02-16
@Artificial Intelligence: Thanks! worked very well for me.

---

