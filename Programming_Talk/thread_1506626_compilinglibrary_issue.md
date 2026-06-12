---
title: "compiling/library issue"
date: 2010-06-10
forum: Programming Talk
---

### Post by Mach1723 on 2010-06-10
I have been trying to run a build of the software Blender(version 2.5 - development) and it builds fine but when i run it i get.

> 
Error: File incomplete
Segmentation fault


I think this error has to do with my libGL.so which is a symlink to /usr/lib/libGL.so.195.36.15 -- this must have to do with the nvidia proprietary open GL library, though i don't know, and i hope thats not the issue, as another note the version of Blender in the ubuntu repo's is 2.49 and it runs fine.

heres the output of an ldd command( probally not useful )

>         
        linux-gate.so.1 =>  (0x00e00000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x0022a000)
        libpng12.so.0 => /lib/libpng12.so.0 (0x00bec000)
        libz.so.1 => /lib/libz.so.1 (0x0044a000)
        libsamplerate.so.0 => /usr/lib/libsamplerate.so.0 (0x0024b000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x007a2000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00eff000)
        libGL.so.1 => /usr/lib/nvidia-current/libGL.so.1 (0x00847000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00110000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x0045f000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x00181000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x00f8f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0057c000)
        /lib/ld-linux.so.2 (0x00cfd000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00cae000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x003df000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x00ac1000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x0090c000)
        libpulse-simple.so.0 => /usr/lib/libpulse-simple.so.0 (0x0018f000)
        libpulse.so.0 => /usr/lib/libpulse.so.0 (0x00194000)
        libdirectfb-1.2.so.0 => /usr/lib/libdirectfb-1.2.so.0 (0x006d6000)
        libfusion-1.2.so.0 => /usr/lib/libfusion-1.2.so.0 (0x00d58000)
        libdirect-1.2.so.0 => /usr/lib/libdirect-1.2.so.0 (0x001d6000)
        libGLcore.so.1 => /usr/lib/nvidia-current/libGLcore.so.1 (0x00f93000)
        libnvidia-tls.so.1 => /usr/lib/nvidia-current/tls/libnvidia-tls.so.1 (0x001ec000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x001ee000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x001fe000)


---

