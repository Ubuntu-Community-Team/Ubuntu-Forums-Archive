---
title: "X Windows will not work in lubuntu 12.10"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by adlo on 2013-02-24
Hi all,
 
I have just installed lubuntu 12.10 64-bit on my Acer Aspire One (D270) netbook, but it will not boot into the GUI. If I try logging in from the command line and typing 'startx', the GUI will try and start up, but fails. This is despite the fact that X windows and the GUI worked fine during the installation.
 
Looking at the XOrg.0.log file, I think the graphics driver is the issue. This computer uses the Intel GMA 3650 chip. I was going to attach the log file, but the forum won't accept it for some reason. The relevant parts (I hope), though, are:
 
--------------------------------------------------------------------------------------
 
[ 152.579] Module class: X.Org Video Driver
[ 152.579] ABI class: X.Org Video Driver, version 13.0
[ 152.579] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
Haswell Server (GT2+), Haswell SDV Desktop (GT1),
Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
Haswell ULT Server (GT1), Haswell ULT Server (GT2),
Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
ValleyView PO board
[ 152.582] (II) VESA: driver for VESA chipsets: vesa
[ 152.582] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 152.582] (II) FBDEV: driver for framebuffer: fbdev
[ 152.582] (--) using VT number 7
[ 152.590] (II) intel(0): using device path '/dev/dri/card0'
[ 152.590] (WW) Falling back to old probe method for vesa
[ 152.590] (WW) Falling back to old probe method for modesetting
[ 152.590] (WW) Falling back to old probe method for fbdev
[ 152.590] (II) Loading sub module "fbdevhw"
[ 152.590] (II) LoadModule: "fbdevhw"
[ 152.591] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 152.591] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 152.591] compiled for 1.13.0, module version = 0.0.2
[ 152.591] ABI class: X.Org Video Driver, version 13.0
[ 152.592] (EE) intel(0): [drm] Failed to detect GEM. Kernel 2.6.28 required.
[ 152.592] (EE) intel(0): Failed to become DRM master.
[ 152.592] (II) UnloadModule: "intel"
[ 152.592] (EE) Screen(s) found, but none have a usable configuration.
[ 152.592] 
Fatal server error:
[ 152.592] no screens found
[ 152.592] (EE) 
Please consult the The X.Org Foundation support 
at [http://wiki.x.org](http://wiki.x.org)
for help. 
[ 152.592] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 152.592] (EE) 
[ 152.609] Server terminated with error (1). Closing log file.

---

### Post by gordintoronto on 2013-02-28
Have a look at this:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

