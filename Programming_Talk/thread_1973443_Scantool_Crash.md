---
title: "Scantool Crash"
date: 2012-05-04
forum: Programming Talk
---

### Post by cody1233 on 2012-05-04
I compiled source software from Scantool.net and it's dependencies, but when I am connecting to my car the program crashes and comes up with this in the terminal window:

cody@cody-laptop:~$ sudo scantool
Fri May  4 19:05:51 2012
Version: 1.21 for DOS

Initializing All Modules...
---------------------------
Initializing Allegro... OK
Installing Timers... OK
Installing Keyboard... OK
Installing Mouse... OK
Loading Preferences... OK
Trying Windowed Graphics Mode... OK
Loading Data File... OK
Initializing Serial Module... OK
Opening COM1... opened /dev/ttyUSB0
OK

Displaying Main Menu...
-----------------------
*** stack smashing detected ***: scantool terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0xb7525dd5]
/lib/i386-linux-gnu/libc.so.6(+0xffd8a)[0xb7525d8a]
scantool[0x8057d22]
scantool[0x8057534]
scantool[0x80569ad]
scantool[0x8089661]
scantool[0x808986e]
scantool[0x808c09e]
scantool[0x808c9c2]
scantool[0x805597b]
scantool[0x805085e]
scantool[0x8089661]
scantool[0x808c5f7]
scantool[0x808c9c2]
scantool[0x80507f2]
scantool[0x80505cd]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xb743f4d3]
scantool[0x804febd]
======= Memory map: ========
08048000-08133000 r-xp 00000000 08:01 1242070    /usr/bin/scantool
08134000-08135000 r--p 000eb000 08:01 1242070    /usr/bin/scantool
08135000-08147000 rw-p 000ec000 08:01 1242070    /usr/bin/scantool
08147000-08166000 rw-p 00000000 00:00 0 
08e5e000-08f05000 rw-p 00000000 00:00 0          [heap]
b5fd4000-b6100000 rw-s 00000000 00:04 262149     /SYSV00000000 (deleted)
b6100000-b6121000 rw-p 00000000 00:00 0 
b6121000-b6200000 ---p 00000000 00:00 0 
b628b000-b628c000 ---p 00000000 00:00 0 
b628c000-b6a8c000 rw-p 00000000 00:00 0 
b6a8c000-b6a8d000 ---p 00000000 00:00 0 
b6a8d000-b728d000 rw-p 00000000 00:00 0 
b728d000-b72a9000 r-xp 00000000 08:01 1792627    /lib/i386-linux-gnu/libgcc_s.so.1
b72a9000-b72aa000 r--p 0001b000 08:01 1792627    /lib/i386-linux-gnu/libgcc_s.so.1
b72aa000-b72ab000 rw-p 0001c000 08:01 1792627    /lib/i386-linux-gnu/libgcc_s.so.1
b72ab000-b7383000 r-xp 00000000 08:01 1450226    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b7383000-b7384000 ---p 000d8000 08:01 1450226    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b7384000-b7388000 r--p 000d8000 08:01 1450226    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b7388000-b7389000 rw-p 000dc000 08:01 1450226    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
b7389000-b7390000 rw-p 00000000 00:00 0 
b739c000-b73e9000 rw-p 00000000 00:00 0 
b73e9000-b73ee000 r-xp 00000000 08:01 1449710    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b73ee000-b73ef000 r--p 00004000 08:01 1449710    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b73ef000-b73f0000 rw-p 00005000 08:01 1449710    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b73f0000-b73f2000 r-xp 00000000 08:01 1449699    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b73f2000-b73f3000 r--p 00001000 08:01 1449699    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b73f3000-b73f4000 rw-p 00002000 08:01 1449699    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b73f4000-b73f5000 rw-p 00000000 00:00 0 
b73f5000-b73f9000 r-xp 00000000 08:01 1449714    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b73f9000-b73fa000 r--p 00004000 08:01 1449714    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b73fa000-b73fb000 rw-p 00005000 08:01 1449714    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b73fb000-b7403000 r-xp 00000000 08:01 1449732    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b7403000-b7404000 r--p 00007000 08:01 1449732    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b7404000-b7405000 rw-p 00008000 08:01 1449732    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b7405000-b7424000 r-xp 00000000 08:01 1450298    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b7424000-b7425000 r--p 0001f000 08:01 1450298    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b7425000-b7426000 rw-p 00020000 08:01 1450298    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b7426000-b75c5000 r-xp 00000000 08:01 1792606    /lib/i386-linux-gnu/libc-2.15.so
b75c5000-b75c7000 r--p 0019f000 08:01 1792606    /lib/i386-linux-gnu/libc-2.15.so
b75c7000-b75c8000 rw-p 001a1000 08:01 1792606    /lib/i386-linux-gnu/libc-2.15.so
b75c8000-b75cb000 rw-p 00000000 00:00 0 
b75cb000-b75f5000 r-xp 00000000 08:01 1792638    /lib/i386-linux-gnu/libm-2.15.so
b75f5000-b75f6000 r--p 00029000 08:01 1792638    /lib/i386-linux-gnu/libm-2.15.so
b75f6000-b75f7000 rw-p 0002a000 08:01 1792638    /lib/i386-linux-gnu/libm-2.15.so
b75f7000-b75f8000 rw-p 00000000 00:00 0 
b75f8000-b760f000 r-xp 00000000 08:01 1792686    /lib/i386-linux-gnu/libpthread-2.15.so
b760f000-b7610000 r--p 00016000 08:01 1792686    /lib/i386-linux-gnu/libpthread-2.15.so
b7610000-b7611000 rw-p 00017000 08:01 1792686    /lib/i386-linux-gnu/libpthread-2.15.so
b7611000-b7613000 rw-p 00000000 00:00 0 
b7613000-b7616000 r-xp 00000000 08:01 1792619    /lib/i386-linux-gnu/libdl-2.15.so
b7616000-b7617000 r--p 00002000 08:01 1792619    /lib/i386-linux-gnu/libdl-2.15.so
b7617000-b7618000 rw-p 00003000 08:01 1792619    /lib/i386-linux-gnu/libdl-2.15.so
b7618000-b761c000 r-xp 00000000 08:01 1449740    /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
b761c000-b761d000 r--p 00003000 08:01 1449740    /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
b761d000-b761e000 rw-p 00004000 08:01 1449740    /usr/lib/i386-linux-gnu/libXxf86vm.so.1.0.0
b761e000-b7627000 r-xp 00000000 08:01 1449706    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b7627000-b7628000 r--p 00008000 08:01 1449706    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b7628000-b7629000 rw-p 00009000 08:01 1449706    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b7629000-b7639000 r-xp 00000000 08:01 1449728    /usr/lib/i386-linux-gnu/libXpm.so.4.11.0
b7639000-b763a000 r--p 0000f000 08:01 1449728    /usr/lib/i386-linux-gnu/libXpm.so.4.11.0
b763a000-b763b000 rw-p 00010000 08:01 1449728    /usr/lib/i386-linux-gnu/libXpm.so.4.11.0
b763b000-b763c000 rw-p 00000000 00:00 0 
b763c000-b764c000 r-xp 00000000 08:01 1449712    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b764c000-b764d000 r--p 0000f000 08:01 1449712    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b764d000-b764e000 rw-p 00010000 08:01 1449712    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b764e000-b777e000 r-xp 00000000 08:01 1449697    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b777e000-b777f000 r--p 0012f000 08:01 1449697    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b777f000-b7781000 rw-p 00130000 08:01 1449697    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b7781000-b7782000 rw-p 00000000 00:00 0 
b7786000-b778d000 r-xp 00000000 08:01 1792692    /lib/i386-linux-gnu/librt-2.15.so
b778d000-b778e000 r--p 00006000 08:01 1792692    /lib/i386-linux-gnu/librt-2.15.so
b778e000-b778f000 rw-p 00007000 08:01 1792692    /lib/i386-linux-gnu/librt-2.15.so
b7794000-b7797000 rw-p 00000000 00:00 0 
b7797000-b7798000 r-xp 00000000 00:00 0          [vdso]
b7798000-b77b8000 r-xp 00000000 08:01 1792586    /lib/i386-linux-gnu/ld-2.15.so
b77b8000-b77b9000 r--p 0001f000 08:01 1792586    /lib/i386-linux-gnu/ld-2.15.so
b77b9000-b77ba000 rw-p 00020000 08:01 1792586    /lib/i386-linux-gnu/ld-2.15.so
bfc99000-bfcba000 rw-p 00000000 00:00 0          [stack]
cody@cody-laptop:~$ 
Any Ideas??  Note that i'm running this with the sudo command...not sure if that is contributing to this error or not...I can't run it without though.

---

### Post by Bachstelze on 2012-05-04
Most probably a bug in the code.

---

