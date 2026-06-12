---
title: "Intel 855GME 3D acceleration"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by mr_bigmouth on 2011-09-24
OK, so I have an old laptop running Lubuntu 11.04 (I switched from Xubuntu) with an Intel 855GME chipset, and the default drivers work fine for 2D stuff, but it's slooooooooooooooow for anything that requires hardware acceleration (even Armagetron Advanced!). Where can I find actual 3D drivers for this thing, and how do I install/enable them? Thanx in advance. :)

BTW, my laptop is an Acer Travelmate 4502LMi.

Also, I'm not trying to run Compiz. (Unless that's somehow required for 3D acceleration in games).

---

### Post by Frogs Hair on 2011-09-24
I found this thread in the archives  and I hope it points in the right direction .     [http://ubuntuforums.org/archive/index.php/t-40865.html](http://ubuntuforums.org/archive/index.php/t-40865.html)

---

### Post by mr_bigmouth on 2011-09-24
I tried installing the Dri drivers according to the instructions here [http://ubuntuforums.org/showthread.php?t=132908](http://ubuntuforums.org/showthread.php?t=132908) (skipping the kernel upgrade since the kernel I'm using is already 686), and the Dri common files installed fine, but when I try installing the i915 version, this happens:

```
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.freedesktop.org ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```Anyhow, I checked the dri.log file and here's what I got:
```

./install.sh: line 677: make: command not found
```What the heck is causing this to happen? I thought I already had "make".

EDIT: I installed make and tried it again, but the installer complained about missing gcc, so I installed that and tried it again and now I get this in the log file:

```
make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.38-11-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core/drm_auth.c:36:0:
/home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core/drmP.h:44:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[3]: *** [/home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/permanoob/Downloads/i915-20060309-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2
```

---

### Post by anewguy on 2011-09-24
I'm not going to say it's your problem, but since you had to install GCC......  Have you installed the build-essential package?

Dave ;)

---

### Post by mr_bigmouth on 2011-09-24
I just installed build-essentials and I got the same thing. >_<

---

### Post by wildmanne39 on 2011-09-24
Hi, those cards are supported by default now, but I think that being an older card, 3d is no longer supported in 11.04 as in 10.04.

If you open synaptic and type i915 you will see it there.
Thank you

---

### Post by mr_bigmouth on 2011-09-24
Great, what am I supposed to do now? Is there a way to "hack" it so that I can enable 3D?

---

### Post by wildmanne39 on 2011-09-24
Hi, this may help but read carefully what is says, down the page it talks about turning kms on for that driver and it is off by default because of a bug, if the fix work's you may get 3d support but I am not sure.
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You can do a google search also for your card and ubuntu 11.04 and it will show some site about your card.
Thank you

---

### Post by mr_bigmouth on 2011-09-24
Well, I read the Maverick Meerkat version of the article (since it's the latest one), and I created a xorg.conf file as specified, and that was enough to enable working 3D. :) It's sort of glitchy, but it's much better than it used to be. Thanks! :D

---

### Post by wildmanne39 on 2011-09-24
Hi, I am glad it is working better, enjoy ubuntu, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by mr_bigmouth on 2011-09-25
no problem. :D

---

