---
title: "New graphics driver packages, at least a new name"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-11
I just noticed that these are new in Launchpad and soon in Oneiric repos:

NVidia:
- nvidia-current-updates_280.13-0ubuntu1
- nvidia-settings-updates_280.13-0ubuntu1
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-updates/280.13-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-graphics-drivers-updates/280.13-0ubuntu1)
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings-updates/280.13-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings-updates/280.13-0ubuntu1)

ATI/AMD
- fglrx-updates_8.872-0ubuntu1
- fglrx-amdcccle-updates_8.872-0ubuntu1
[https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer-updates/2:8.872-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/fglrx-installer-updates/2:8.872-0ubuntu1)

So, just a new name, or.

---

### Post by dino99 on 2011-08-11
i was not waiting for those but the newest stable 280.26 published a few days ago by nvidia.

---

### Post by ratcheer on 2011-08-11
I just installed fglrx-updates_8.872-0ubuntu1 and  fglrx-amdcccle-updates_8.872-0ubuntu1 from the repos, but my Catalyst Control Center still shows driver as version 11.6. What's up with that?


Tim

---

### Post by dino99 on 2011-08-12
got the packages into the repo. But nothing seems different with the previous packages.

---

### Post by el_koraco on 2011-08-12
> **ratcheer said:**
> I just installed fglrx-updates_8.872-0ubuntu1 and  fglrx-amdcccle-updates_8.872-0ubuntu1 from the repos, but my Catalyst Control Center still shows driver as version 11.6. What's up with that?


Tim

That's an fglrx bug, CCC shows the first driver version forever, regardless of the changes.

---

### Post by Harry33 on 2011-08-12
> **dino99 said:**
> got the packages into the repo. But nothing seems different with the previous packages.

It is likely just a new naming of those proprietary packages.

---

### Post by buzzmandt on 2011-08-12
aptitude show:
> aptitude show nvidia-current-updates
Package: nvidia-current-updates          
New: yes
State: not installed
Version: 280.13-0ubuntu1
Priority: optional
Section: restricted/misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 170 M
Depends: x11-common (>= 1:7.0.0), make, sed (> 3.0), dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers,
         patch, acpid, libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libx11-6, libxext6, libxv1, libxvmc1, zlib1g (>= 1:1.1.4),
         xorg-video-abi-10, xserver-xorg-core (>= 2:1.10.0-0ubuntu1~)
Recommends: nvidia-settings-updates
Conflicts: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Replaces: nvidia-180-modaliases, nvidia-185-modaliases, nvidia-current-modaliases
Provides: xorg-driver-video, xserver-xorg-video-
Description: NVIDIA binary Xorg driver, kernel module and VDPAU library
 The binary driver provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server. AGP, PCIe, SLI,
 TV-out and flat panel displays are also supported. 
 
 This package also includes the source for building the kernel module required by the Xorg driver, and provides NVIDIA's
 implementation of the Video Decode and presentation API. The latter enables acceleration for GeForce 8 and later series cards for
 h264 video. 
 
 GPUs such as GeForce series 6 or newer are supported. 
 
 See /usr/share/doc/nvidia-current-updates/README.txt.gz for a complete list of supported GPUs and PCIIDs


---

### Post by Harry33 on 2011-08-12
> **buzzmandt said:**
> aptitude show:

And that is exactly the same as the info for nvidia-current.

---

