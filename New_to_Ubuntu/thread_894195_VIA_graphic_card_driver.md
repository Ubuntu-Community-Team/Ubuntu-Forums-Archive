---
title: "VIA graphic card driver"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by charlie1kimo on 2008-08-19
Hi, everyone...
This is my first time using Ubuntu, and I am trying to get everything set up. After installed, Ubuntu seemed to auto-configured most of the things for me. However, the graphic card driver seems a little bit weird.

I can run any 2D applications without any problems, but I can't get any of 3D applications working, such as compiz and google-earth. T_T

So what can I do to configure the graphic card?

My computer is AMD64 and graphic card is VIA K8M890, thank you for all of your help and advise!!!

---

### Post by alienexplorers on 2008-08-19
You need to load in a graphic card driver for you graphic card.  The only problem is I have only heard of drivers for nvidia, ati, and intel.  Did you try checking google to see if there is a driver.  Or you could check on the VIA page.

---

### Post by alienexplorers on 2008-08-19
I know this page is for edgy, but you might want to give it a read threw:
[http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/]("http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")

---

### Post by prshah on 2008-08-19
> **charlie1kimo said:**
> 
So what can I do to configure the graphic card?


Press alt+F2, and then give the command```
gksudo displayconfig-gtk
```, then click on the "Graphics card" tab, and post back which driver is in use; better yet, post a screenshot.

Also, open a terminal (Applications-Accessories-Terminal), and post back the output of these command```
glxinfo | grep -i direct
cat /var/log/Xorg.0.log | grep -i accel
cat /var/log/Xorg.0.log | grep  "dri"

```

---

### Post by charlie1kimo on 2008-08-19
> **prshah said:**
> Press alt+F2, and then give the command```
gksudo displayconfig-gtk
```, then click on the "Graphics card" tab, and post back which driver is in use; better yet, post a screenshot.

Also, open a terminal (Applications-Accessories-Terminal), and post back the output of these command```
glxinfo | grep -i direct
cat /var/log/Xorg.0.log | grep -i accel
cat /var/log/Xorg.0.log | grep  "dri"

```

After I did the displayconfig-gtk, the result is the following:
Graphic Card (VESA driver (generic))
Driver: None
Display Memory: Auto

And after I did the other commands, results are:

charlie@Xzero:~$ glxinfo | grep -i direct
direct rendering: Yes
0000:   f0000001  00000300  f0000006  00000001
0010:   f000000b  00000000  f000000c  00180200
0020:   f000000d  00180200  f000000e  80200020
0030:   f0000002  00000000  f0000003  00000000
0040:   f0000004  00000000  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22

charlie@Xzero:~$ cat /var/log/Xorg.0.log | grep -i accel
(==) CHROME(0): Acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)

charlie@Xzero:~$ cat /var/log/Xorg.0.log | grep  "dri"
	X.Org XInput driver : 2.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
(==) Matched openchrome for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
	ABI class: X.Org XInput driver, version 2.0
	ABI class: X.Org XInput driver, version 2.0
(!!) VIA Technologies does not support or endorse this driver in any way.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) [drm] loaded kernel module for "via" driver.
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): [dri] use agp.
(II) CHROME(0): [dri] frame buffer initialized.
(II) CHROME(0): [dri] kernel data initialized.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so

Thank you for your help!

---

### Post by charlie1kimo on 2008-08-19
bump...=(

---

### Post by skymera on 2008-08-19
Can't help sorry.
But my laptop has the K8M800 chipset and i am too looking for a way to enable 3D.

Hope you get it sorted :)

I've tried OpenChrome and Via for drivers but neither can give 3D.

UniChrome won't install properly so i can't test that.

Maybe give it a shot?

---

