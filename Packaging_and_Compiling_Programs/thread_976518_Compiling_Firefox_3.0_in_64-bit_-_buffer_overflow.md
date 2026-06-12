---
title: "Compiling Firefox 3.0 in 64-bit - buffer overflow?"
date: 2008-11-09
forum: Packaging and Compiling Programs
---

### Post by Sealbhach on 2008-11-09
Hi, I've been following this guide here:

[http://ubuntu-snippets.blogspot.com/2008/07/build-firefox-3-web-browser-with-jssh.html](http://ubuntu-snippets.blogspot.com/2008/07/build-firefox-3-web-browser-with-jssh.html)

and it seemed to compile the thing OK, but when I try the command to run it:

./mozilla/firefox-jssh/dist/bin/firefox -jssh


it doesn't launch and I get this message in the terminal:

```
*** buffer overflow detected ***: ./mozilla/firefox-jssh/dist/bin/firefox-bin terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f09c9243887]
/lib/libc.so.6[0x7f09c9241750]
/lib/libc.so.6[0x7f09c9241e0b]
./mozilla/firefox-jssh/dist/bin/libxul.so(XRE_GetBinaryPath+0x4d)[0x7f09cd6ac2c7]
./mozilla/firefox-jssh/dist/bin/firefox-bin[0x400e9e]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f09c9162466]
./mozilla/firefox-jssh/dist/bin/firefox-bin[0x400cf9]
======= Memory map: ========
00400000-00402000 r-xp 00000000 08:05 1167949                            /home/oliver/mozilla/firefox-jssh/dist/bin/firefox-bin
00602000-00603000 r--p 00002000 08:05 1167949                            /home/oliver/mozilla/firefox-jssh/dist/bin/firefox-bin
00603000-00604000 rw-p 00003000 08:05 1167949                            /home/oliver/mozilla/firefox-jssh/dist/bin/firefox-bin
7f09c4c00000-7f09c4d00000 rw-p 7f09c4c00000 00:00 0 
7f09c4d15000-7f09c4d1a000 r-xp 00000000 08:02 172630                     /usr/lib/libXdmcp.so.6.0.0
7f09c4d1a000-7f09c4f19000 ---p 00005000 08:02 172630                     /usr/lib/libXdmcp.so.6.0.0
7f09c4f19000-7f09c4f1a000 rw-p 00004000 08:02 172630                     /usr/lib/libXdmcp.so.6.0.0
7f09c4f1a000-7f09c4f1c000 r-xp 00000000 08:02 172619                     /usr/lib/libXau.so.6.0.0
7f09c4f1c000-7f09c511b000 ---p 00002000 08:02 172619                     /usr/lib/libXau.so.6.0.0
7f09c511b000-7f09c511c000 rw-p 00001000 08:02 172619                     /usr/lib/libXau.so.6.0.0
7f09c511c000-7f09c5124000 r-xp 00000000 08:02 226810                     /lib/librt-2.8.90.so
7f09c5124000-7f09c5323000 ---p 00008000 08:02 226810                     /lib/librt-2.8.90.so
7f09c5323000-7f09c5324000 r--p 00007000 08:02 226810                     /lib/librt-2.8.90.so
7f09c5324000-7f09c5325000 rw-p 00008000 08:02 226810                     /lib/librt-2.8.90.so
7f09c5325000-7f09c533c000 r-xp 00000000 08:02 172578                     /usr/lib/libICE.so.6.3.0
7f09c533c000-7f09c553b000 ---p 00017000 08:02 172578                     /usr/lib/libICE.so.6.3.0
7f09c553b000-7f09c553d000 rw-p 00016000 08:02 172578                     /usr/lib/libICE.so.6.3.0
7f09c553d000-7f09c5540000 rw-p 7f09c553d000 00:00 0 
7f09c5540000-7f09c5548000 r-xp 00000000 08:02 172607                     /usr/lib/libSM.so.6.0.0
7f09c5548000-7f09c5747000 ---p 00008000 08:02 172607                     /usr/lib/libSM.so.6.0.0
7f09c5747000-7f09c5748000 r--p 00007000 08:02 172607                     /usr/lib/libSM.so.6.0.0
7f09c5748000-7f09c5749000 rw-p 00008000 08:02 172607                     /usr/lib/libSM.so.6.0.0
7f09c5749000-7f09c574a000 r-xp 00000000 08:02 173563                     /usr/lib/libxcb-xlib.so.0.0.0
7f09c574a000-7f09c5949000 ---p 00001000 08:02 173563                     /usr/lib/libxcb-xlib.so.0.0.0
7f09c5949000-7f09c594a000 r--p 00000000 08:02 173563                     /usr/lib/libxcb-xlib.so.0.0.0
7f09c594a000-7f09c594b000 rw-p 00001000 08:02 173563                     /usr/lib/libxcb-xlib.so.0.0.0
7f09c594b000-7f09c5973000 r-xp 00000000 08:02 226800                     /lib/libpcre.so.3.12.1
7f09c5973000-7f09c5b72000 ---p 00028000 08:02 226800                     /lib/libpcre.so.3.12.1
7f09c5b72000-7f09c5b73000 r--p 00027000 08:02 226800                     /lib/libpcre.so.3.12.1
7f09c5b73000-7f09c5b74000 rw-p 00028000 08:02 226800                     /lib/libpcre.so.3.12.1
7f09c5b74000-7f09c5b8f000 r-xp 00000000 08:02 173565                     /usr/lib/libxcb.so.1.0.0
7f09c5b8f000-7f09c5d8e000 ---p 0001b000 08:02 173565                     /usr/lib/libxcb.so.1.0.0
7f09c5d8e000-7f09c5d8f000 r--p 0001a000 08:02 173565                     /usr/lib/libxcb.so.1.0.0
7f09c5d8f000-7f09c5d90000 rw-p 0001b000 08:02 173565                     /usr/lib/libxcb.so.1.0.0
7f09c5d90000-7f09c5d97000 r-xp 00000000 08:02 173561                     /usr/lib/libxcb-render.so.0.0.0
7f09c5d97000-7f09c5f97000 ---p 00007000 08:02 173561                     /usr/lib/libxcb-render.so.0.0.0
7f09c5f97000-7f09c5f98000 r--p 00007000 08:02 173561                     /usr/lib/libxcb-render.so.0.0.0
7f09c5f98000-7f09Aborted

```

Anyone got a link to a guide on compiling Firefox 3.x in Intrepid 64-bit?




.

---

### Post by Sealbhach on 2008-11-10
*bump* 

Anyone know what this buffer overflow" might be?

The normal Firefox in the repos runs fine. I was wondering if it was because I extracted the tar in my /home folder.

Do I need to link the executable to /usr/bin or something?


.

---

### Post by TylerRick on 2008-11-11
I'm experiencing the exact same problem. Also on Ubuntu 8.10 64-bit...

I hate it when this happens and I have no idea what to try next. Maybe we shouldn't be pulling the latest from cvs but should be compiling the same version that's in the repos (Firefox 3.0.3)?

---

### Post by brianmrowe on 2009-02-15
I have the same problem compiling for 8.10 on 32bit.  I wish I could fix it, but I don't think I can...
I do want to look at not trying to compile latest.  I'll post if that works.



/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb68496d8]
/lib/tls/i686/cmov/libc.so.6[0xb6847800]
/lib/tls/i686/cmov/libc.so.6[0xb6847f68]
./firefox-jssh/dist/bin/libxul.so(XRE_GetBinaryPath+0x55)[0xb748e5ba]
./firefox-jssh/dist/bin/firefox-bin[0x8048b34]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6765685]
./firefox-jssh/dist/bin/firefox-bin[0x8048a21]
======= Memory map: ========
08048000-0804a000 r-xp 00000000 08:01 12096999   /home/browe/src/mozilla/firefox-jssh/dist/bin/firefox-bin
0804a000-0804b000 r--p 00001000 08:01 12096999   /home/browe/src/mozilla/firefox-jssh/dist/bin/firefox-bin
0804b000-0804c000 rw-p 00002000 08:01 12096999   /home/browe/src/mozilla/firefox-jssh/dist/bin/firefox-bin
b6200000-b6300000 rw-p b6200000 00:00 0 
b6381000-b6385000 rw-p b6381000 00:00 0 
b6385000-b6389000 r-xp 00000000 08:01 31605785   /usr/lib/libXdmcp.so.6.0.0
b6389000-b638a000 rw-p 00003000 08:01 31605785   /usr/lib/libXdmcp.so.6.0.0
b638a000-b638c000 r-xp 00000000 08:01 31605396   /usr/lib/libXau.so.6.0.0
b638c000-b638d000 rw-p 00001000 08:01 31605396   /usr/lib/libXau.so.6.0.0
b638d000-b6394000 r-xp 00000000 08:01 18989347   /lib/tls/i686/cmov/librt-2.8.90.so
b6394000-b6395000 r--p 00007000 08:01 18989347   /lib/tls/i686/cmov/librt-2.8.90.so
b6395000-b6396000 rw-p 00008000 08:01 18989347   /lib/tls/i686/cmov/librt-2.8.90.so
b6396000-b6397000 rw-p b6396000 00:00 0 
b6397000-b63ac000 r-xp 00000000 08:01 31606310   /usr/lib/libICE.so.6.3.0
b63ac000-b63ad000 rw-p 00014000 08:01 31606310   /usr/lib/libICE.so.6.3.0
b63ad000-b63af000 rw-p b63ad000 00:00 0 
b63af000-b63b6000 r-xp 00000000 08:01 34504980   /usr/lib/libSM.so.6.0.0
b63b6000-b63b7000 r--p 00006000 08:01 34504980   /usr/lib/libSM.so.6.0.0
b63b7000-b63b8000 rw-p 00007000 08:01 34504980   /usr/lib/libSM.so.6.0.0
b63b8000-b63b9000 r-xp 00000000 08:01 31607096   /usr/lib/libxcb-xlib.so.0.0.0
b63b9000-b63ba000 r--p 00000000 08:01 31607096   /usr/lib/libxcb-xlib.so.0.0.0
b63ba000-b63bb000 rw-p 00001000 08:01 31607096   /usr/lib/libxcb-xlib.so.0.0.0
b63bb000-b63e3000 r-xp 00000000 08:01 18989131   /lib/libpcre.so.3.12.1
b63e3000-b63e4000 r--p 00027000 08:01 18989131   /lib/libpcre.so.3.12.1
b63e4000-b63e5000 rw-p 00028000 08:01 18989131   /lib/libpcre.so.3.12.1
b63e5000-b63e6000 rw-p b63e5000 00:00 0 
b63e6000-b63fd000 r-xp 00000000 08:01 31605810   /usr/lib/libxcb.so.1.0.0
b63fd000-b63fe000 r--p 00016000 08:01 31605810   /usr/lib/libxcb.so.1.0.0
b63fe000-b63ff000 rw-p 00017000 08:01 31605810   /usr/lib/libxcb.so.1.0.0
b63ff000-b6405000 r-xp 00000000 08:01 31607014   /usr/lib/libxcb-render.so.0.0.0
b6405000-b6406000 r--p 00005000 08:01 31607014   /usr/lib/libxcb-render.so.0.0.0
b6406000-b6407000 rw-p 00006000 08:01 31607014   /usr/lib/libxcb-render.so.0.0.0
b6407000-b640a000 r-xp 00000000 08:01 31608238   /usr/lib/libxcb-render-util.so.0.0.0
b640a000-b640b000 r--p 00002000 08:01 31608238   /usr/lib/libxcb-render-util.so.0.0.0
b640b000-b640c000 rw-p 00003000 08:01 31608238   /usr/lib/libxcb-render-util.so.0.0.0
b640c000-b6430000 r-xp 00000000 08:01 34504960   /usr/lib/libpng12.so.0.27.0
b6430000-b6432000 rw-p 00023000 08:01 34504960   /usr/lib/libpng12.so.0.27.0
b6432000-b6471000 r-xp 00000000 08:01 31608230   /usr/lib/libpixman-1.so.0.12.0
b6471000-b6473000 r--p 0003e000 08:01 31608230   /usr/lib/libpixman-1.so.0.12.0
b6473000-b6474000 rw-p 00040000 08:01 31608230   /usr/lib/libpixman-1.so.0.12.0
b6474000-b6475000 rw-p b6474000 00:00 0 
b6475000-b648d000 r-xp 00000000 08:01 18989101   /lib/libselinux.so.1
b648d000-b648e000 r--p 00017000 08:01 18989101   /lib/libselinux.so.1
b648e000-b648f000 rw-p 00018000 08:01 18989101   /lib/libselinux.so.1
b648f000-b6497000 r-xp 00000000 08:01 31606353   /usr/lib/libXcursor.so.1.0.2
b6497000-b6498000 rw-p 00007000 08:01 31606353   /usr/lib/libXcursor.so.1.0.2
b6498000-b649d000 r-xp 00000000 08:01 34504997   /usr/lib/libXrandr.so.2.1.0
b649d000-b649e000 r--p 0000Aborted

---

### Post by thomasalbright on 2009-03-25
I'm having the same problem on Intrepid.  I've tried both Firefox 3.0.6 and 3.0.7, and neither worked.  However, I was able to compile and use 'Minefield', the beta of Firefox 3.1, without any buffer overruns.

Has anyone had any luck yet with Firefox 3.0?

---

### Post by Sjord on 2009-04-02
[URL="https://bugs.launchpad.net/bugs/325039"]Bug #325039:
Firefox 3.0.5 compilation success, but launching app, buffer overflow falls out[/URL]

---

### Post by cl333r on 2009-05-03
Ah I don't know what's the matter but here on Jaunty 64 I still got same issue.

---

### Post by gastly on 2009-06-12
I have the exact same issue on a custom build too! And I'm on a 32-bit machine.

---

### Post by asac on 2009-06-15
you need a patch to prevent gcc stack protection to kick in.

Try the debian/patches/bz412610_att335369_realpath_overflow.patch from the xulrunner-1.9 package.

FWIW, for mozilla related questions its always good to visit #ubuntu-mozillateam on freenode.

---

