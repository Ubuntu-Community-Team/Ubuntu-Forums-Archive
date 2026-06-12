---
title: "Need help compiling ZSNES 1.42 on Lucid"
date: 2011-01-23
forum: Packaging and Compiling Programs
---

### Post by DangerOnTheRanger on 2011-01-23
Well, I'd like to play Street Fighter Alpha 2 against other people using ZBattle ( [http://zbattle.net](http://zbattle.net) ). 

I have to use ZSNES (which is the SNES emulator ZBattle uses underneath) for emulation. However, only ZSNES 1.42 or lower will work, so the repository version (1.51 or 1.52) doesn't work.

Sooo, I had to compile ZSNES from scratch, and the only dependency I don't have is SDL 1.2.

However, **sudo apt-get install libsdl1.2-dev **throws up:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaa1-dev libasound2-dev libaudio-dev libcaca-dev libdrm-dev
  libgl1-mesa-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev
  libncurses5-dev libpulse-dev libsdl1.2debian libsdl1.2debian-alsa
  libslang2-dev mesa-common-dev
Suggested packages:
  libasound2-doc
The following packages will be REMOVED:
  libsdl1.2debian-pulseaudio ubuntu-desktop
The following NEW packages will be installed:
  libaa1-dev libasound2-dev libaudio-dev libcaca-dev libdrm-dev
  libgl1-mesa-dev libglu1-mesa-dev libncurses5-dev libpulse-dev libsdl1.2-dev
  libsdl1.2debian-alsa libslang2-dev mesa-common-dev
The following packages will be upgraded:
  libgl1-mesa-glx libglu1-mesa libsdl1.2debian
3 upgraded, 13 newly installed, 2 to remove and 421 not upgraded.

```I do NOT want to remove ubuntu-desktop and SDL's PulseAudio extension. Bad things will happen :roll:

Anyone have any workarounds?

EDIT: Post #100 for me! Wahooo!

---

### Post by SevenMachines on 2011-01-23
sdl-dev should install fine without forcing anything to be removed, the fact that it tries upgrade libsdl1.2debian makes me wonder...
* are you're packages up-to-date?
* do you have additional ppa's installed? 

technically, removing the 2 packages it mentions shouldnt cause the world to end, sdl-pulseaudio isn't chronically essential and ubuntu-desktop is just a meta-package (removed because it requires sdl-pulseaudio).

But the real problem is that, when synched with the ubuntu repositories, this problem should not occur

---

### Post by DangerOnTheRanger on 2011-01-25
Hmm, installing libsdl1.2debian-pulseaudio and then libsdl1.2debian and *then* libsdl1.2-dev let go off all those wierd dependencies.

Now, though, when I compile ZSNES, it gives this error:

```

gcc  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o zip/zpng.o -c zip/zpng.c
gcc  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o effects/burn.o -c effects/burn.c
gcc  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o effects/water.o -c effects/water.c
gcc  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o effects/smoke.o -c effects/smoke.c
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/7zlzma.o -c jma/7zlzma.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/crc32.o -c jma/crc32.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/iiostrm.o -c jma/iiostrm.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/inbyte.o -c jma/inbyte.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/jma.o -c jma/jma.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/lzma.o -c jma/lzma.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/lzmadec.o -c jma/lzmadec.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/winout.o -c jma/winout.cpp
g++  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o jma/zsnesjma.o -c jma/zsnesjma.cpp
g++ -o zsnes chips/sfxproc.o chips/fxemu2.o chips/dsp1proc.o chips/fxemu2b.o chips/fxemu2c.o chips/fxtable.o chips/sa1proc.o chips/sa1regs.o chips/dsp1emu.o chips/st10proc.o chips/seta10.o chips/dsp2proc.o chips/sdd1emu.o cpu/addrni.o cpu/dma.o cpu/dsp.o cpu/dspproc.o cpu/execute.o cpu/executec.o cpu/irq.o cpu/memory.o cpu/spc700.o cpu/stable.o cpu/table.o cpu/tableb.o cpu/tablec.o linux/copyvwin.o linux/sdlintrf.o linux/sdllink.o linux/sw_draw.o linux/zloaderw.o linux/ztcp.o linux/zipxw.o linux/zfilew.o dos/debug.o dos/joy.o dos/modemrtn.o dos/vesa2.o dos/initvid.o dos/sw.o dos/gppro.o dos/vesa12.o gui/gui.o gui/menu.o video/makev16b.o video/makev16t.o video/makevid.o video/mode716.o video/mode716b.o video/mode716d.o video/mode716e.o video/mode716t.o video/mode7.o video/mode7ext.o video/mv16tms.o video/newg162.o video/newgfx16.o video/newgfx2.o video/newgfx.o video/m716text.o video/2xsaiw.o video/procvid.o video/sw_draw.o video/hq2x16.o video/hq2x32.o video/hq3x16.o video/hq3x32.o video/hq4x16.o video/hq4x32.o cfgload.o endmem.o init.o initc.o uic.o patch.o ui.o vcache.o version.o zip/unzip.o zip/zpng.o effects/burn.o effects/water.o effects/smoke.o jma/7zlzma.o jma/crc32.o jma/iiostrm.o jma/inbyte.o jma/jma.o jma/lzma.o jma/lzmadec.o jma/winout.o jma/zsnesjma.o  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro  -L/usr/local/lib -L/usr/lib  -lz -L/usr/lib -lSDL  -lpng -lm -L
g++: argument to '-L' missing

