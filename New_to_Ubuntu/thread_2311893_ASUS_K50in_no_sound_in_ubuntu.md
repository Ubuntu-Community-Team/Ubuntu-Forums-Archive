---
title: "ASUS K50in no sound in ubuntu"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by Mohammad_AMIN on 2016-01-31
aplay: device_list:268: no soundcards found...

lspci -v | grep -A7 -i "audio"
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: ASUSTeK Computer Inc. Device 16f3
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2

00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0




my alsa-information 
[http://www.alsa-project.org/db/?f=b857945944176e0b51485fd19a8e75c34ee6da35](http://www.alsa-project.org/db/?f=b857945944176e0b51485fd19a8e75c34ee6da35)


please help. i use ubuntu15.10

---

### Post by steveo314 on 2016-02-04
See if this helps:
[http://askubuntu.com/a/97017]("http://askubuntu.com/a/97017")

---

### Post by Mohammad_AMIN on 2016-02-05
sound of laptop dont back and i install linux mint . this os is very nice

---

