---
title: "Nvidia drivers 285.03 beta released"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-18
Nvidia corporation has released new proprietary drivers: 285.03 beta.

Xorg-edgers has made this available for Ubuntu users really soon.
So you will find it in their PPA.

> 
RELEASE HIGHLIGHTS
* Fixed a bug causing corruption of images which are 2047 pixels wide.
* Improved performance of the RENDER extension on Fermi-based GPUs.
* Fixed a bug causing the X server to crash after a VT-switch while running an OpenGL stereo application which is a member of a swap group.


---

### Post by t1497f35 on 2011-08-18
It also features OpenGL 4.2 for GeForce 400+ series.

---

### Post by rburkartjo on 2011-08-18
harry tks for the heads up

---

### Post by Harry33 on 2011-08-18
> **rburkartjo said:**
> harry tks for the heads up

You are welcome.

---

### Post by VinDSL on 2011-08-18
Working great, Harry!

nvidia-current 285.03 / 3.1.0 kernel (daily build)


```

Thu Aug 18 12:32:15 MST 2011
Ubuntu oneiric (development branch)
Linux 3.1.0-999-generic
unity 4.8.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 285.03

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Swappiness: 45

```

---

### Post by Harry33 on 2011-08-18
> **VinDSL said:**
> Working great, Harry!

nvidia-current 285.03 / 3.1.0 kernel (daily build)



Fine.
Oh well, can you tell any difference between the kernels 3.1.0 rc2 (daily) and 3.0.1 (from Oneiric repos)?

---

### Post by godhika on 2011-08-18
Well if we only had Optimus support.....

---

### Post by VinDSL on 2011-08-18
> **Harry33 said:**
> Fine.
Oh well, can you tell any difference between the kernels 3.1.0 rc2 (daily) and 3.0.1 (from Oneiric repos)?
It booted up okay.  Everything looked like it was working, but I had to hit the road, so I played with it for less than an hour.

I'll give it a better workout, later tonight.  ;)

---