make: *** [zsnes] Error 1

```

A missing argument, but what's it for?

**man gcc** gives:

```

-Fdir
           Add the framework directory dir to the head of the list of
           directories to be searched for header files.  These directories are
           interleaved with those specified by -I options and are scanned in a
           left-to-right order.

           A framework directory is a directory with frameworks in it.  A
           framework is a directory with a "Headers" and/or "PrivateHeaders"
           directory contained directly in it that ends in ".framework".  The
           name of a framework is the name of this directory excluding the
           ".framework".  Headers associated with the framework are found in
           one of those two directories, with "Headers" being searched first.
           A subframework is a framework directory that is in a framework's
           "Frameworks" directory.  Includes of subframework headers can only
           appear in a header of a framework that contains the subframework,
           or in a sibling subframework header.  Two subframeworks are
           siblings if they occur in the same framework.  A subframework
           should not have the same name as a framework, a warning will be
           issued if this is violated.  Currently a subframework cannot have
           subframeworks, in the future, the mechanism may be extended to
           support this.  The standard frameworks can be found in
           "/System/Library/Frameworks" and "/Library/Frameworks".

```

I just removed the flag in the Makefile, and it linked without errors.
When I tried to run zsnes, it choked with:

```

ZSNES v1.42 (c) 1997-2005, ZSNES Team

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before doing so.

Use ZSNES -? for command line definitions.

