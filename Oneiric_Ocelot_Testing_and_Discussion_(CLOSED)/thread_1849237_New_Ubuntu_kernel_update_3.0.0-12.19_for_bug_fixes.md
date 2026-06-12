---
title: "New Ubuntu kernel update 3.0.0-12.19 for bug fixes"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-24
This new bug fix version (3.0.0-12.19) is in Launchpad now.
Not yet in Oneiric repos, but available for manual installation.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-12.19](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0.0-12.19)

> **Changelog**
linux (3.0.0-12.19) oneiric; urgency=low

  [ Alex Bligh ]

  * SAUCE: (drop after v3.1) net/netfilter/nf_conntrack_netlink.c: fix Oops
    on container destroy
    - LP: #843892

  [ Andy Whitcroft ]

  * [Config] standardise on HZ=250
  * SAUCE: headers_install: fix #include "..." usage for userspace
    - LP: #824377
  * make module-inclusion selection retain the left overs
  * add a new linux-image-extras package for virtual

  [ edwin_rong ]

  * SAUCE: Staging: add driver for Realtek RTS5139 cardreader
    - LP: #824273

  [ Greg Kroah-Hartman ]

  * SAUCE: staging: rts5139: add vmalloc.h to some files to fix the build.
    - LP: #824273

  [ Jesse Sung ]

  * SAUCE: Unregister input device only if it is registered
    - LP: #839238

  [ Keng-Yu Lin ]

  * [Config] Enable CONFIG_RTS5139=m on i386/amd64
    - LP: #824273

  [ Leann Ogasawara ]

  * SAUCE: x86: reboot: Make Dell Optiplex 990 use reboot=pci
    - LP: #768039
  * SAUCE: x86: reboot: Make Dell Latitude E6220 use reboot=pci
    - LP: #838402

  [ Ming Lei ]

  * SAUCE: ata: make DVD drive recognisable on systems with Sandybridge CPT
    chipset
    - LP: #794642

  [ Paolo Pisati ]

  * [Config] Compile-in vfat support for armel
    - LP: #853783

  [ Randy Dunlap ]

  * SAUCE: staging: fix rts5139 depends & build
    - LP: #824273

  [ Tim Gardner ]

  * [Config] Fix binary-% build target
  * SAUCE: (drop after 3.0.0) OMAP3 and 4 hwmod I2C units only allow 16 bit
    access
    - LP: #852225

  [ Upstream Kernel Changes ]

  * hfsplus: Fix kfree of wrong pointers in hfsplus_fill_super() error path
    - LP: #854987
  * rt2x00: Serialize TX operations on a queue.
    - LP: #855239
 -- Leann Ogasawara <email address hidden>   Wed, 14 Sep 2011 06:14:30 -0700

---

### Post by VinDSL on 2011-09-24
Working fine!  Thanks, Harry!

```

vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo && dpkg -s mesa-utils && echo

Sat Sep 24 02:19:49 MST 2011
Ubuntu oneiric (development branch)
Linux 3.0.0-12-generic
unity 4.16.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

vindsl@Zuul:~$ 


```

---

### Post by dino99 on 2011-09-24
installed from repo :)

---

### Post by VinDSL on 2011-09-24
> **dino99 said:**
> installed from repo :)
Heh!  That was quick!  :)

---

