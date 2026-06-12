---
title: "Can build but can't run Firefox"
date: 2009-03-30
forum: Programming Talk
---

### Post by cl333r on 2009-03-30
Hi folks,
Firefox compiles & builds ok with default gcc for Jaunty and Intrepid following the official instructions from Mozilla.
However I can't start it: when I try run it I get a buffer overflow (on both Jaunty and Intrepid).
Any hint why this happens? Maybe it's a gcc 4.3 issue?
The overflow happens when using both 32 & 64 bit versions of Ubuntu on my Pentium D 3.4Ghz each core (which supports x86_64).

My mozconfig:
```

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize

```

The error stack:
```

*** buffer overflow detected ***: ./firefox-bin terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f2b02b672c7]
/lib/libc.so.6[0x7f2b02b65170]
/lib/libc.so.6[0x7f2b02b6582b]
./libxul.so(XRE_GetBinaryPath+0x4d)[0x7f2b06ddda17]
./firefox-bin[0x400e8e]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f2b02a865a6]
./firefox-bin[0x400ce9]
======= Memory map: ========
00400000-00402000 r-xp 00000000 08:11 266650                             /home/fox/Desktop/firefox/firefox-bin
00602000-00603000 r--p 00002000 08:11 266650                             /home/fox/Desktop/firefox/firefox-bin
00603000-00604000 rw-p 00003000 08:11 266650                             /home/fox/Desktop/firefox/firefox-bin
7f2afdc00000-7f2afdd00000 rw-p 7f2afdc00000 00:00 0 
7f2afdd74000-7f2afdd77000 r-xp 00000000 08:11 2674                       /lib/libuuid.so.1.2
7f2afdd77000-7f2afdf77000 ---p 00003000 08:11 2674                       /lib/libuuid.so.1.2
7f2afdf77000-7f2afdf78000 r--p 00003000 08:11 2674                       /lib/libuuid.so.1.2
7f2afdf78000-7f2afdf79000 rw-p 00004000 08:11 2674                       /lib/libuuid.so.1.2
7f2afdf79000-7f2afdf7e000 r-xp 00000000 08:11 9093                       /usr/lib/libXdmcp.so.6.0.0
7f2afdf7e000-7f2afe17d000 ---p 00005000 08:11 9093                       /usr/lib/libXdmcp.so.6.0.0
7f2afe17d000-7f2afe17e000 rw-p 00004000 08:11 9093                       /usr/lib/libXdmcp.so.6.0.0
7f2afe17e000-7f2afe180000 r-xp 00000000 08:11 9082                       /usr/lib/libXau.so.6.0.0
7f2afe180000-7f2afe37f000 ---p 00002000 08:11 9082                       /usr/lib/libXau.so.6.0.0
7f2afe37f000-7f2afe380000 r--p 00001000 08:11 9082                       /usr/lib/libXau.so.6.0.0
7f2afe380000-7f2afe381000 rw-p 00002000 08:11 9082                       /usr/lib/libXau.so.6.0.0
7f2afe381000-7f2afe388000 r-xp 00000000 08:11 2647                       /lib/librt-2.9.so
7f2afe388000-7f2afe587000 ---p 00007000 08:11 2647                       /lib/librt-2.9.so
7f2afe587000-7f2afe588000 r--p 00006000 08:11 2647                       /lib/librt-2.9.so
7f2afe588000-7f2afe589000 rw-p 00007000 08:11 2647                       /lib/librt-2.9.so
7f2afe589000-7f2afe5a0000 r-xp 00000000 08:11 9043                       /usr/lib/libICE.so.6.3.0
7f2afe5a0000-7f2afe79f000 ---p 00017000 08:11 9043                       /usr/lib/libICE.so.6.3.0
7f2afe79f000-7f2afe7a1000 rw-p 00016000 08:11 9043                       /usr/lib/libICE.so.6.3.0
7f2afe7a1000-7f2afe7a4000 rw-p 7f2afe7a1000 00:00 0 
7f2afe7a4000-7f2afe7ac000 r-xp 00000000 08:11 9074                       /usr/lib/libSM.so.6.0.0
7f2afe7ac000-7f2afe9ab000 ---p 00008000 08:11 9074                       /usr/lib/libSM.so.6.0.0
7f2afe9ab000-7f2afe9ac000 r--p 00007000 08:11 9074                       /usr/lib/libSM.so.6.0.0
7f2afe9ac000-7f2afe9ad000 rw-p 00008000 08:11 9074                       /usr/lib/libSM.so.6.0.0
7f2afe9ad000-7f2afe9c8000 r-xp 00000000 08:11 10054                      /usr/lib/libxcb.so.1.1.0
7f2afe9c8000-7f2afebc7000 ---p 0001b000 08:11 10054                      /usr/lib/libxcb.so.1.1.0
7f2afebc7000-7f2afebc8000 r--p 0001a000 08:11 10054                      /usr/lib/libxcb.so.1.1.0
7f2afebc8000-7f2afebc9000 rw-p 0001b000 08:11 10054                      /usr/lib/libxcb.so.1.1.0
7f2afebc9000-7f2afebd0000 r-xp 00000000 08:11 10052                      /usr/lib/libxcb-render.so.0.0.0
7f2afebd0000-7f2afedd0000 ---p 00007000 08:11 10052                      /usr/lib/libxcb-render.so.0.0.0
7f2afedd0000-7f2afedd1000 r--p 00007000 08:11 10052                      /usr/lib/libxcb-render.so.0.0.0
7f2afedd1000-7f2afedd2000 rw-p 00008000 08:11 10052                      /usr/lib/libxcb-render.so.0.0.0
7f2afedd2000-7f2afedd5000 r-xp 00000000 08:11 10050                      /usr/lib/libxcb-render-util.so.0.0.0
7f2afedd5000-7f2afefd4000 ---p 00003000 08:11 10050                      /usr/lib/libxcb-render-util.so.0.0.0
7f2afefd4000-7f2afefd5000 r--p 00002000 08:11 10050                      /usr/lib/libxcb-render-util.so.0.0.0
7f2afefd5000-7f2afefd6000 rw-p 00003000 08:11 10050                      /usr/lib/libxcb-render-util.so.0.0.0
7f2afefd6000-7f2afeffb000 r-xp 00000000 08:11 9842                       /usr/lib/libpng12.so.0.27.0
7f2afeffb000-7f2aff1fb000 ---p 00025000 08:11 9842                       /usr/lib/libpng12.so.0.27.0
7f2aff1fb000-7f2aff1fc000 r--p 00025000 08:11 9842                       /usr/lib/libpng12.so.0.27.0
7f2aff1fc000-7f2aff1fd000 rw-p 00026000 08:11 9842                       /usr/lib/libpng12.so.0.27.0
7f2aff1fd000-7f2aff211000 r-xp 00000000 08:11 9282                       /usr/lib/libdirect-1.0.so.0.1.0
7f2aff211000-7f2aff411000 ---p 00014000 08:11 9282                       /usr/lib/libdirect-1.0.so.0.1.0
7f2aff411000-7f2aff412000 r--p 00014000 08:11 9282                       /usr/lib/libdirect-1.0.so.0.1.0
7f2aff412000-7f2aff413000 rw-p 00015000 08:11 9282                       /usr/lib/libdirect-1.0.so.0.1.0
7f2aff413000-7f2aff41b000 r-xp 00000000 08:11 9364                       /usr/lib/libfusion-1.0.so.0.1.0
7f2aff41b000-7f2aff61a000 ---p 00008000 08:11 9364                       /usr/lib/libfusion-1.0.so.0.1.0
7f2aff61a000-7f2aff61b000 r--p 00007000 08:11 9364                       /usr/lib/libfusion-1.0.so.0.1.0
7f2aff61b000-7f2aff61c000 rw-p 00008000 08:11 9364                       /usr/lib/libfusion-1.0.so.0.1.0
7f2aff61c000-7f2aff68d000 r-xp 00000000 08:11 9284                       /usr/lib/libdirectfb-1.0.so.0.1.0
7f2aff68d000-7f2aff88c000 ---p 00071000 08:11 9284                       /usr/lib/libdirectfb-1.0.so.0.1.0
7f2aff88c000-7f2aff88e000 r--p 00070000 08:11 9284                       /usr/lib/libdirectfb-1.0.so.0.1.0
7f2aff88e000-7f2aff890000 rw-p 00072000 08:11 9284                       /usr/lib/libdirectfb-1.0.so.0.1.0
7f2aff890000-7f2aff8d3000 r-xp 00000000 08:11 9836                       /usr/lib/libpixman-1.so.0.13.2
7f2aff8d3000-7f2affad2000 ---p 00043000 08:11 9836                       /usr/lib/libpixman-1.so.0.13.2
7f2affad2000-7f2affad4000 r--p 00042000 08:11 9836                       /usr/lib/libpixman-1.so.0.13.2
7f2affad4000-7f2affad5000 rw-p 00044000 08:11 9836                       /usr/lib/libpixman-1.so.0.13.2
7f2affad5000-7f2affaef000 r-xp 00000000 08:11 2649                       /lib/libselinux.so.1
7f2affaef000-7f2affcee000 ---p 0001a000 08:11 2649                       /lib/libselinux.so.1
7f2affcee000-7f2affcef000 r--p 00019000 08:11 2649                       /lib/libselinux.so.1
7f2affcef000-7f2affcf0000 rw-p 0001a000 08:11 2649                       /lib/libselinux.so.1
7f2affcf0000-7f2affcf1000 rw-p 7f2affcf0000 00:00 0 
7f2affcf1000-7f2affd20000 r-xp 00000000 08:11 2635                       /lib/libpcre.so.3.12.1
7f2affd20000-7f2afff1f000 ---p 0002f000 08:11 2635                       /lib/libpcre.so.3.12.1
7f2afff1f000-7f2afff20000 r--p 0002e000 08:11 2635                       /lib/libpcre.so.3.12.1
7f2afff20000-7f2afff21000 rw-p 0002f000 08:11 2635                       /lib/libpcre.so.3.12.1
7f2afff21000-7f2afff2a000 r-xp 00000000 08:11 9089                       /usr/lib/libXcursor.so.1.0.2
7f2afff2a000-7f2b0012a000 ---p 00009000 08:11 9089                       /usr/lib/libXcursor.so.1.0.2
7f2b0012a000-7f2b0012b000 rw-p 00009000 08:11 9089                       /usr/lib/libXcursor.so.1.0.2
7f2b0012b000-7f2b00133000 r-xp 00000000 08:11 9115                       /usr/lib/libXrandr.so.2.2.0
7f2b00133000-7f2b00332000 ---p 00008000 08:11 9115                       /usr/lib/libXrandr.so.2.2.0
7f2b00332000-7f2b00333000 r--p 00007000 08:11 9115                       /usr/lib/libXrandr.so.2.2.0
7f2b00333000-7f2b00334000 rw-p 00008000 08:11 9115                       /usr/lib/libXrandr.so.2.2.0
7f2b00334000-7f2b0033d000 r-xp 00000000 08:11 9103                       /usr/lib/libXi.so.6.0.0
7f2b0033d000-7f2b0053d000 ---p 00009000 08:11 9103                       /usr/lib/libXi.so.6.0.0
7f2b0053d000-7f2b0053e000 r--p 00009000 08:11 9103                       /usr/lib/libXi.so.6.0.0
7f2b0053e000-7f2b0053f000 rw-p 0000a000 08:11 9103                       /usr/lib/libXi.so.6.0.0
7f2b0053f000-7f2b00541000 r-xp 00000000 08:11 9105                       /usr/lib/libXinerama.so.1.0.0
7f2b00541000-7f2b00740000 ---p 00002000 08:11 9105                       /usr/lib/libXinerama.so.1.0.0
7f2b00740000-7f2b00741000 rw-p 00001000 08:11 9105                       /usr/lib/libXinerama.so.1.0.0
7f2b00741000-7f2b00752000 r-xp 00000000 0Aborted


```

ADDED: Firefox that comes with both Intrepid & Jaunty run ok.

---