*** glibc detected *** ./zsnes: munmap_chunk(): invalid pointer: 0xbfe84e5a ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0x21d591]
/lib/tls/i686/cmov/libc.so.6(+0x6c80e)[0x21e80e]
./zsnes[0x80df8db]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x1c8bd6]
./zsnes[0x804b7e1]
======= Memory map: ========
00110000-0012d000 r-xp 00000000 07:00 261208     /lib/libgcc_s.so.1
0012d000-0012e000 r-xp 0001c000 07:00 261208     /lib/libgcc_s.so.1
0012e000-0012f000 rwxp 0001d000 07:00 261208     /lib/libgcc_s.so.1
0012f000-00144000 r-xp 00000000 07:00 265572     /lib/tls/i686/cmov/libpthread-2.11.1.so
00144000-00145000 r-xp 00014000 07:00 265572     /lib/tls/i686/cmov/libpthread-2.11.1.so
00145000-00146000 rwxp 00015000 07:00 265572     /lib/tls/i686/cmov/libpthread-2.11.1.so
00146000-00148000 rwxp 00000000 00:00 0 
00148000-0014a000 r-xp 00000000 07:00 265552     /lib/tls/i686/cmov/libdl-2.11.1.so
0014a000-0014b000 r-xp 00001000 07:00 265552     /lib/tls/i686/cmov/libdl-2.11.1.so
0014b000-0014c000 rwxp 00002000 07:00 265552     /lib/tls/i686/cmov/libdl-2.11.1.so
0014c000-00160000 r-xp 00000000 07:00 269111     /usr/lib/libdirect-1.2.so.0.8.0
00160000-00161000 r-xp 00013000 07:00 269111     /usr/lib/libdirect-1.2.so.0.8.0
00161000-00162000 rwxp 00014000 07:00 269111     /usr/lib/libdirect-1.2.so.0.8.0
00162000-00185000 r-xp 00000000 07:00 277620     /lib/libpng12.so.0.42.0
00185000-00186000 r-xp 00022000 07:00 277620     /lib/libpng12.so.0.42.0
00186000-00187000 rwxp 00023000 07:00 277620     /lib/libpng12.so.0.42.0
00187000-0018e000 r-xp 00000000 07:00 265576     /lib/tls/i686/cmov/librt-2.11.1.so
0018e000-0018f000 r-xp 00006000 07:00 265576     /lib/tls/i686/cmov/librt-2.11.1.so
0018f000-00190000 rwxp 00007000 07:00 265576     /lib/tls/i686/cmov/librt-2.11.1.so
00190000-00195000 rwxp 00000000 00:00 0 
00195000-001b0000 r-xp 00000000 07:00 261150     /lib/ld-2.11.1.so
001b0000-001b1000 r-xp 0001a000 07:00 261150     /lib/ld-2.11.1.so
001b1000-001b2000 rwxp 0001b000 07:00 261150     /lib/ld-2.11.1.so
001b2000-00305000 r-xp 00000000 07:00 265546     /lib/tls/i686/cmov/libc-2.11.1.so
00305000-00306000 ---p 00153000 07:00 265546     /lib/tls/i686/cmov/libc-2.11.1.so
00306000-00308000 r-xp 00153000 07:00 265546     /lib/tls/i686/cmov/libc-2.11.1.so
00308000-00309000 rwxp 00155000 07:00 265546     /lib/tls/i686/cmov/libc-2.11.1.so
00309000-0030c000 rwxp 00000000 00:00 0 
0030c000-0034c000 r-xp 00000000 07:00 269702     /usr/lib/libpulse.so.0.12.2
0034c000-0034d000 r-xp 00040000 07:00 269702     /usr/lib/libpulse.so.0.12.2
0034d000-0034e000 rwxp 00041000 07:00 269702     /usr/lib/libpulse.so.0.12.2
0034e000-003c1000 r-xp 00000000 07:00 269113     /usr/lib/libdirectfb-1.2.so.0.8.0
003c1000-003c2000 ---p 00073000 07:00 269113     /usr/lib/libdirectfb-1.2.so.0.8.0
003c2000-003c3000 r-xp 00073000 07:00 269113     /usr/lib/libdirectfb-1.2.so.0.8.0
003c3000-003c4000 rwxp 00074000 07:00 269113     /usr/lib/libdirectfb-1.2.so.0.8.0
003c4000-003c5000 rwxp 00000000 00:00 0 
003c5000-003cc000 r-xp 00000000 07:00 268878     /usr/lib/libSM.so.6.0.1
003cc000-003cd000 r-xp 00006000 07:00 268878     /usr/lib/libSM.so.6.0.1
003cd000-003ce000 rwxp 00007000 07:00 268878     /usr/lib/libSM.so.6.0.1
003ce000-003d5000 r-xp 00000000 07:00 261318     /lib/libwrap.so.0.7.6
003d5000-003d6000 r-xp 00006000 07:00 261318     /lib/libwrap.so.0.7.6
003d6000-003d7000 rwxp 00007000 07:00 261318     /lib/libwrap.so.0.7.6
003d7000-003da000 r-xp 00000000 07:00 261316     /lib/libuuid.so.1.3.0
003da000-003db000 r-xp 00002000 07:00 261316     /lib/libuuid.so.1.3.0
003db000-003dc000 rwxp 00003000 07:00 261316     /lib/libuuid.so.1.3.0
003dc000-003e0000 r-xp 00000000 07:00 268895     /usr/lib/libXdmcp.so.6.0.0
003e0000-003e1000 r-xp 00003000 07:00 268895     /usr/lib/libXdmcp.so.6.0.0
003e1000-003e2000 rwxp 00004000 07:00 268895     /usr/lib/libXdmcp.so.6.0.0
003e3000-004cc000 r-xp 00000000 07:00 269789     /usr/lib/libstdc++.so.6.0.13
004cc000-004cd000 ---p 000e9000 07:00 269789     /usr/lib/libstdc++.so.6.0.13
004cd000-004d1000 r-xp 000e9000 07:00 269789     /usr/lib/libstdc++.so.6.0.13
004d1000-004d2000 rwxp 000ed000 07:00 269789     /usr/lib/libstdc++.so.6.0.13
004d2000-004d9000 rwxp 00000000 00:00 0 
004d9000-00522000 r-xp 00000000 07:00 269703     /usr/lib/libpulsecommon-0.9.21.so
00522000-00523000 r-xp 00048000 07:00 269703     /usr/lib/libpulsecommon-0.9.21.so
00523000-00524000 rwxp 00049000 07:00 269703     /usr/lib/libpulsecommon-0.9.21.so
00524000-00530000 r-xp 00000000 07:00 268905     /usr/lib/libXi.so.6.1.0
00530000-00531000 r-xp 0000c000 07:00 268905     /usr/lib/libXi.so.6.1.0
00531000-00532000 rwxp 0000d000 07:00 268905     /usr/lib/libXi.so.6.1.0
00532000-00545000 r-xp 00000000 07:00 265557     /lib/tls/i686/cmov/libnsl-2.11.1.so
00545000-00546000 r-xp 00012000 07:00 265557     /lib/tls/i686/cmov/libnsl-2.11.1.so
00546000-00547000 rwxp 00013000 07:00 265557     /lib/tls/i686/cmov/libnsl-2.11.1.so
00547000-00549000 rwxp 00000000 00:00 0 
0055b000-0055f000 r-xp 00000000 07:00 268925     /usr/lib/libXtst.so.6.1.0
0055f000-00560000 r-xp 00003000 07:00 268925     /usr/lib/libXtst.so.6.1.0
00560000-00561000 rwxp 00004000 07:00 268925     /usr/lib/libXtst.so.6.1.0
00561000-005c2000 r-xp 00000000 07:00 269762     /usr/lib/libsndfile.so.1.0.21
005c2000-005c3000 ---p 00061000 07:00 269762     /usr/lib/libsndfile.so.1.0.21
005c3000-005c4000 r-xp 00061000 07:00 269762     /usr/lib/libsndfile.so.1.0.21
005c4000-005c5000 rwxp 00062000 07:00 269762     /usr/lib/libsndfile.so.1.0.21
005c5000-005c9000 rwxp 00000000 00:00 0 
005c9000-00600000 r-xp 00000000 07:00 261186     /lib/libdbus-1.so.3.4.0
00600000-00601000 r-xp 00036000 07:00 261186     /lib/libdbus-1.so.3.4.0
00601000-00602000 rwxp 00037000 07:00 261186     /lib/libdbus-1.so.3.4.0
00687000-00688000 r-xp 00000000 00:00 0          [vdso]
00749000-0075c000 r-xp 00000000 07:00 261323     /lib/libz.so.1.2.3.3
0075c000-0075d000 r-xp 00012000 07:00 261323     /lib/libz.so.1.2.3.3
0075d000-0075e000 rwxp 00013000 07:00 261323     /lib/libz.so.1.2.3.3
0076f000-00774000 r-xp 00000000 07:00 269608     /usr/lib/libogg.so.0.6.0
00774000-00775000 r-xp 00004000 07:00 269608     /usr/lib/libogg.so.0.6.0
00775000-00776000 rwxp 00005000 07:00 269608     /usr/lib/libogg.so.0.6.0Aborted

