---
title: "WebGL working in Chromium but not in Firefox? Driver Problem?"
date: 2018-08-15
forum: New to Ubuntu
---

### Post by exxotec on 2018-08-15
WebGL is running in Chrome but not in Firefox, altough I turned every switch I could move in about:config and reinstalled the graphics card drivers.
My about:support says: "WebGL creation failed"

This is actually what I get in my Terminal when I try to get informations about my graphics card (a Nvidia 1050ti):

```
glxinfo | grep OpenGL
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  76
  Current serial number in output stream:  77

```

```
lspci -vnn | grep VGA -A 12
28:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c82] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:1c82]
    Flags: bus master, fast devsel, latency 0, IRQ 69
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    [virtual] Expansion ROM at f7000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_396, nvidia_396_drm
```

So in the OpenGL output there is a potential, that something is not working. But I don't know where to go for now.
It's frustrating, that there are official drivers, obiviously working in Chromium, but not in Firefox at all.

---

### Post by wildmanne39 on 2018-08-15
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

