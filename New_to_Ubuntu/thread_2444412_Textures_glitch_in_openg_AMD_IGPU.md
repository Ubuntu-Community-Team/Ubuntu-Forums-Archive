---
title: "Textures glitch in openg AMD IGPU"
date: 2020-05-29
forum: New to Ubuntu
---

### Post by dnikic on 2020-05-29
Upon opening most 3D games i encounter some sort of graphical glitches relating textures on Ideapad S145.
The same problem was present back from Ubuntu 18.04 and still is.
I've provided two example glitches in a picture below.

[ATTACH=CONFIG]286043[/ATTACH]

OS: Ubuntu 20.04 LTS x86_64
Kernel: 5.4.0-33-generic 
Processor: AMD® Ryzen 3 3200u with radeon vega mobile gfx × 4 
DE: Gnome 3.36.2
Windowing system: X11
Ram memory: 5,7 GiB (8gb total for System Ram and iGPUVram)
OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.0.4
Vulkan Instance Version: 1.2.131



```
  
*-display                 
       description: VGA compatible controller
       product: Picasso
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
       configuration: driver=amdgpu latency=0
       resources: irq:55 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:1000(size=256) memory:d0600000-d067ffff

```

---

### Post by Perfect Storm on 2020-05-30
Have you tried with Option “TearFree” “on” in the x org config file?

---

### Post by dnikic on 2020-05-30
I haven't attempted to edit the x11 config, but using wayland instead of x11 didn't fix the issue.

---

### Post by dnikic on 2020-08-09
**FIXED**

_Source_
It was a mesa bug:
[https://gitlab.freedesktop.org/mesa/mesa/-/issues/2814](https://gitlab.freedesktop.org/mesa/mesa/-/issues/2814)

_The fix_
created file:
sudo nano /etc/environment.d/mesa.conf 
pasted in:
AMD_DEBUG=nodmacopyimage

---

