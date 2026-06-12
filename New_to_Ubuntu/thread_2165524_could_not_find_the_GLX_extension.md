---
title: "could not find the GLX extension"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by john_smith2 on 2013-08-05
Ubuntu Studio 12.04 64bit

Happens when trying to run blender through the terminal.

john@john-Aspire-5742:~$ blender
connect failed: No such file or directory
Xlib:  extension "GLX" missing on display ":0.0".
/build/buildd/blender-2.68.a+svn58900/intern/ghost/intern/GHOST_WindowX11.cpp:192: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!

Do  have to update my intel drivers and if yes how
john@john-Aspire-5742:~$ lspci -nnk | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)

---

### Post by john_smith2 on 2013-08-07
Bump

---

### Post by john_smith2 on 2013-08-18
Bump

---

### Post by zeljkojagust on 2013-08-18
Can you please execute the following in your console and paste the output here:

ldd /usr/lib/blender/blender

---

### Post by john_smith2 on 2013-08-18
john@john-Aspire-5742:~$  ldd /usr/lib/blender/blender 
    linux-vdso.so.1 =>  (0x00007ffffa5ff000)
    libGL.so.1 => /usr/lib/nvidia-current/libGL.so.1 (0x00007f83432fd000)
    libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007f834308f000)
    libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f8342e66000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f8342c4f000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f83429b3000)
    libpython3.3m.so.1.0 => /usr/lib/x86_64-linux-gnu/libpython3.3m.so.1.0 (0x00007f83423e0000)
    libGLEW.so.1.6 => /usr/lib/x86_64-linux-gnu/libGLEW.so.1.6 (0x00007f8342175000)
    libopenal.so.1 => /usr/lib/x86_64-linux-gnu/libopenal.so.1 (0x00007f8341f25000)
    libfftw3.so.3 => /usr/lib/libfftw3.so.3 (0x00007f8341baa000)
    libjack.so.0 => /usr/lib/x86_64-linux-gnu/libjack.so.0 (0x00007f8341966000)
    libsndfile.so.1 => /usr/lib/x86_64-linux-gnu/libsndfile.so.1 (0x00007f83416ff000)
    libSDL-1.2.so.0 => /usr/lib/x86_64-linux-gnu/libSDL-1.2.so.0 (0x00007f8341465000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f8341248000)
    libtiff.so.4 => /usr/lib/x86_64-linux-gnu/libtiff.so.4 (0x00007f8340fe4000)
    libOpenImageIO.so.1.1 => /usr/lib/libOpenImageIO.so.1.1 (0x00007f83409d1000)
    libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007f8340781000)
    libboost_filesystem.so.1.49.0 => /usr/lib/libboost_filesystem.so.1.49.0 (0x00007f8340562000)
    libboost_system.so.1.49.0 => /usr/lib/libboost_system.so.1.49.0 (0x00007f834035d000)
    libboost_thread.so.1.49.0 => /usr/lib/libboost_thread.so.1.49.0 (0x00007f8340142000)
    libboost_locale.so.1.49.0 => /usr/lib/libboost_locale.so.1.49.0 (0x00007f833fe69000)
    libHalf.so.6 => /usr/lib/libHalf.so.6 (0x00007f833fc25000)
    libIex.so.6 => /usr/lib/libIex.so.6 (0x00007f833fa06000)
    libIlmImf.so.6 => /usr/lib/libIlmImf.so.6 (0x00007f833f745000)
    libtinyxml.so.2.6.2 => /usr/lib/libtinyxml.so.2.6.2 (0x00007f833f52f000)
    libopenjpeg.so.2 => /usr/lib/libopenjpeg.so.2 (0x00007f833f30f000)
    libavformat.so.55 => not found
    libavcodec.so.55 => not found
    libavutil.so.52 => not found
    libavdevice.so.55 => not found
    libswscale.so.2 => /usr/lib/x86_64-linux-gnu/libswscale.so.2 (0x00007f833f0c7000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f833ee8a000)
    libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007f833eb2e000)
    libspnav.so.0 => /usr/lib/libspnav.so.0 (0x00007f833e929000)
    liboslcomp.so.1.3 => /usr/lib/liboslcomp.so.1.3 (0x00007f833e6c8000)
    liboslexec.so.1.3 => /usr/lib/liboslexec.so.1.3 (0x00007f833e310000)
    liboslquery.so.1.3 => /usr/lib/liboslquery.so.1.3 (0x00007f833e0f2000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f833ddf2000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f833dabd000)
    libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007f833d8ad000)
    libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007f833d6a8000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f833d4a4000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f833d0e4000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f833cde8000)
    libgomp.so.1 => /usr/lib/x86_64-linux-gnu/libgomp.so.1 (0x00007f833cbda000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f833c9c3000)
    libnvidia-tls.so.304.88 => /usr/lib/nvidia-current/tls/libnvidia-tls.so.304.88 (0x00007f833c7c0000)
    libnvidia-glcore.so.304.88 => /usr/lib/nvidia-current/libnvidia-glcore.so.304.88 (0x00007f833a3d6000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f833a1c4000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f8339fbc000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f8339d91000)
    libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007f8339b8e000)
    libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007f8339944000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f8339474000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f8339248000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f8339041000)
    libasound.so.2 => /usr/lib/x86_64-linux-gnu/libasound.so.2 (0x00007f8338d53000)
    libpulse-simple.so.0 => /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0 (0x00007f8338b4f000)
    libpulse.so.0 => /usr/lib/x86_64-linux-gnu/libpulse.so.0 (0x00007f8338907000)
    libcaca.so.0 => /usr/lib/x86_64-linux-gnu/libcaca.so.0 (0x00007f833863b000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f834363c000)
    libboost_regex.so.1.49.0 => /usr/lib/libboost_regex.so.1.49.0 (0x00007f8338333000)
    libwebp.so.2 => /usr/lib/x86_64-linux-gnu/libwebp.so.2 (0x00007f83380fb000)
    libicuuc.so.48 => /usr/lib/libicuuc.so.48 (0x00007f8337d90000)
    libicui18n.so.48 => /usr/lib/libicui18n.so.48 (0x00007f83379c8000)
    libImath.so.6 => /usr/lib/libImath.so.6 (0x00007f83377c1000)
    libIlmThread.so.6 => /usr/lib/libIlmThread.so.6 (0x00007f83375ba000)
    libavutil.so.51 => /usr/lib/x86_64-linux-gnu/libavutil.so.51 (0x00007f833739a000)
    libLLVM-3.1.so.1 => /usr/lib/x86_64-linux-gnu/libLLVM-3.1.so.1 (0x00007f8335e06000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f8335be8000)
    libpulsecommon-1.1.so => /usr/lib/x86_64-linux-gnu/libpulsecommon-1.1.so (0x00007f8335989000)
    libjson.so.0 => /usr/lib/x86_64-linux-gnu/libjson.so.0 (0x00007f8335781000)
    libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f833553c000)
    libslang.so.2 => /lib/x86_64-linux-gnu/libslang.so.2 (0x00007f83351cb000)
    libncursesw.so.5 => /lib/x86_64-linux-gnu/libncursesw.so.5 (0x00007f8334f9e000)
    libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007f8334d76000)
    libicudata.so.48 => /usr/lib/libicudata.so.48 (0x00007f8333a06000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f83337fd000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f83335fa000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f83333f4000)
    libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f83331ea000)
    libasyncns.so.0 => /usr/lib/x86_64-linux-gnu/libasyncns.so.0 (0x00007f8332fe4000)
    libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f8332dc9000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f8332bad000)

---

### Post by zeljkojagust on 2013-08-18
I think this should resolve your problem:
[http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work](http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work)

---

