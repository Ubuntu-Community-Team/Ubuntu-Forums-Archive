---
title: "nvidia/bumblebee driver issues"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by readmylips on 2014-07-22
Hey guys,

So I've wasted two days trying to make the nvidia GT 540M driver to work properly on Ubuntu 12.04.4 LTS. First thing I did was install the proprietary drivers, then I downloaded the executable driver from the nvidia website and now I`m taking a swing at bumblebee. Let me paint you the picture..

```
root@ubuntubox:~# glxinfo | grep OpenGLOpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 9.0
OpenGL shading language version string: 1.30
OpenGL extensions:

```
```
root@ubuntubox:~# lshw -c video  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:2000(size=128) memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:3000(size=64)

```
```
root@ubuntubox:~# pidof bumblebeed 
3282

```
```
root@ubuntubox:~# lspci -nnk | grep -i vga -A3 | grep 'in use'    
Kernel driver in use: i915

```

If I try to run something say "optirun steam", i get:
```
[ 2193.457094] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[ 2193.457153] [ERROR]Aborting because fallback start is disabled.

```

I read around and people say that changing in the bumblebee.conf 'Driver=' to 'Driver=nvidia' and '[COLOR=#545454][FONT=arial]**KernelDriver**[/FONT][/COLOR][COLOR=#545454][FONT=arial]=[/FONT][/COLOR][COLOR=#545454][FONT=arial]**nvidia**[/FONT][/COLOR][COLOR=#545454][FONT=arial]-[/FONT][/COLOR][COLOR=#545454][FONT=arial]**current'**[/FONT][/COLOR] to 'KernelDriver=nvidia' should fix that, but it didn't for me.

I don't usually post asking for help, I read and do, but this one i swear I don't understand. If someone could shed some light over here it would be greatly appreciated.

Cheers.

---

### Post by readmylips on 2014-07-22
solved it.. [http://mylinuxexplore.blogspot.ro/2014/03/solved-nvidia-cant-access-secondary-gpu.html](http://mylinuxexplore.blogspot.ro/2014/03/solved-nvidia-cant-access-secondary-gpu.html)

---

