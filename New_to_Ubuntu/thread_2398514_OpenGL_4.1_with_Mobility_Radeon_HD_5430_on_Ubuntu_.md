---
title: "OpenGL 4.1 with Mobility Radeon HD 5430 on Ubuntu 18.04 LTS"
date: 2018-08-13
forum: New to Ubuntu
---

### Post by samdejong86 on 2018-08-13
Hello Ubuntu forums,

I have recently replaced Windows 7 on my PC with Ubuntu 18.04.1 LTS. I am trying to play a game (Bioshock Infinite) via steam, but I'm told that it requires OpenGL 4.1. How do I set this up?

As far as I can tell, my graphics card (Mobility Radeon HD 5430) supports OpenGL 4.1, as I was able to play Bioshock Infinite on Windows with the same hardware.

Here are the results of some commands that might be helpful in diagnosing the issue:

```
$ lspci

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]
```

```
$ LIBGL_DEBUG=verbose glxinfo | grep version

libGL: Can't open configuration file /home/sam/.drirc: No such file or directory.
libGL: pci id for fd 4: 1002:68e1, driver r600
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/r600_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
libGL: Can't open configuration file /home/sam/.drirc: No such file or directory.
libGL: Can't open configuration file /home/sam/.drirc: No such file or directory.
libGL: Using DRI3 for screen 0
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.0.5
OpenGL core profile shading language version string: 3.30
OpenGL version string: 3.0 Mesa 18.0.5
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10


```


And some system information:

Ubuntu 18.04.1 LTS
Memory:    7.7 GiB
Processor: AMD® Fx(tm)-6100 six-core processor × 6 
Graphics:  AMD® Cedar
GNOME:     3.28.2
OS type:   64-bit

Thank you for your advice and assistance!

---

### Post by Claus7 on 2018-08-13
Hello and welcome to the forums!

As far as I can tell:
OpenGL version string: 3.0 Mesa 18.0.5

the version that you have installed is not the one required by the game. You can verify this by issuing just the command:
glxinfo | grep "OpenGL version"

Also your:
Max core profile version: 3.3

which does not include the 4.1 too. 

Checking in AMD's website, 
[https://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86_64&rev=15.9](https://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86_64&rev=15.9)
the proprietary driver should support this feature, yet using ubuntu 14.04.

Regards!

---

### Post by deadflowr on 2018-08-13
Unfortunately the open source drivers for that card only support 3.3
From: [https://www.x.org/wiki/RadeonFeature/]("https://www.x.org/wiki/RadeonFeature/")
> 19 OpenGL 4.2 is currently only supported on CYPRESS, CAYMAN and ARUBA. All other chips are currently limited to OpenGL 3.3
From memory somewhere else, I believe there are a few extensions required in order to meet the necessary needs of OpenGL 4.1 that have not or cannot be used or implemented by these cards with the open source drivers yet.

As stated the only current way is using Ubuntu 14.04.1 with the AMD closed source drivers.
But you need the 14.04.1 release, specifically: [http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")

Any Ubuntu version higher, like 14.04.2 or 16.04 or 18.04 will not run the drivers.
(Well 14.04.2 could I guess technically, but it's not supported by Ubuntu anymore, 14.04.1 is still supported, for another 9(ish) months or so.)

---

### Post by samdejong86 on 2018-08-13
> 
Checking in AMD's website, 
[https://support.amd.com/en-us/downlo...86_64&rev=15.9]("https://support.amd.com/en-us/download/desktop/previous/detail?os=Linux%20x86_64&rev=15.9")
the proprietary driver should support this feature, yet using ubuntu 14.04.

Would this driver work on Ubuntu 18.04, or am I out of luck getting this to work?

---

### Post by deadflowr on 2018-08-13
> **samdejong86 said:**
> Would this driver work on Ubuntu 18.04, or am I out of luck getting this to work?

As I posted already, no it will not work on 18.04.

---

### Post by samdejong86 on 2018-08-13
Bummer. 

Thanks for taking the time to help me, I really appreciate it.

-Sam

---

### Post by Yellow Pasque on 2018-08-15
You can try faking the OpenGL version. Start it like this:
```
MESA_GL_VERSION_OVERRIDE=4.1 MESA_GLSL_VERSION_OVERRIDE=410 bioshock
```
(I'm not sure what the game's binary is called. Substitute for 'bioshock' appropriately.)

> From memory somewhere else, I believe there are a few extensions required in order to meet the necessary needs of OpenGL 4.1 that have not or cannot be used or implemented by these cards with the open source drivers yet.
Yeah, more detail: [https://www.phoronix.com/scan.php?page=news_item&px=R600g-Almost-At-OpenGL-4.5](https://www.phoronix.com/scan.php?page=news_item&px=R600g-Almost-At-OpenGL-4.5)

---

### Post by Claus7 on 2018-08-15
Hello,

just an afterthought. Could Oibaf's drivers provide this support instead?
[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Regards!

---

### Post by Yellow Pasque on 2018-08-15
> **Claus7 said:**
> Could Oibaf's drivers provide this support instead?

I don't think so. As the article I linked to points out:
> At the moment OpenGL 4.x with R600g is only advertised for Radeon HD 5800 and HD 6900 series graphics cards. Other hardware at the moment is limited to OpenGL 3.3 due to not having ARB_gpu_shader_fp64 support.
But if the program you're using doesn't make use of the extension, you may be able to get away with faking the OpenGL version.

---