```

Know anything about this error message?
Thanks for the previous quick reply!

---

### Post by SevenMachines on 2011-01-25
munmap_chunk(): invalid pointer is  some error in the code on freeing up  memory free/delete. To fix it you'd need to debug the code.
You might be better served trying to get whatever it is working on a newer zsnes version. Otherwise you can do a debug build, use the debugger to track down the problem, fix it or look in svn for the fix... all in all a bit of a chore :)

---

### Post by SevenMachines on 2011-01-25
Actually, it looks like that was a common problem with zsnes version 1.42 from a quick google

---

### Post by DangerOnTheRanger on 2011-01-25
Actually, ZSNES is in the repos, but it's version 1.52, and it seems a lot of people report problems with ZBattle netplay with that specific version.

I'll try it anyway, though, and post the results here.

---

### Post by SevenMachines on 2011-01-25
You can always give svn a bash
[http://board.zsnes.com/phpBB3/viewtopic.php?f=18&t=7371](http://board.zsnes.com/phpBB3/viewtopic.php?f=18&t=7371)

---

### Post by DangerOnTheRanger on 2011-01-27
Okay, I'll try SVN, too.
Thanks! I'll post back (again) with results.

---

### Post by DangerOnTheRanger on 2011-02-20
Been a while, but that didn't work...

---

