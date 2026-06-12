---
title: "ATI Radeon HD 4650"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by jaimedieu.sdb on 2012-01-31
Hi all,

I'm having a problem. I have a 1GB ATI Radeon HD 4650 in my laptop. After installing the proprietary driver for this VGA Card, the laptop only recognizes 256 MB of the VGA. How can I make use of my entire 1GB? 

Below is the result of the command " lspci -v | less"

02:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650] (prog-if 00 [VGA controller])
        Subsystem: Dell Device 0456
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 2000 [size=256]
        Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

---

### Post by partloer on 2012-02-01
Good question here are a couple of website that you can read about.

Basically that command doesn't represent what your GPU is actually using.  This seems to be the case when using the manufactures software.

[http://ubuntuforums.org/showthread.php?t=1703958]("http://ubuntuforums.org/showthread.php?t=1703958")

[http://askubuntu.com/questions/46197/how-to-check-video-memory-size]("http://askubuntu.com/questions/46197/how-to-check-video-memory-size")

---

