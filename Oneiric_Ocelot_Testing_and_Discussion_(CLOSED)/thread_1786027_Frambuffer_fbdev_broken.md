---
title: "Frambuffer fbdev broken"
date: 2011-06-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-19
I was trying to make an IntelGma500 netbook working in Oneiric by using the new driver (really a kernel module) psb_gfx included in Kernel 3.x.
This driver require fbdev framebuffer to work,  but it seems broken the one included in Xorg 1.10.

Also trying to use only fbdev (and not psb_gfx) I'm not able to employ it.. this is a regression not present in NN.

```
(II) LoadModule: "fbdev"
[    15.607] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.607] (II) Module fbdev: vendor="X.Org Foundation"
[    15.607] 	compiled for 1.10.0, module version = 0.4.2
[    15.607] 	ABI class: X.Org Video Driver, version 10.0
[    15.607] (II) FBDEV: driver for framebuffer: fbdev
[    15.607] (++) using VT number 7

[    15.607] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    15.607] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    15.609] (II) Loading sub module "fbdevhw"
[    15.609] (II) LoadModule: "fbdevhw"
[    15.610] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.611] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.611] 	compiled for 1.10.2, module version = 0.0.2
[    15.611] 	ABI class: X.Org Video Driver, version 10.0
[    15.611] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.611] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.611] **(EE) open /dev/fb0: No such file or directory**
[    15.611] (WW) Falling back to old probe method for fbdev
[    15.611] (II) UnloadModule: "fbdev"
[    15.611] (II) Unloading fbdev
[    15.611] (II) UnloadModule: "fbdevhw"
[    15.611] (II) Unloading fbdevhw
[    15.611] (EE) Screen(s) found, but none have a usable configuration.
[    15.611] 
Fatal server error:
[    15.611] no screens found
```

I know fbdev is not commonly used (becuase better user-space drivers are available for other gfx chipsets) so probably no one encountered this issue.

Any hints? xorg-edgers-ppa maybe ships a newer version of xorg-fbdev?

---

### Post by dino99 on 2011-06-19
seems that fbdev is quite oldish and not so often maintained into xorg:

- if its not installed, then xorg log complaint, even if user have removed video=all
- its the same about nv or vesa

so xorg need some cleanings. Wonder if we can force it to ignore it in case of kernel module conflict. The other way is to blacklist the kernel module to test only with xorg.

---

### Post by lucazade on 2011-06-19
> **dino99 said:**
> seems that fbdev is quite oldish and not so often maintained into xorg:

- if its not installed, then xorg log complaint, even if user have removed video=all
- its the same about nv or vesa

so xorg need some cleanings. Wonder if we can force it to ignore it in case of kernel module conflict. The other way is to blacklist the kernel module to test only with xorg.

was thinking the same..

to blacklist fbdev I've added it maunally to blacklist.conf (in order to have a vesafb working otherwise there was a conflict between modules).

the fbdev kernel module doesn't seem to be shipped with stock kernel3.0 (at least modprobe and modinfo doesn't find the module).
I'd like to try the fbdev kernel module but I'd like to not recompile kernel to get it... is there a faster way to try it?

---

