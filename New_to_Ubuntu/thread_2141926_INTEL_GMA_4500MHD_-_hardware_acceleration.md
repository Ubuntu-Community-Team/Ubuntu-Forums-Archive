---
title: "INTEL GMA 4500MHD - hardware acceleration"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by dias75 on 2013-05-04
INTEL GMA 4500MHD 

$ glxinfo | grep OpenGL 
OpenGL vendor string: Tungsten Graphics, Inc 
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2 
OpenGL version string: 2.1 Mesa 7.9-devel 
OpenGL shading language version string: 1.20 
OpenGL extensions: 
~$ 
 
$ glxinfo | grep render 
direct rendering: Yes 
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2 
dell@dell-Inspiron-1545:~$  
 
 
lspci -ks `lspci|grep VGA|awk '{print $1}'` 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
    Subsystem: Dell Device 02aa 
    Kernel driver in use: i915 
    Kernel modules: i915 
--[I]
I want to get the video card hardware acceleration. Card supports it. [/I][https://01.org/linuxgraphics/community/vaapi](https://01.org/linuxgraphics/community/vaapi)
[I]
But[/I]
$ vainfo libva 
libva: libva version 0.31.0 
libva: va_getDriverName() returns 0 
libva: Trying to open /usr/lib/dri/i965_drv_video.so 
libva: va_openDriver() returns -1 
vaInitialize failed with error code -1 (unknown libva error),exit 
~$ 
[I]
Please tell me why vainfo produces an error ? 
And where does this i965 chipset, if my chipset G45 ?
[/I]
libva1 libva-x11-1 installed 
i965-va-driver - no

---

### Post by brainwash on 2013-05-04
The package **i965-va-driver** supports the Intel G45 & HD Graphics family. Moreover, you should read following thread for additional information:

[http://ubuntuforums.org/showthread.php?t=2104318](http://ubuntuforums.org/showthread.php?t=2104318)

---

