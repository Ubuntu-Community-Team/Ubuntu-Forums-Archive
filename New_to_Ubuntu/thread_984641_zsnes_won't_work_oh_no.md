---
title: "zsnes won't work oh no"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by ColeJayStooks on 2008-11-16
hey guys another question thanks for helping before with thunderbird

now i'm trying to get the zsnes emulator running, but it's not working out. i installed the version in the repository so that should work, right?

i remembered that i didn't have 3D acceleration on so i installed my propriety nvidia drivers... restart the comp then i get a dialogue box saying my driver is not activated, but it is installed. so i activate it, forced to restart, then try to run zsnes again. nothing happens... i can run GENS just fine though with that package that's on the forums (i wonder why that's not in the repository though lol)

anyway this is what i get. at first i get the impression it needs to be run as root so i could give it some configurations but i guess not.

```
~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c27558]
/lib/tls/i686/cmov/libc.so.6[0xb7c25680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 5711498    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 5711498    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 5711498    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09748000-097bb000 rw-p 09748000 00:00 0          [heap]
b5daa000-b68b8000 rw-p b5daa000 00:00 0 
b68b8000-b68e0000 r-xp 00000000 08:01 4161648    /lib/libpcre.so.3.12.1
b68e0000-b68e1000 r--p 00027000 08:01 4161648    /lib/libpcre.so.3.12.1
b68e1000-b68e2000 rw-p 00028000 08:01 4161648    /lib/libpcre.so.3.12.1
b68e2000-b6997000 r-xp 00000000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6997000-b6998000 r--p 000b4000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6998000-b6999000 rw-p 000b5000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6999000-b699d000 r-xp 00000000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b699d000-b699e000 r--p 00003000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b699e000-b699f000 rw-p 00004000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b69b1000-b69b2000 rw-p b69b1000 00:00 0 
b69b2000-b6a00000 r-xp 00000000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b6a00000-b6a01000 r--p 0004d000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b6a01000-b6a02000 rw-p 0004e000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b6a02000-b6a0e000 r-xp 00000000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b6a0e000-b6a0f000 r--p 0000b000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b6a0f000-b6a10000 rw-p 0000c000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b6a14000-b6a17000 r-xp 00000000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b6a17000-b6a18000 r--p 00002000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b6a18000-b6a19000 rw-p 00003000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b6a19000-b6a1e000 r-xp 00000000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b6a1e000-b6a1f000 r--p 00004000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b6a1f000-b6a20000 rw-p 00005000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b6a20000-b6a21000 r-xp 00000000 08:01 5734767    /usr/lib/ao/plugins-2/libarts.so
b6a21000-b6a23000 rw-p 00000000 08:01 5734767    /usr/lib/ao/plugins-2/libarts.so
b6a23000-b6a45000 r-xp 00000000 08:01 5712559    /usr/lib/libaudiofile.so.0.0.2
b6a45000-b6a48000 rw-p 00021000 08:01 5712559    /usr/lib/libaudiofile.so.0.0.2
b6a48000-b6a51000 r-xp 00000000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a51000-b6a52000 r--p 00008000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a52000-b6a53000 rw-p 00009000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a53000-b6a68000 r-xp 00000000 08:01 5712434    /usr/lib/libICE.so.6.3.0
b6a68000-b6a69000 rw-p 00014000 08:01 5712434    /usr/lib/libICE.so.6.3.0
b6a69000-b6a6b000 rw-p b6a69000 00:00 0 
b6a6b000-b6a72000 r-xp 00000000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a72000-b6a73000 r--p 00006000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a73000-b6a74000 rw-p 00007000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a74000-b6ac1000 r-xp 00000000 08:01 5712516    /usr/lib/libXt.so.6.0.0
b6ac1000-b6ac5000 rw-p 0004c000 08:01 5712516    /usr/lib/libXt.so.6.0.0
b6ac5000-b6adb000 r-xp 00000000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6adb000-b6adc000 r--p 00015000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6adc000-b6add000 rw-p 00016000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6add000-b6ae7000 r-xp 00000000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ae7000-b6ae8000 r--p 00009000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ae8000-b6ae9000 rw-p 0000a000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ae9000-b6af2000 r-xp 00000000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6af2000-b6af3000 r--p 00008000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6af3000-b6af4000 rw-p 00009000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6af4000-b6b09000 r-xp 00000000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6b09000-b6b0a000 r--p 00014000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6b0a000-b6b0b000 rw-p 00015000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6b0b000-b6b0d000 rw-p b6b0b000 00:00 0 
b6b0f000-b6b12000 r-xp 00000000 08:01 5734766    /usr/lib/ao/plugins-2/libalsa09.so
b6b12000-b6b14000 rw-p 00002000 08:01 5734766    /usr/lib/ao/plugins-2/libalsa09.so
b6b14000-b6b16000 r-xp 00000000 08:01 5734770    /usr/lib/ao/plugins-2/liboss.so
b6b16000-b6b18000 rw-p 00001000 08:01 5734770    /usr/lib/ao/plugins-2/liboss.so
b6b18000-b6b1b000 r-xp 00000000 08:01 4161578    /lib/libcap.so.1.10
b6b1b000-b6b1c000 rw-p 00002000 08:01 4161578    /lib/libcap.so.1.10
b6b1c000-b6b1e000 r-xp 00000000 08:01 5734771    /usr/lib/ao/plugins-2/libpulse.so
b6b1e000-b6b20000 rw-p 00001000 08:01 5734771    /usr/lib/ao/plugins-2/libpulse.so
b6b20000-b6b23000 rw-p b6b20000 00:00 0 
b6b23000-b6b27000 r-xp 00000000 08:01 5712486    /usr/lib/libXdmcp.so.6.0.0
b6b27000-b6b28000 rw-p 00003000 08:01 5712486    /usr/lib/libXdmcp.so.6.0.0
b6b28000-b6b3f000 r-xp 00000000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6b3f000-b6b40000 r--p 00016000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6b40000-b6b41000 rw-p 00017000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6b41000-b6b42000 r-xp 00000000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b42000-b6b43000 r--p 00000000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b43000-b6b44000 rw-p 00001000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b44000-b6b46000 r-xp 00000000 08:01 5712475    /usr/lib/libXau.so.6.0.0
b6b46000-b6b47000 rw-p 00001000 08:01 5712475    /usr/lib/libXau.so.6.0.0
b6b47000-b6b4e000 r-xp 00000000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b4e000-b6b4f000 r--p 00007000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b4f000-b6b50000 rw-p 00008000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b50000-b6b51000 rw-p b6b50000 00:00 0 
b6b51000-b6c3c000 r-xp 00000000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6c3c000-b6c3d000 r--p 000ea000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6c3d000-b6c3f000 rw-p 000eb000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6c3f000-b6c40000 rw-p b6c3f000 00:00 0 
b6c40000-b6c4d000 r-xp 00000000 08:01 5712490    /usr/lib/libXext.so.6.4.0
b6c4d000-b6c4f000 rw-p 0000c000 08:01 5712490    /usr/lib/libXext.so.6.4.0
b6c4f000-b6c50000 r-xp 00000000 08:01 213521     /usr/lib/tls/libnvidia-tls.so.177.80
b6c50000-b6c51000 rw-p 00000000 08:01 213521     /usr/lib/tls/libnvidia-tls.so.177.80
b6c51000-b7814000 r-xp 00000000 08:01 5711489    /usr/lib/libGLcore.so.177.80
b7814000-b79b8000 rwxp 00bc3000 08:01 5711489    /usr/lib/libGLcore.so.177.80
b79b8000-b79c3000 rwxp b79b8000 00:00 0 
b79c3000-b79d6000 r-xp 00000000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b79d6000-b79d7000 r--p 00012000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b79d7000-b79d8000 rw-p 00013000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b79d8000-b79df000 r-xp 00000000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b79df000-b79e0000 r--p 00006000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b79e0000-b79e1000 rw-p 00007000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b79e1000-b79e2000 rw-p b79e1000 00:00 0 
b79e2000-b7a46000 r-xp 00000000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a46000-b7a47000 r--p 00063000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a47000-b7a48000 rw-p 00064000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a48000-b7a4a000 r-xp 00000000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a4a000-b7a4b000 r--p 00001000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a4b000-b7a4c000 rw-p 00002000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a4c000-b7b0f000 r-xp 00000000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7b0f000-b7b11000 r--p 000c2000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7b11000-b7b14000 rw-p 000c4000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7b14000-b7b29000 r-xp 00000000 08:01 4179315    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b29000-b7b2a000 r--p 00014000 08:01 4179315    /lib/tls/i686/cmov/libpAborted
~$ sudo zsnes
[sudo] password for ColeJayStooks: 
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: Logitech Trackball
Mouse 1: Macintosh mouse button emulation
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7be7558]
/lib/tls/i686/cmov/libc.so.6[0xb7be5680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 5711498    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 5711498    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 5711498    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
0a260000-0a2d3000 rw-p 0a260000 00:00 0          [heap]
b5d6a000-b6878000 rw-p b5d6a000 00:00 0 
b6878000-b68a0000 r-xp 00000000 08:01 4161648    /lib/libpcre.so.3.12.1
b68a0000-b68a1000 r--p 00027000 08:01 4161648    /lib/libpcre.so.3.12.1
b68a1000-b68a2000 rw-p 00028000 08:01 4161648    /lib/libpcre.so.3.12.1
b68a2000-b6957000 r-xp 00000000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6957000-b6958000 r--p 000b4000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6958000-b6959000 rw-p 000b5000 08:01 5712668    /usr/lib/libglib-2.0.so.0.1800.2
b6959000-b695d000 r-xp 00000000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b695d000-b695e000 r--p 00003000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b695e000-b695f000 rw-p 00004000 08:01 5713444    /usr/lib/libgthread-2.0.so.0.1800.2
b6971000-b6972000 rw-p b6971000 00:00 0 
b6972000-b69c0000 r-xp 00000000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b69c0000-b69c1000 r--p 0004d000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b69c1000-b69c2000 rw-p 0004e000 08:01 5713247    /usr/lib/libpulse.so.0.4.1
b69c2000-b69ce000 r-xp 00000000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b69ce000-b69cf000 r--p 0000b000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b69cf000-b69d0000 rw-p 0000c000 08:01 5713245    /usr/lib/libpulse-simple.so.0.0.1
b69d4000-b69d7000 r-xp 00000000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b69d7000-b69d8000 r--p 00002000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b69d8000-b69d9000 rw-p 00003000 08:01 5713437    /usr/lib/libgmodule-2.0.so.0.1800.2
b69d9000-b69de000 r-xp 00000000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b69de000-b69df000 r--p 00004000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b69df000-b69e0000 rw-p 00005000 08:01 5713708    /usr/lib/libartsc.so.0.0.0
b69e0000-b69e1000 r-xp 00000000 08:01 5734767    /usr/lib/ao/plugins-2/libarts.so
b69e1000-b69e3000 rw-p 00000000 08:01 5734767    /usr/lib/ao/plugins-2/libarts.so
b69e3000-b6a05000 r-xp 00000000 08:01 5712559    /usr/lib/libaudiofile.so.0.0.2
b6a05000-b6a08000 rw-p 00021000 08:01 5712559    /usr/lib/libaudiofile.so.0.0.2
b6a08000-b6a11000 r-xp 00000000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a11000-b6a12000 r--p 00008000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a12000-b6a13000 rw-p 00009000 08:01 5712716    /usr/lib/libesd.so.0.2.39
b6a13000-b6a28000 r-xp 00000000 08:01 5712434    /usr/lib/libICE.so.6.3.0
b6a28000-b6a29000 rw-p 00014000 08:01 5712434    /usr/lib/libICE.so.6.3.0
b6a29000-b6a2b000 rw-p b6a29000 00:00 0 
b6a2b000-b6a32000 r-xp 00000000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a32000-b6a33000 r--p 00006000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a33000-b6a34000 rw-p 00007000 08:01 5712463    /usr/lib/libSM.so.6.0.0
b6a34000-b6a81000 r-xp 00000000 08:01 5712516    /usr/lib/libXt.so.6.0.0
b6a81000-b6a85000 rw-p 0004c000 08:01 5712516    /usr/lib/libXt.so.6.0.0
b6a85000-b6a9b000 r-xp 00000000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6a9b000-b6a9c000 r--p 00015000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6a9c000-b6a9d000 rw-p 00016000 08:01 5713710    /usr/lib/libaudio.so.2.4
b6a9d000-b6aa7000 r-xp 00000000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6aa7000-b6aa8000 r--p 00009000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6aa8000-b6aa9000 rw-p 0000a000 08:01 4179306    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6aa9000-b6ab2000 r-xp 00000000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6ab2000-b6ab3000 r--p 00008000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6ab3000-b6ab4000 rw-p 00009000 08:01 4179310    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6ab4000-b6ac9000 r-xp 00000000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6ac9000-b6aca000 r--p 00014000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6aca000-b6acb000 rw-p 00015000 08:01 4179300    /lib/tls/i686/cmov/libnsl-2.8.90.so
b6acb000-b6acd000 rw-p b6acb000 00:00 0 
b6acf000-b6ad2000 r-xp 00000000 08:01 5734766    /usr/lib/ao/plugins-2/libalsa09.so
b6ad2000-b6ad4000 rw-p 00002000 08:01 5734766    /usr/lib/ao/plugins-2/libalsa09.so
b6ad4000-b6ad6000 r-xp 00000000 08:01 5734770    /usr/lib/ao/plugins-2/liboss.so
b6ad6000-b6ad8000 rw-p 00001000 08:01 5734770    /usr/lib/ao/plugins-2/liboss.so
b6ad8000-b6adb000 r-xp 00000000 08:01 4161578    /lib/libcap.so.1.10
b6adb000-b6adc000 rw-p 00002000 08:01 4161578    /lib/libcap.so.1.10
b6adc000-b6ade000 r-xp 00000000 08:01 5734771    /usr/lib/ao/plugins-2/libpulse.so
b6ade000-b6ae0000 rw-p 00001000 08:01 5734771    /usr/lib/ao/plugins-2/libpulse.so
b6ae0000-b6ae3000 rw-p b6ae0000 00:00 0 
b6ae3000-b6ae7000 r-xp 00000000 08:01 5712486    /usr/lib/libXdmcp.so.6.0.0
b6ae7000-b6ae8000 rw-p 00003000 08:01 5712486    /usr/lib/libXdmcp.so.6.0.0
b6ae8000-b6aff000 r-xp 00000000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6aff000-b6b00000 r--p 00016000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6b00000-b6b01000 rw-p 00017000 08:01 5713419    /usr/lib/libxcb.so.1.0.0
b6b01000-b6b02000 r-xp 00000000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b02000-b6b03000 r--p 00000000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b03000-b6b04000 rw-p 00001000 08:01 5713417    /usr/lib/libxcb-xlib.so.0.0.0
b6b04000-b6b06000 r-xp 00000000 08:01 5712475    /usr/lib/libXau.so.6.0.0
b6b06000-b6b07000 rw-p 00001000 08:01 5712475    /usr/lib/libXau.so.6.0.0
b6b07000-b6b0e000 r-xp 00000000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b0e000-b6b0f000 r--p 00007000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b0f000-b6b10000 rw-p 00008000 08:01 4179319    /lib/tls/i686/cmov/librt-2.8.90.so
b6b10000-b6b11000 rw-p b6b10000 00:00 0 
b6b11000-b6bfc000 r-xp 00000000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6bfc000-b6bfd000 r--p 000ea000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6bfd000-b6bff000 rw-p 000eb000 08:01 5712469    /usr/lib/libX11.so.6.2.0
b6bff000-b6c00000 rw-p b6bff000 00:00 0 
b6c00000-b6c0d000 r-xp 00000000 08:01 5712490    /usr/lib/libXext.so.6.4.0
b6c0d000-b6c0f000 rw-p 0000c000 08:01 5712490    /usr/lib/libXext.so.6.4.0
b6c0f000-b6c10000 r-xp 00000000 08:01 213521     /usr/lib/tls/libnvidia-tls.so.177.80
b6c10000-b6c11000 rw-p 00000000 08:01 213521     /usr/lib/tls/libnvidia-tls.so.177.80
b6c11000-b77d4000 r-xp 00000000 08:01 5711489    /usr/lib/libGLcore.so.177.80
b77d4000-b7978000 rwxp 00bc3000 08:01 5711489    /usr/lib/libGLcore.so.177.80
b7978000-b7983000 rwxp b7978000 00:00 0 
b7983000-b7996000 r-xp 00000000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b7996000-b7997000 r--p 00012000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b7997000-b7998000 rw-p 00013000 08:01 5712672    /usr/lib/libdirect-1.0.so.0.1.0
b7998000-b799f000 r-xp 00000000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b799f000-b79a0000 r--p 00006000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b79a0000-b79a1000 rw-p 00007000 08:01 5712750    /usr/lib/libfusion-1.0.so.0.1.0
b79a1000-b79a2000 rw-p b79a1000 00:00 0 
b79a2000-b7a06000 r-xp 00000000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a06000-b7a07000 r--p 00063000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a07000-b7a08000 rw-p 00064000 08:01 5712674    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a08000-b7a0a000 r-xp 00000000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a0a000-b7a0b000 r--p 00001000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a0b000-b7a0c000 rw-p 00002000 08:01 4179295    /lib/tls/i686/cmov/libdl-2.8.90.so
b7a0c000-b7acf000 r-xp 00000000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7acf000-b7ad1000 r--p 000c2000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7ad1000-b7ad4000 rw-p 000c4000 08:01 5712549    /usr/lib/libasound.so.2.0.0
b7ad4000-b7ae9000 r-xp 00000000 08:01 4179315    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7ae9000-b7aea000 r--p 00014000 08:01 4179315    /lib/tls/i686/cmov/libpAborted
~$ 
```

is there a way to know my drivers are activated? i can turn on the special desktop effects but they distract me lol and that's about all i know... also, anyone know whats over buffering or what is going on? thanks in advance!

---

### Post by jimmy the saint on 2008-11-16
Have you tried uninstalling it then reinstlling it?  Use synaptic and make sure you choose to "completely remove" the app, which will also eliminate any config files.

---

### Post by nhasian on 2008-11-16
actually the one in the repos doesnt work.  it did with hardy, but something ibex broke it.  this version does work with 8.10 Intrepid Ibex:

[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)

---

### Post by ColeJayStooks on 2008-11-16
ok i'm doing that now but i'm going to try another solution as it purges and reinstalls

i installed snes9express and for the most part it seems like it would work out except two or three things...

for one, when i want to play the games in full screen, they won't go full screen and when i exit the game i get this message:

```
snes9x -scale -hires -fullscreen -j "/home/coleman/Documents/rom/SNES/06 - Secret of Mana.smc"
Reading config file /etc/snes9x/snes9x.conf
joystick: No joystick found.
Can't open "/dev/mem", full screen mode not available: Permission denied
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

      after 519 requests (517 known processed) with 0 events remaining.

Controller Port 1: Pad 1
Controller Port 2: <none>
Rate: 22050, Buffer size: 2048, 16-bit: yes, Stereo: yes, Encoded: no
No ROM file header found.
"Secret of MANA" [checksum ok] HiROM, 16Mbits, Type: ROM+RAM+BAT, Mode: 21, TV: NTSC, S-RAM: 8KB, ROMId: ? Company: C3 CRC32: D0176B24

snes9x returned error code 1
```

i turned off joystick support because that leads to the next question (but "error code 1" doesn't help out the full screen issue)

i have a playstation 2 controller going through a usb hub thing, and for llinux installs in the past, has always worked out. now it's not doing so hot.

under "Controllers" i tick "Use Joystick" on and then the configure button. it tells me it can't find the joystick. so i press the "Devices..." button and redirect "/dev/js0" to "/dev/input/js0", which i can then configure through the "Configure Button Maps..." button. then, i try and run a game and this happens:

```
snes9x -scale -hires -fullscreen -joydev1 /dev/input/js0 -joymap1 1 2 0 3 6 7 8 9 -joydev2 /dev/input/js1 "/home/coleman/Documents/rom/SNES/06 - Secret of Mana.smc"
snes9x: S9xUsage: snes9x <options> <rom image filename>

Where <options> can be:

-sound or -so                   Enable digital sound output
-nosound or -ns                 Disable digital sound output
-soundskip or -sk <0-3>         Sound CPU skip-waiting method
-soundquality, -sq, or -r <num> Set sound playback quality
                                  0 - off, 1 - 8192, 2 - 11025, 3 - 16500,
                                  4 - 22050 (default), 5 - 29300, 6 - 36600,
                                  7 - 44000
-altsampledecode or -alt        Use alternate sample decoder
-stereo or -st                  Enable stereo sound output (implies -sound)
-mono                           Enable monaural sound output (implies -sound)
-soundsync or -sy               Enable sound sync to CPU at startup
-soundsync2 or -sy2             Alternate method to sync sound
-threadsound or -ts             Use a separate thread to output sound
-interpolatedsound or -is <0-3> Select sound interpolation method
                     Reading config file /etc/snes9x/snes9x.conf
             0=none, 1=linear, 2=cubic, 3=gaussian
-echo or -e                     Enable DSP echo effects at startup
-noecho or -ne                  Disable DSP echo effects at startup
-envx or -ex                    Enable volume envelope height reading
-nosamplecaching, -nsc, or -nc  Disable sample caching
-nomastervolume or -nmv         Disable master volume setting
-fix                            'Fix' sound frequencies

-conf <filename>                Use specified conf file (after standard files)
-nostdconf                      Do not load the standard config files
-hdma or -ha                    Enable HDMA emulation at startup
-nohdma or -nh                  Disable HDMA emulation at startup
-transparency or -tr            Enable transparency effects
-notransparency or -nt          Disable transparency effects at start
-windows                        Enable graphic window effects
-nowindows or -nw               Disable graphic window effects
-im7                            Enable Mode 7 interpolation effects
-displayframerate or -dfr       Display the frame rate counter
-aidoshm <shmid>                Run in AIDO mode, with specified SHM ID

-hires or -hi                   Enable support for hi-res and interlace modes
-frameskip or -f <num>          Screen update frame skip rate
-frametime or -ft <float>       Milliseconds per frame for frameskip auto-adjust

-hirom, -hr, or -fh             Force Hi-ROM memory map
-lorom, -lr, or -fl             Force Lo-ROM memory map
-bs                             Use BS Satellite System ROM mapping
-bsxbootup                      Boot up BS games from BS-X
-nointerleave or -ni            ROM image is not in interleaved format
-interleaved or -i              ROM image is in interleaved format
-interleaved2 or -i2            ROM image is in interleaved 2 format
-interleavedgd24 or -gd24       ROM image is in interleaved gd24 format
-header, -he, or -hd            Force the detection of a ROM image header
-noheader or -nhd               Force the detection of no ROM image header
-ntsc or -n                     Force NTSC timing (60 frames/sec)
-pal or -p                      Force PAL timing (50 frames/sec)
-superfx or -sfx                Force detection of the SuperFX chip
-nosuperfx or -nosfx            Force detection of no SuperFX chip
-dsp1                           Force detection of the DSP-1 chip
-nodsp1                         Force detection of no DSP-1 chip

-nopatch                        Do not apply any available IPS patches
-cheat                          Apply saved cheats
-nocheat                        Do not apply saved cheats
-gamegenie or -gg <code>        Supply a Game Genie code
-actionreplay or -ar <code>     Supply a Pro-Action Reply code
-goldfinger or -gf <code>       Supply a Gold Finger code

-nomp5                          Disable emulation of the Multiplayer 5 adapter
-nomouse                        Disable emulation of the SNES mouse
-nosuperscope                   Disable emulation of the Superscope
-nojustifier                    Disable emulation of the Konami Justifier
-port# <control>                Specify which controller to emulate in port 1/2
      Controllers: none            No controller
                   pad#            Joypad number 1-8
                   mouse#          Mouse number 1-2
                   superscope      Superscope (not useful with -port1)
                   justifier       Blue Justifier (not useful with -port1)
                   one-justifier   ditto
                   two-justifiers  Blue & Pink Justifiers
                   mp5:####        MP5 with the 4 named pads (1-8 or n)

-net                            Enable netplay
-port or -po <num>              Use port <num> for netplay
-server or -srv <string>        Use the specified server for netplay

-nojoy or -j                    Disable joystick reading
-joydev1 <string>               Specify joysick device 1
-joydev2 <string>               Specify joysick device 2
-joydev3 <string>               Specify joysick device 3
-joydev4 <string>               Specify joysick device 4
-buffersize, -bs, or -b <num>   Sound playback buffer size in bytes
-loadsnapshot <file>            Load snapshot file at start
-sdd1-pack <file>               Use named S-DD1 graphics pack

-set-repeat or -no-set-repeat   Whether to allow altering keyboard auto-repeat
-y or -y1                       Enable 'TV mode' (implies -16 -hires -tr)
-y2                             Enable Kreed's Super 2xSaI image processing
-y3                             Enable Kreed's Super Eagle image processing
-y4                             Enable Kreed's 2xSaI image processing
-y5                             Enable Kreed's software bi-linear filtering
-GUI.interpolate<num>           Same as -y<num>
-scale or -sc                   Scale image to fit window
-nomodeswitch or -nms           Don't switch modes in fullscreen mode
-fullscreen or -fs              Begin in fullscreen mode

ROM image needs to be in Super MagiCom (*.smc), Super FamiCom (*.sfc),
*.fig, or split (*.1, *.2, or sf32527a, sf32527b, etc) format and can be
compressed with zip, gzip, or compress.

snes9x returned error code 1
```

ends up not running the game at all. :(

OH AND BTW i completely removed and reinstalled zsnes through all this typing... still comes up with the same errors. :(

---

### Post by ColeJayStooks on 2008-11-16
> **nhasian said:**
> actually the one in the repos doesnt work.  it did with hardy, but something ibex broke it.  this version does work with 8.10 Intrepid Ibex:

[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)

weird... i first tried the pentium4 tar because that's my processor... there wasn't a source but there was a zsnes executable so i ran it and it ran almost excellently (anytime i did frame rate skipping through the ~ button the audio and game wouldn't be synced, so when mario jumped or something you'd hear it a few seconds later)...

so i take the source package, install that and... still the same errors as before.

would there be any way to make the pentium4 tar installable?

---

### Post by ColeJayStooks on 2008-11-17
bump because i am still stuck 	:-k

---

### Post by nhasian on 2008-11-18
I just unpacked the archive and ran the executable.  it worked fine for me on a core2duo processor except i couldnt figure out how to install a microsoft 360 gamepad... but thats another issue altogether :)

> **ColeJayStooks said:**
> would there be any way to make the pentium4 tar installable?

---

### Post by likemindead on 2008-11-20
Yup. Have to use the older version that was linked above, for now. Hopefully the latest ZSNES will be fixed to work with 8.10 soon enough.

---

### Post by likemindead on 2008-11-30
Any idea when the latest ZSNES will work with Ibex?

---

