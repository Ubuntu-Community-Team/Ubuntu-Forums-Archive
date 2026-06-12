---
title: "Problems when compiling on Ubuntu Linux"
date: 2009-03-07
forum: Packaging and Compiling Programs
---

### Post by Oluwajobi on 2009-03-07
Hi, Everyone,

While compiling a software, l encountered some little problems ;

Problem 1:

*** buffer overflow detected ***: ./program1 terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c696d8]
/lib/tls/i686/cmov/libc.so.6[0xb7c67800]
/lib/tls/i686/cmov/libc.so.6[0xb7c66ef8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb7bdca78]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xf4a)[0xb7baf90a]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb7c66fa4]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb7c66eed]
./aline[0x80654ea]
./aline[0x80656a1]
./aline[0x8067741]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7b85685]
./aline[0x8049c51]
======= Memory map: ========
08048000-0806d000 r-xp 00000000 08:01 2203989    /home/bart/Progs/aline
0806d000-0806e000 r--p 00024000 08:01 2203989    /home/bart/Progs/aline
0806e000-0806f000 rw-p 00025000 08:01 2203989    /home/bart/Progs/aline
0806f000-0807a000 rw-p 0806f000 00:00 0 
09380000-093c1000 rw-p 09380000 00:00 0          [heap]
b7ae0000-b7aed000 r-xp 00000000 08:01 1392661    /lib/libgcc_s.so.1
b7aed000-b7aee000 r--p 0000c000 08:01 1392661    /lib/libgcc_s.so.1
b7aee000-b7aef000 rw-p 0000d000 08:01 1392661    /lib/libgcc_s.so.1
b7aef000-b7af3000 r-xp 00000000 08:01 1500744    /usr/lib/libXfixes.so.3.1.0
b7af3000-b7af4000 rw-p 00003000 08:01 1500744    /usr/lib/libXfixes.so.3.1.0
b7af4000-b7afc000 r-xp 00000000 08:01 1500764    /usr/lib/libXrender.so.1.3.0
b7afc000-b7afd000 r--p 00007000 08:01 1500764    /usr/lib/libXrender.so.1.3.0
b7afd000-b7afe000 rw-p 00008000 08:01 1500764    /usr/lib/libXrender.so.1.3.0
b7b0b000-b7b0d000 rw-p b7b0b000 00:00 0 
b7b0d000-b7b11000 r-xp 00000000 08:01 1500738    /usr/lib/libXdmcp.so.6.0.0
b7b11000-b7b12000 rw-p 00003000 08:01 1500738    /usr/lib/libXdmcp.so.6.0.0
b7b12000-b7b14000 r-xp 00000000 08:01 1500727    /usr/lib/libXau.so.6.0.0
b7b14000-b7b15000 rw-p 00001000 08:01 1500727    /usr/lib/libXau.so.6.0.0
b7b15000-b7b17000 r-xp 00000000 08:01 1409705    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b17000-b7b18000 r--p 00001000 08:01 1409705    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b18000-b7b19000 rw-p 00002000 08:01 1409705    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b19000-b7b30000 r-xp 00000000 08:01 1501671    /usr/lib/libxcb.so.1.0.0
b7b30000-b7b31000 r--p 00016000 08:01 1501671    /usr/lib/libxcb.so.1.0.0
b7b31000-b7b32000 rw-p 00017000 08:01 1501671    /usr/lib/libxcb.so.1.0.0
b7b32000-b7b33000 r-xp 00000000 08:01 1501669    /usr/lib/libxcb-xlib.so.0.0.0
b7b33000-b7b34000 r--p 00000000 08:01 1501669    /usr/lib/libxcb-xlib.so.0.0.0
b7b34000-b7b35000 rw-p 00001000 08:01 1501669    /usr/lib/libxcb-xlib.so.0.0.0
b7b35000-b7b36000 rw-p b7b35000 00:00 0 
b7b36000-b7b43000 r-xp 00000000 08:01 1500742    /usr/lib/libXext.so.6.4.0
b7b43000-b7b45000 rw-p 0000c000 08:01 1500742    /usr/lib/libXext.so.6.4.0
b7b45000-b7b4c000 r-xp 00000000 08:01 1500758    /usr/lib/libXp.so.6.2.0
b7b4c000-b7b4d000 r--p 00006000 08:01 1500758    /usr/lib/libXp.so.6.2.0
b7b4d000-b7b4e000 rw-p 00007000 08:01 1500758    /usr/lib/libXp.so.6.2.0
b7b4e000-b7b63000 r-xp 00000000 08:01 1500686    /usr/lib/libICE.so.6.3.0
b7b63000-b7b64000 rw-p 00014000 08:01 1500686    /usr/lib/libICE.so.6.3.0
b7b64000-b7b66000 rw-p b7b64000 00:00 0 
b7b66000-b7b6d000 r-xp 00000000 08:01 1500715    /usr/lib/libSM.so.6.0.0
b7b6d000-b7b6e000 r--p 00006000 08:01 1500715    /usr/lib/libSM.so.6.0.0
b7b6e000-b7b6f000 rw-p 00007000 08:01 1500715    /usr/lib/libSM.so.6.0.0
b7b6f000-b7cc7000 r-xp 00000000 08:01 1409702    /lib/tls/i686/cmov/libc-2.8.90.so
b7cc7000-b7cc9000 r--p 00158000 08:01 1409702    /lib/tls/i686/cmov/libc-2.8.90.so
b7cc9000-b7cca000 rw-p 0015a000 08:01 1409702    /lib/tls/i686/cmov/libc-2.8.90.so
b7cca000-b7ccd000 rw-p b7cca000 00:00 0 
b7ccd000-b7db8000 r-xp 00000000 08:01 1499909    /usr/lib/libX11.so.6.2.0
b7db8000-b7db9000 r--p 000ea000 08:01 1499909    /usr/lib/libX11.so.6.2.0
b7db9000-b7dbb000 rw-p 000eb000 08:01 1499909    /usr/lib/libX11.so.6.2.0
b7dbb000-b7dbc000 rw-p b7dbb000 00:00 0 
b7dbc000-b7e09000 r-xp 00000000 08:01 1500768    /usr/lib/libXt.so.6.0.0
b7e09000-b7e0d000 rw-p 0004c000 08:01 1500768    /usr/lib/libXt.so.6.0.0
b7e0d000-b7e0e000 rw-p b7e0d000 00:00 0 
b7e0e000-b7f3c000 r-xp 00000000 08:01 1501614    /usr/lib/libXm.so.2.0.1
b7f3c000-b7f3d000 r--p 0012e000 08:01 1501614    /usr/lib/libXm.so.2.0.1
b7f3d000-b7f4d000 rw-p 0012f000 08:01 1501614    /usr/lib/libXm.so.2.0.1
b7f4d000-b7f4f000 rw-p b7f4d000 00:00 0 
b7f4f000-b7f73000 r-xp 00000000 08:01 1409706    /lib/tls/i686/cmov/libm-2.8.90.so
b7f73000-b7f74000 r--p 00023000 08:01 1409706    /lib/tls/i686/cmov/libm-2.8.90.so
b7f74000-b7f75000 rw-p 00024000 08:01 1409706    /lib/tls/i686/cmov/libm-2.8.90.so
b7f78000-b7f80000 r-xp 00000000 08:01 1500734    /usr/lib/libXcursor.so.1.0.2
b7f80000-b7f81000 rw-p 00007000 08:01 1500734    /usr/lib/libXcursor.so.1.0.2
b7f81000-b7f84000 rw-p b7f81000 00:00 0 
b7f84000-b7f9e000 r-xp 00000000 08:01 1392652    /lib/ld-2.8.90.so
b7f9e000-b7f9f000 r-xp b7f9e000 00:00 0          [vdso]
b7f9f000-b7fa0000 r--p 0001a000 08:01 1392652    /lib/ld-2.8.90.so
b7fa0000-b7fa1000 rw-p 0001b000 08:01 1392652    /lib/ld-2.8.90.so
bf98b000-bf9a0000 rw-p bffeb000 00:00 0          [stack]
Aborted


Problem 2 :

<make: *** No rule to make target `program1.man', needed by `program1_man'. Stop.>


Please, how do l resolve these.

Thanks.

Jide

---

