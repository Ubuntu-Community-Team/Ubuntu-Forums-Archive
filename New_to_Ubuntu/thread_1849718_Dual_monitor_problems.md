---
title: "Dual monitor problems"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by disabled20191128 on 2011-09-25
Hi, 

I can't get dual monitors to work, i have an Asus p5b-vm running ubuntu 10.04, i have an Intel onboard graphic card and i also have an Nvidia 8400GS graphic card. Please help me!


lspci -v 

00:02.0 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 81ea
    Flags: fast devsel, IRQ 11
    Memory at feb00000 (32-bit, non-prefetchable) [disabled] [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [disabled] [size=256M]
    I/O ports at e000 [disabled] [size=8]
    Capabilities: <access denied>

and 

01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 9044
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 9c00 [size=128]
    [virtual] Expansion ROM at fe5e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau


lspci |grep -e VGA -e Display
00:02.0 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

---

### Post by disabled20191128 on 2011-09-26
Problem solved, my nvidia 8400GS had a vga an hdmi and a dvi slot, so i bought a dvi to vga cable and connected my 2nd monitor to the dvi slot, then i used the nvidia x server settings and finally got twinview working.

---

