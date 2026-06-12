---
title: "I keep getting a Minecraft error"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by hutriv on 2012-04-07
Ok so i load up minecraft and it opens to the menu screen. If i go into Multiplayer and click on a server i play on it opens up and it shows everything, the map, but then it closes the launcher and if i try to play singleplayer, when i create a world it just stops 1/5 of the way and freezes:( i have tried using all jdk and jre's and i was using Sun jre, or whatever it is, and this is what happened. Ill copy the error report. By the way i got this error report in my home folder and noticed it was an error report when they popped up after countless attempts to fix Minecraft. Now you see Minecraft worked great before i had to re-download Ubuntu cause i was stupid and took all privileges from my system using the sudo command by accident and well now i keep trying different methods and it just wont work. I don't know why cause before it worked perfectly and now it doesn't and it's making me frustrated cause i love this game. 

ERROR REPORT!!!

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7705416, pid=4980, tid=2978798448
#
# JRE version: 6.0_31-b04
# Java VM: Java HotSpot(TM) Client VM (20.6-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x00001374

Registers:
EAX=0x00000000, EBX=0x00001374, ECX=0x0000139d, EDX=0x0000000b
ESP=0xb18cd28c, EBP=0xb18cd398, ESI=0x00000020, EDI=0xb76eeff4
EIP=0xb7705416, EFLAGS=0x00200206, CR2=0xb76f6100

Top of Stack: (sp=0xb18cd28c)
0xb18cd28c:   b76e5e6e b76eeff4 b11ab880 b0b8b743
0xb18cd29c:   0000000b 00000000 00000000 00000000
0xb18cd2ac:   00001000 00000000 00000000 00000000
0xb18cd2bc:   00000000 00000000 7fffffff fffffffe
0xb18cd2cc:   ffffffff ffffffff ffffffff ffffffff
0xb18cd2dc:   ffffffff ffffffff ffffffff ffffffff
0xb18cd2ec:   ffffffff ffffffff ffffffff ffffffff
0xb18cd2fc:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb7705416)
0xb77053f6:   00 00 00 00 00 00 00 00 00 00 58 b8 77 00 00 00
0xb7705406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0xb7705416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73
0xb7705426:   68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 6e 73 74 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x00001374 is an unknown value
ECX=0x0000139d is an unknown value
EDX=0x0000000b is an unknown value
ESP=0xb18cd28c is an unknown value
EBP=0xb18cd398 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb76eeff4: <offset 0x17ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb76d7000


Stack: [0xb18bd000,0xb18ce000],  sp=0xb18cd28c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [libpthread.so.0+0x6d31]  short+0xd1


---------------  P R O C E S S  ---------------

VM state:synchronizing (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x083eb558] Safepoint_lock - owner thread: 0x08411800
[0x083eb5c0] Threads_lock - owner thread: 0x08411800

Heap
 def new generation   total 21888K, used 2407K [0x7f080000, 0x80830000, 0x84480000)
  eden space 19520K,   0% used [0x7f080000, 0x7f089dc8, 0x80390000)
  from space 2368K, 100% used [0x805e0000, 0x80830000, 0x80830000)
  to   space 2368K,   0% used [0x80390000, 0x80390000, 0x805e0000)
 tenured generation   total 48480K, used 32157K [0x84480000, 0x873d8000, 0x8ec80000)
   the space 48480K,  66% used [0x84480000, 0x863e7690, 0x863e7800, 0x873d8000)
 compacting perm gen  total 12288K, used 8847K [0x8ec80000, 0x8f880000, 0x92c80000)
   the space 12288K,  71% used [0x8ec80000, 0x8f523cb8, 0x8f523e00, 0x8f880000)
    ro space 10240K,  61% used [0x92c80000, 0x932a9838, 0x932a9a00, 0x93680000)
    rw space 12288K,  60% used [0x93680000, 0x93dba040, 0x93dba200, 0x94280000)

Code Cache  [0xb4b22000, 0xb4e12000, 0xb6b22000)
 total_blobs=1724 nmethods=1361 adapters=297 free_code_cache=30490048 largest_free_block=192

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
083e8000-08eb4000 rwxp 00000000 00:00 0          [heap]
7f080000-80830000 rwxp 00000000 00:00 0 
80830000-84480000 rwxp 00000000 00:00 0 
84480000-873d8000 rwxp 00000000 00:00 0 
873d8000-8ec80000 rwxp 00000000 00:00 0 
8ec80000-8f880000 rwxp 00000000 00:00 0 
8f880000-92c80000 rwxp 00000000 00:00 0 
92c80000-932aa000 r-xs 00001000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
932aa000-93680000 rwxp 00000000 00:00 0 
93680000-93dbb000 rwxp 0062b000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
93dbb000-94280000 rwxp 00000000 00:00 0 
94280000-94362000 rwxp 00d66000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94362000-94680000 rwxp 00000000 00:00 0 
94680000-94688000 r-xs 00e48000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94688000-94a80000 rwxp 00000000 00:00 0 
9ddff000-9de00000 ---p 00000000 00:00 0 
9de00000-9e000000 rwxp 00000000 00:00 0 
9e000000-9e0ee000 rwxp 00000000 00:00 0 
9e0ee000-9e100000 ---p 00000000 00:00 0 
9e1af000-9e1b2000 ---p 00000000 00:00 0 
9e1b2000-9e200000 rwxp 00000000 00:00 0 
9e200000-9e2ff000 rwxp 00000000 00:00 0 
9e2ff000-9e300000 ---p 00000000 00:00 0 
9e334000-a8374000 rwxp 00000000 00:00 0 
a8374000-a8375000 ---p 00000000 00:00 0 
a8375000-a8b75000 rwxp 00000000 00:00 0 
a8b75000-acb76000 rwxs 00000000 00:12 63099      /run/shm/pulse-shm-2815449410
acb76000-accdc000 r-xp 00000000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
accdc000-acced000 r-xp 00165000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
acced000-accee000 rwxp 00176000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
accee000-acd3a000 r-xp 00000000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
acd3a000-acd3b000 r-xp 0004b000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
acd3b000-acd3c000 rwxp 0004c000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
acd3c000-acda7000 r-xp 00000000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
acda7000-acda8000 r-xp 0006b000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
acda8000-acda9000 rwxp 0006c000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
acda9000-acdad000 rwxp 00000000 00:00 0 
acdad000-ace10000 r-xp 00000000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ace10000-ace11000 r-xp 00062000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ace11000-ace12000 rwxp 00063000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ace12000-ace5e000 r-xp 00000000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
ace5e000-ace5f000 r-xp 0004b000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
ace5f000-ace60000 rwxp 0004c000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
ace60000-acf4c000 r-xp 00000000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
acf4c000-acf50000 r-xp 000eb000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
acf50000-acf51000 rwxp 000ef000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
acf51000-acf76000 r-xp 00000000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
acf76000-acf77000 rwxp 00025000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
acf77000-ad064000 rwxp 00000000 00:00 0 
ad064000-ad164000 rwxs 05b10000 00:05 8271       /dev/ati/card0
ad164000-ad364000 rwxs c493b000 00:05 8271       /dev/ati/card0
ad364000-aeb68000 rwxp 00000000 00:00 0 
aeb68000-af268000 rwxs 00006000 00:05 8271       /dev/ati/card0
af268000-b1022000 r-xp 00000000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b1022000-b10ed000 rwxp 01db9000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b10ed000-b11ad000 rwxp 00000000 00:00 0 
b11ad000-b133e000 rwxs 00000000 00:04 12255241   /SYSV00000000 (deleted)
b133e000-b13a3000 rwxs 00000000 00:04 12222471   /SYSV00000000 (deleted)
b13a3000-b13a6000 ---p 00000000 00:00 0 
b13a6000-b13f4000 rwxp 00000000 00:00 0 
b13f4000-b13f7000 ---p 00000000 00:00 0 
b13f7000-b1445000 rwxp 00000000 00:00 0 
b1445000-b15d6000 rwxs 00000000 00:04 10878981   /SYSV00000000 (deleted)
b15d6000-b1842000 rwxp 00000000 00:00 0 
b1842000-b18a2000 rwxs 00000000 00:04 10747910   /SYSV00000000 (deleted)
b18bd000-b18be000 ---p 00000000 00:00 0 
b18be000-b18ce000 rwxp 00000000 00:00 0 
b18ce000-b18e5000 r-xs 003c2000 08:01 274284     /home/hutriv/.minecraft/bin/minecraft.jar
b18e5000-b18e8000 r-xs 0001f000 08:01 274283     /home/hutriv/.minecraft/bin/lwjgl_util.jar
b18e8000-b18ed000 r-xs 00033000 08:01 274282     /home/hutriv/.minecraft/bin/jinput.jar
b18ed000-b18f6000 r-xs 000ac000 08:01 274281     /home/hutriv/.minecraft/bin/lwjgl.jar
b18f6000-b18f9000 r-xs 000cc000 08:01 280947     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/localedata.jar
b18f9000-b18fc000 ---p 00000000 00:00 0 
b18fc000-b194a000 rwxp 00000000 00:00 0 
b194a000-b194d000 ---p 00000000 00:00 0 
b194d000-b199b000 rwxp 00000000 00:00 0 
b199b000-b19a1000 r-xs 00095000 08:01 2245562    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jsse.jar
b19a1000-b19a9000 r-xs 00115000 08:01 2245514    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/resources.jar
b19a9000-b19ac000 ---p 00000000 00:00 0 
b19ac000-b19fa000 rwxp 00000000 00:00 0 
b19fa000-b19fd000 ---p 00000000 00:00 0 
b19fd000-b1a4b000 rwxp 00000000 00:00 0 
b1a4b000-b1a4e000 ---p 00000000 00:00 0 
b1a4e000-b1a9c000 rwxp 00000000 00:00 0 
b1a9c000-b1a9d000 ---p 00000000 00:00 0 
b1a9d000-b229d000 rwxp 00000000 00:00 0 
b229d000-b229e000 ---p 00000000 00:00 0 
b229e000-b2a9e000 rwxp 00000000 00:00 0 
b2a9e000-b2ab6000 r-xp 00000000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2ab6000-b2ab7000 r-xp 00017000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2ab7000-b2ab8000 rwxp 00018000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2ab8000-b2ac8000 r-xp 00000000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2ac8000-b2ac9000 ---p 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2ac9000-b2aca000 r-xp 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2aca000-b2acb000 rwxp 00011000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2acb000-b2ace000 r-xs 00027000 08:01 280946     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/sunjce_provider.jar
b2ace000-b2ad3000 r-xp 00000000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2ad3000-b2ad4000 r-xp 00004000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2ad4000-b2ad5000 rwxp 00005000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2ad5000-b2ad7000 r-xp 00000000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2ad7000-b2ad8000 r-xp 00001000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2ad8000-b2ad9000 rwxp 00002000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2ad9000-b2adc000 r-xs 00013000 08:01 2245530    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jce.jar
b2adc000-b2aef000 r-xp 00000000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2aef000-b2af0000 r-xp 00012000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2af0000-b2af1000 rwxp 00013000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2af1000-b2b01000 r-xp 00000000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b01000-b2b02000 r-xp 0000f000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b02000-b2b03000 rwxp 00010000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b03000-b2b4a000 r-xp 00000000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2b4a000-b2b4b000 r-xp 00046000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2b4b000-b2b4c000 rwxp 00047000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2b4c000-b2b61000 r-xp 00000000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2b61000-b2b62000 r-xp 00015000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2b62000-b2b63000 rwxp 00016000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2b63000-b2b8d000 r-xp 00000000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2b8d000-b2b8e000 r-xp 00029000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2b8e000-b2b8f000 rwxp 0002a000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2b8f000-b2bce000 r-xp 00000000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2bce000-b2bcf000 r-xp 0003f000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2bcf000-b2bd0000 rwxp 00040000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2bd2000-b2bd6000 r-xp 00000000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bd6000-b2bd7000 r-xp 00004000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bd7000-b2bd8000 rwxp 00005000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bd8000-b2bdf000 r-xp 00000000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2bdf000-b2be0000 r-xp 00006000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2be0000-b2be1000 rwxp 00007000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2be1000-b2be6000 r-xp 00000000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2be6000-b2be7000 ---p 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2be7000-b2be8000 r-xp 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2be8000-b2be9000 rwxp 00006000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2be9000-b2c3b000 r-xp 00000000 08:01 527586     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b2c3b000-b2c92000 r-xp 00000000 08:01 527633     /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b2c92000-b2c94000 r-xp 00000000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2c94000-b2c95000 r-xp 00001000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2c95000-b2c96000 rwxp 00002000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2c96000-b2c97000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b2c97000-b2c9d000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b2c9d000-b2c9f000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b2c9f000-b2ca2000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b2ca2000-b2ca5000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b2ca5000-b2ca6000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b2ca6000-b2caa000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b2caa000-b2cab000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b2cab000-b2cac000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b2cac000-b2cad000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b2cad000-b2cb1000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b2cb1000-b2cb5000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b2cb5000-b2cbc000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b2cbc000-b2cc7000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b2cc7000-b2cca000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b2cca000-b2cec000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b2cec000-b2cf0000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b2cf0000-b2cf3000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b2cf3000-b2d00000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b2d00000-b2dfd000 rwxp 00000000 00:00 0 
b2dfd000-b2e00000 ---p 00000000 00:00 0 
b2e02000-b2e08000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b2e08000-b2e0b000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b2e0b000-b2e13000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b2e13000-b2e1b000 r-xp 00000000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b2e1b000-b2e1c000 r-xp 00007000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b2e1c000-b2e1d000 rwxp 00008000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b2e1d000-b2e23000 r-xp 00000000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2e23000-b2e24000 r-xp 00005000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2e24000-b2e25000 rwxp 00006000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2e25000-b2e28000 ---p 00000000 00:00 0 
b2e28000-b2e76000 rwxp 00000000 00:00 0 
b2e76000-b2e79000 ---p 00000000 00:00 0 
b2e79000-b2ec7000 rwxp 00000000 00:00 0 
b2ec7000-b2f07000 rwxs 00010000 00:05 8271       /dev/ati/card0
b2f07000-b2f40000 r-xp 00000000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2f40000-b2f42000 rwxp 00038000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2f45000-b2f4a000 r-xp 00000000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2f4a000-b2f4b000 r-xp 00004000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2f4b000-b2f4c000 rwxp 00005000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2f4c000-b2f53000 r-xs 00000000 08:01 2225514    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b2f53000-b2f63000 rwxs d0000000 00:05 8271       /dev/ati/card0
b2f63000-b2f6a000 r-xp 00000000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b2f6a000-b2f6b000 rwxp 00006000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b2f6b000-b2f87000 r-xp 00000000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2f87000-b2f88000 r-xp 0001b000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2f88000-b2f89000 rwxp 0001c000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2f89000-b3052000 r-xp 00000000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b3052000-b305e000 rwxp 000c8000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b305e000-b3073000 rwxp 00000000 00:00 0 
b3073000-b3078000 r-xp 00000000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b3078000-b3079000 r-xp 00004000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b3079000-b307a000 rwxp 00005000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b307d000-b3080000 r-xp 00000000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b3080000-b3081000 r-xp 00002000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b3081000-b3082000 rwxp 00003000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b3082000-b3084000 rwxs 00002000 00:05 8271       /dev/ati/card0
b3084000-b30db000 r-xp 00000000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b30db000-b30dc000 r-xp 00056000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b30dc000-b30dd000 rwxp 00057000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b30dd000-b30e4000 r-xp 00000000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b30e4000-b30e5000 rwxp 00006000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b30e5000-b30f9000 r-xp 00000000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b30f9000-b30fa000 rwxp 00013000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b30fa000-b3127000 r-xp 00000000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3127000-b3128000 r-xp 0002c000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3128000-b3129000 rwxp 0002d000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b3129000-b312f000 r-xp 00000000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b312f000-b3130000 r-xp 00005000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b3130000-b3131000 rwxp 00006000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b3131000-b315a000 r-xp 00000000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b315a000-b315b000 r-xp 00028000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b315b000-b315c000 rwxp 00029000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b315c000-b3164000 r-xp 00000000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3164000-b3165000 r-xp 00008000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3165000-b3166000 rwxp 00009000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3166000-b3177000 r-xp 00000000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3177000-b3178000 r-xp 00010000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3178000-b3179000 rwxp 00011000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3179000-b3181000 r-xp 00000000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3181000-b3182000 r-xp 00007000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3182000-b3183000 rwxp 00008000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3183000-b3192000 r-xp 00000000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3192000-b3193000 r-xp 0000e000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3193000-b3194000 rwxp 0000f000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3194000-b3198000 r-xp 00000000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3198000-b3199000 r-xp 00003000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3199000-b319a000 rwxp 00004000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b319b000-b31a0000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b31a0000-b31a9000 r-xp 00000000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b31a9000-b31aa000 r-xp 00008000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b31aa000-b31ab000 rwxp 00009000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b31ab000-b31b0000 r-xp 00000000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b31b0000-b31b1000 r-xp 00004000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b31b1000-b31b2000 rwxp 00005000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b31b2000-b31ef000 r-xp 00000000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b31ef000-b31f0000 r-xp 0003c000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b31f0000-b31f1000 rwxp 0003d000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b31f1000-b31f6000 r-xp 00000000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b31f6000-b31f7000 r-xp 00004000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b31f7000-b31f8000 rwxp 00005000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b31f8000-b31fc000 r-xp 00000000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b31fc000-b31fd000 r-xp 00003000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b31fd000-b31fe000 rwxp 00004000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b31fe000-b3224000 r-xp 00000000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b3224000-b3225000 ---p 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b3225000-b3227000 r-xp 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b3227000-b3228000 rwxp 00028000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b3228000-b323b000 r-xp 00000000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b323b000-b323c000 r-xp 00012000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b323c000-b323d000 rwxp 00013000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b323d000-b323f000 rwxp 00000000 00:00 0 
b323f000-b325b000 r-xp 00000000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b325b000-b325c000 r-xp 0001b000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b325c000-b325d000 rwxp 0001c000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b325d000-b3270000 r-xp 00000000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3270000-b3271000 r-xp 00012000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3271000-b3272000 rwxp 00013000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3272000-b327a000 r-xp 00000000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b327a000-b327b000 r-xp 00007000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b327b000-b327c000 rwxp 00008000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b327c000-b327e000 r-xp 00000000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b327e000-b327f000 r-xp 00001000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b327f000-b3280000 rwxp 00002000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b3280000-b32a8000 r-xp 00000000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b32a8000-b32a9000 r-xp 00027000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b32a9000-b32aa000 rwxp 00028000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b32aa000-b3328000 r-xp 00000000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b3328000-b332c000 r-xp 0007d000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b332c000-b332d000 rwxp 00081000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b332d000-b33bf000 r-xp 00000000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b33bf000-b33c3000 r-xp 00091000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b33c3000-b33c4000 rwxp 00095000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b33c4000-b33c6000 r-xp 00000000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b33c6000-b33c7000 r-xp 00001000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b33c7000-b33c8000 rwxp 00002000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b33c8000-b33ca000 r-xp 00000000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b33ca000-b33cb000 r-xp 00001000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b33cb000-b33cc000 rwxp 00002000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b33cc000-b34c3000 r-xp 00000000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b34c3000-b34c4000 r-xp 000f6000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b34c4000-b34c5000 rwxp 000f7000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b34c5000-b3512000 r-xp 00000000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b3512000-b3513000 r-xp 0004d000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b3513000-b3514000 rwxp 0004e000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b3514000-b3546000 r-xp 00000000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b3546000-b3547000 ---p 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b3547000-b3548000 r-xp 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b3548000-b3549000 rwxp 00033000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b3549000-b3590000 r-xp 00000000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3590000-b3591000 r-xp 00047000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3591000-b3592000 rwxp 00048000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3592000-b36d4000 r-xp 00000000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b36d4000-b36d6000 r-xp 00142000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b36d6000-b36d7000 rwxp 00144000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b36d7000-b36d8000 rwxp 00000000 00:00 0 
b36d8000-b379f000 r-xp 00000000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b379f000-b37a0000 r-xp 000c7000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b37a0000-b37a1000 rwxp 000c8000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b37a1000-b37a3000 rwxp 00000000 00:00 0 
b37a3000-b384e000 r-xp 00000000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b384e000-b3850000 r-xp 000ab000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b3850000-b3851000 rwxp 000ad000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b3851000-b3cb2000 r-xp 00000000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3cb2000-b3cb6000 r-xp 00461000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3cb6000-b3cb8000 rwxp 00465000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3cb8000-b3cba000 rwxp 00000000 00:00 0 
b3cba000-b3cbb000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b3cbb000-b3cc1000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b3cc1000-b3cc3000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b3cc3000-b3cc6000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b3cc6000-b3cc9000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b3cc9000-b3cca000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b3cca000-b3cce000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b3cce000-b3ccf000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b3ccf000-b3cd0000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b3cd0000-b3cd1000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b3cd1000-b3cd5000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b3cd5000-b3cd9000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b3cd9000-b3ce0000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b3ce0000-b3ceb000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b3ceb000-b3cee000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b3cee000-b3cf0000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b3cf0000-b3cf1000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b3cf1000-b3d13000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b3d13000-b3d17000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b3d17000-b3d1a000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b3d1a000-b3d27000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b3d27000-b3d2d000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b3d2e000-b3d35000 r-xp 00000000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3d35000-b3d36000 r-xp 00006000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3d36000-b3d37000 rwxp 00007000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3d37000-b3d39000 r-xp 00000000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3d39000-b3d3a000 r-xp 00001000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3d3a000-b3d3b000 rwxp 00002000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3d3b000-b3d3e000 r-xp 00000000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3d3e000-b3d3f000 r-xp 00002000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3d3f000-b3d40000 rwxp 00003000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3d40000-b3d6b000 r-xp 00000000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3d6b000-b3d6c000 r-xp 0002a000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3d6c000-b3d6d000 rwxp 0002b000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3d6d000-b3d8b000 r-xp 00000000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3d8b000-b3d8c000 r-xp 0001d000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3d8c000-b3d8d000 rwxp 0001e000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3d8d000-b3daa000 r-xp 00000000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3daa000-b3dac000 r-xp 0001c000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3dac000-b3dad000 rwxp 0001e000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3dad000-b3db8000 r-xp 00000000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3db8000-b3db9000 r-xp 0000a000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3db9000-b3dba000 rwxp 0000b000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3dba000-b3dbd000 ---p 00000000 00:00 0 
b3dbd000-b3e0b000 rwxp 00000000 00:00 0 
b3e0b000-b3e0f000 r-xp 00000000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e0f000-b3e10000 r-xp 00003000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e10000-b3e11000 rwxp 00004000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e11000-b3e1a000 r-xp 00000000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e1a000-b3e1b000 r-xp 00008000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e1b000-b3e1c000 rwxp 00009000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e1c000-b3e25000 r-xp 00000000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e25000-b3e26000 r-xp 00008000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e26000-b3e27000 rwxp 00009000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e28000-b3e36000 r-xp 00000000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3e36000-b3e37000 r-xp 0000d000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3e37000-b3e38000 rwxp 0000e000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3e38000-b3eb1000 r-xp 00000000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3eb1000-b3ebb000 rwxp 00078000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3ebb000-b3ec0000 rwxp 00000000 00:00 0 
b3ec0000-b3ec5000 r-xp 00000000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3ec5000-b3ec6000 r-xp 00004000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3ec6000-b3ec7000 rwxp 00005000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3ec7000-b3ec9000 r-xp 00000000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3ec9000-b3eca000 r-xp 00001000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3eca000-b3ecb000 rwxp 00002000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3ecb000-b3ee8000 r-xp 00000000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3ee8000-b3ee9000 r-xp 0001c000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3ee9000-b3eea000 rwxp 0001d000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3eea000-b3ef8000 r-xp 00000000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3ef8000-b3ef9000 r-xp 0000d000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3ef9000-b3efa000 rwxp 0000e000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3efa000-b3eff000 r-xp 00000000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3eff000-b3f00000 r-xp 00004000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3f00000-b3f01000 rwxp 00005000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3f01000-b4032000 r-xp 00000000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b4032000-b4033000 ---p 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b4033000-b4034000 r-xp 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b4034000-b4036000 rwxp 00132000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b4036000-b4037000 rwxp 00000000 00:00 0 
b4037000-b4048000 r-xp 00000000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b4048000-b4049000 r-xp 00010000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b4049000-b404a000 rwxp 00011000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b404a000-b404b000 rwxs 00005000 00:05 8271       /dev/ati/card0
b404b000-b404e000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b404e000-b4056000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4056000-b405b000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b405b000-b40e0000 r-xp 00000000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b40e0000-b40e7000 rwxp 00085000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b40e7000-b410b000 rwxp 00000000 00:00 0 
b410b000-b410e000 ---p 00000000 00:00 0 
b410e000-b415c000 rwxp 00000000 00:00 0 
b415c000-b415d000 ---p 00000000 00:00 0 
b415d000-b41dd000 rwxp 00000000 00:00 0 
b41dd000-b41e0000 ---p 00000000 00:00 0 
b41e0000-b422e000 rwxp 00000000 00:00 0 
b422e000-b4231000 ---p 00000000 00:00 0 
b4231000-b42af000 rwxp 00000000 00:00 0 
b42af000-b42b2000 ---p 00000000 00:00 0 
b42b2000-b4300000 rwxp 00000000 00:00 0 
b4300000-b4500000 r-xp 00000000 08:01 2231284    /usr/lib/locale/locale-archive
b4500000-b4600000 rwxp 00000000 00:00 0 
b4600000-b4601000 r-xp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b4601000-b4602000 rwxp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b4602000-b4645000 r-xp 00000000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b4645000-b4647000 rwxp 00043000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b4647000-b4648000 rwxp 00000000 00:00 0 
b4648000-b4688000 r-xp 002bd000 08:01 2231284    /usr/lib/locale/locale-archive
b4688000-b468b000 ---p 00000000 00:00 0 
b468b000-b46d9000 rwxp 00000000 00:00 0 
b46d9000-b46dc000 ---p 00000000 00:00 0 
b46dc000-b475e000 rwxp 00000000 00:00 0 
b475e000-b48fa000 r-xs 030c2000 08:01 2245591    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/rt.jar
b48fa000-b48fb000 ---p 00000000 00:00 0 
b48fb000-b4989000 rwxp 00000000 00:00 0 
b4989000-b49a3000 rwxp 00000000 00:00 0 
b49a3000-b49bb000 rwxp 00000000 00:00 0 
b49bb000-b49f8000 rwxp 00000000 00:00 0 
b49f8000-b4a04000 rwxp 00000000 00:00 0 
b4a04000-b4a22000 rwxp 00000000 00:00 0 
b4a22000-b4a3a000 rwxp 00000000 00:00 0 
b4a3a000-b4a76000 rwxp 00000000 00:00 0 
b4a76000-b4a7c000 rwxp 00000000 00:00 0 
b4a7c000-b4a96000 rwxp 00000000 00:00 0 
b4a96000-b4aae000 rwxp 00000000 00:00 0 
b4aae000-b4b22000 rwxp 00000000 00:00 0 
b4b22000-b4e12000 rwxp 00000000 00:00 0 
b4e12000-b6b22000 rwxp 00000000 00:00 0 
b6b22000-b6b31000 r-xp 00000000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6b31000-b6b33000 rwxp 0000e000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6b33000-b6b3e000 r-xp 00000000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6b3e000-b6b3f000 r-xp 0000a000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6b3f000-b6b40000 rwxp 0000b000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6b40000-b6b4a000 r-xp 00000000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6b4a000-b6b4b000 r-xp 00009000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6b4b000-b6b4c000 rwxp 0000a000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6b4c000-b6b54000 r-xp 00000000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6b54000-b6b55000 r-xp 00007000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6b55000-b6b56000 rwxp 00008000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6b56000-b6b6b000 r-xp 00000000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6b6b000-b6b6c000 r-xp 00015000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6b6c000-b6b6d000 rwxp 00016000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6b6d000-b6b6f000 rwxp 00000000 00:00 0 
b6b6f000-b6b71000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b6b71000-b6b72000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b6b72000-b6b78000 rwxp 00000000 00:00 0 
b6b78000-b6b80000 rwxs 00000000 08:01 399786     /tmp/hsperfdata_hutriv/4980
b6b80000-b6ba3000 r-xp 00000000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6ba3000-b6ba5000 rwxp 00023000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6ba5000-b6bac000 r-xp 00000000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6bac000-b6bad000 r-xp 00006000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6bad000-b6bae000 rwxp 00007000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6bae000-b6bb1000 ---p 00000000 00:00 0 
b6bb1000-b6bff000 rwxp 00000000 00:00 0 
b6bff000-b6c27000 r-xp 00000000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c27000-b6c28000 r-xp 00028000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c28000-b6c29000 rwxp 00029000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c29000-b710a000 r-xp 00000000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b710a000-b712d000 rwxp 004e1000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b712d000-b754a000 rwxp 00000000 00:00 0 
b754a000-b76c2000 r-xp 00000000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b76c2000-b76c4000 r-xp 00178000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b76c4000-b76c5000 rwxp 0017a000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b76c5000-b76c8000 rwxp 00000000 00:00 0 
b76c8000-b76cb000 r-xp 00000000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b76cb000-b76cc000 r-xp 00002000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b76cc000-b76cd000 rwxp 00003000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b76cd000-b76d4000 r-xp 00000000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b76d4000-b76d6000 rwxp 00006000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b76d6000-b76d7000 rwxp 00000000 00:00 0 
b76d7000-b76ee000 r-xp 00000000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b76ee000-b76ef000 r-xp 00016000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b76ef000-b76f0000 rwxp 00017000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b76f0000-b76f2000 rwxp 00000000 00:00 0 
b76f2000-b76f4000 r-xs 00016000 08:01 2231027    /home/hutriv/Minecraft.jar
b76f4000-b76f5000 r-xp 0043a000 08:01 2231284    /usr/lib/locale/locale-archive
b76f5000-b76f6000 rwxp 00000000 00:00 0 
b76f6000-b76f7000 ---p 00000000 00:00 0 
b76f7000-b7702000 r-xp 00000000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b7702000-b7703000 rwxp 0000b000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b7703000-b7705000 rwxp 00000000 00:00 0 
b7705000-b7706000 r-xp 00000000 00:00 0          [vdso]
b7706000-b7724000 r-xp 00000000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b7724000-b7725000 r-xp 0001d000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b7725000-b7726000 rwxp 0001e000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
bff42000-bff63000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/hutriv/Minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=hutriv
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x38f030], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC 7897, NOFILE 4096, AS infinity
load average:0.38 0.34 0.36

/proc/meminfo:
MemTotal:        1024968 kB
MemFree:           69712 kB
Buffers:           11836 kB
Cached:           152988 kB
SwapCached:        15948 kB
Active:           413732 kB
Inactive:         373820 kB
Active(anon):     316720 kB
Inactive(anon):   312068 kB
Active(file):      97012 kB
Inactive(file):    61752 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138184 kB
HighFree:           1832 kB
LowTotal:         886784 kB
LowFree:           67880 kB
SwapTotal:       1046524 kB
SwapFree:         947676 kB
Dirty:               556 kB
Writeback:             0 kB
AnonPages:        609360 kB
Mapped:           148832 kB
Shmem:              6004 kB
Slab:              29972 kB
SReclaimable:      17136 kB
SUnreclaim:        12836 kB
KernelStack:        2816 kB
PageTables:         7460 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1559008 kB
Committed_AS:    2365500 kB
VmallocTotal:     122880 kB
VmallocUsed:       30116 kB
VmallocChunk:      87508 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      106488 kB
DirectMap4M:      802816 kB


CPU:total 2 (1 cores per cpu, 2 threads per core) family 15 model 4 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ht

/proc/cpuinfo:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6387.41
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6388.43
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:



Memory: 4k page, physical 1024968k(69712k free), swap 1046524k(947676k free)

vm_info: Java HotSpot(TM) Client VM (20.6-b01) for linux-x86 JRE (1.6.0_31-b04), built on Jan 20 2012 10:30:33 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sat Apr  7 12:22:19 2012
elapsed time: 30 seconds
```

---

### Post by hutriv on 2012-04-07
THIS ERROR IS SPECIFICALLY FROM SINGLE-PLAYER
```
 
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7778416, pid=5487, tid=2972896112
#
# JRE version: 6.0_31-b04
# Java VM: Java HotSpot(TM) Client VM (20.6-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x0000156f

Registers:
EAX=0x00000000, EBX=0x0000156f, ECX=0x00001596, EDX=0x0000000b
ESP=0xb132c28c, EBP=0xb132c398, ESI=0x00000020, EDI=0xb7761ff4
EIP=0xb7778416, EFLAGS=0x00200206, CR2=0xb7769100

Top of Stack: (sp=0xb132c28c)
0xb132c28c:   b7758e6e b7761ff4 b1008880 b09e8743
0xb132c29c:   0000000b 00000000 00000000 00000000
0xb132c2ac:   00001000 00000000 00000000 00000000
0xb132c2bc:   00000000 00000000 7fffffff fffffffe
0xb132c2cc:   ffffffff ffffffff ffffffff ffffffff
0xb132c2dc:   ffffffff ffffffff ffffffff ffffffff
0xb132c2ec:   ffffffff ffffffff ffffffff ffffffff
0xb132c2fc:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb7778416)
0xb77783f6:   00 00 00 00 00 00 00 00 00 00 58 b8 77 00 00 00
0xb7778406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0xb7778416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73
0xb7778426:   68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 6e 73 74 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x0000156f is an unknown value
ECX=0x00001596 is an unknown value
EDX=0x0000000b is an unknown value
ESP=0xb132c28c is an unknown value
EBP=0xb132c398 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb7761ff4: <offset 0x17ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb774a000


Stack: [0xb131c000,0xb132d000],  sp=0xb132c28c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [libpthread.so.0+0x6d31]
[error occurred during error reporting (printing native stack), id 0xb]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 21952K, used 3582K [0x7f080000, 0x80850000, 0x84480000)
  eden space 19520K,   5% used [0x7f080000, 0x7f19f888, 0x80390000)
  from space 2432K, 100% used [0x805f0000, 0x80850000, 0x80850000)
  to   space 2432K,   0% used [0x80390000, 0x80390000, 0x805f0000)
 tenured generation   total 48716K, used 32312K [0x84480000, 0x87413000, 0x8ec80000)
   the space 48716K,  66% used [0x84480000, 0x8640e328, 0x8640e400, 0x87413000)
 compacting perm gen  total 12288K, used 8983K [0x8ec80000, 0x8f880000, 0x92c80000)
   the space 12288K,  73% used [0x8ec80000, 0x8f545cb0, 0x8f545e00, 0x8f880000)
    ro space 10240K,  61% used [0x92c80000, 0x932a9838, 0x932a9a00, 0x93680000)
    rw space 12288K,  60% used [0x93680000, 0x93dba040, 0x93dba200, 0x94280000)

Code Cache  [0xb4b95000, 0xb4e9d000, 0xb6b95000)
 total_blobs=1761 nmethods=1393 adapters=302 free_code_cache=30403840 largest_free_block=192

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
08d49000-0921c000 rwxp 00000000 00:00 0          [heap]
7f080000-80850000 rwxp 00000000 00:00 0 
80850000-84480000 rwxp 00000000 00:00 0 
84480000-87413000 rwxp 00000000 00:00 0 
87413000-8ec80000 rwxp 00000000 00:00 0 
8ec80000-8f880000 rwxp 00000000 00:00 0 
8f880000-92c80000 rwxp 00000000 00:00 0 
92c80000-932aa000 r-xs 00001000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
932aa000-93680000 rwxp 00000000 00:00 0 
93680000-93dbb000 rwxp 0062b000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
93dbb000-94280000 rwxp 00000000 00:00 0 
94280000-94362000 rwxp 00d66000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94362000-94680000 rwxp 00000000 00:00 0 
94680000-94688000 r-xs 00e48000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94688000-94a80000 rwxp 00000000 00:00 0 
9cdff000-9ce00000 ---p 00000000 00:00 0 
9ce00000-9d000000 rwxp 00000000 00:00 0 
9d000000-9d0ef000 rwxp 00000000 00:00 0 
9d0ef000-9d100000 ---p 00000000 00:00 0 
9d200000-9d300000 rwxp 00000000 00:00 0 
9d400000-9d4e8000 rwxp 00000000 00:00 0 
9d4e8000-9d500000 ---p 00000000 00:00 0 
9d51e000-9d521000 ---p 00000000 00:00 0 
9d521000-a75af000 rwxp 00000000 00:00 0 
a75af000-a75b0000 ---p 00000000 00:00 0 
a75b0000-a7db0000 rwxp 00000000 00:00 0 
a7db0000-a7db1000 ---p 00000000 00:00 0 
a7db1000-a85b1000 rwxp 00000000 00:00 0 
a85b1000-ac5b2000 rwxs 00000000 00:12 71435      /run/shm/pulse-shm-1396108646
ac5b2000-ac718000 r-xp 00000000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac718000-ac729000 r-xp 00165000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac729000-ac72a000 rwxp 00176000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac72a000-ac776000 r-xp 00000000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac776000-ac777000 r-xp 0004b000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac777000-ac778000 rwxp 0004c000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac778000-ac7e3000 r-xp 00000000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac7e3000-ac7e4000 r-xp 0006b000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac7e4000-ac7e5000 rwxp 0006c000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac7e5000-ac7e9000 rwxp 00000000 00:00 0 
ac7e9000-ac80e000 r-xp 00000000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
ac80e000-ac80f000 rwxp 00025000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
ac80f000-ac8fc000 rwxp 00000000 00:00 0 
ac8fc000-ac9fc000 rwxs 091c4000 00:05 8271       /dev/ati/card0
ac9fc000-acbfc000 rwxs c4678000 00:05 8271       /dev/ati/card0
acbfc000-ae400000 rwxp 00000000 00:00 0 
ae400000-ae4ef000 rwxp 00000000 00:00 0 
ae4ef000-ae500000 ---p 00000000 00:00 0 
ae500000-ae5c4000 rwxp 00000000 00:00 0 
ae5c4000-ae600000 ---p 00000000 00:00 0 
ae600000-ae6ee000 rwxp 00000000 00:00 0 
ae6ee000-ae700000 ---p 00000000 00:00 0 
ae70f000-ae7fb000 r-xp 00000000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ae7fb000-ae7ff000 r-xp 000eb000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ae7ff000-ae800000 rwxp 000ef000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ae800000-ae8ff000 rwxp 00000000 00:00 0 
ae8ff000-ae900000 ---p 00000000 00:00 0 
ae920000-ae983000 r-xp 00000000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ae983000-ae984000 r-xp 00062000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ae984000-ae985000 rwxp 00063000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
ae985000-ae9c5000 rwxs 00010000 00:05 8271       /dev/ati/card0
ae9c5000-af0c5000 rwxs 00006000 00:05 8271       /dev/ati/card0
af0c5000-b0e7f000 r-xp 00000000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b0e7f000-b0f4a000 rwxp 01db9000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b0f4a000-b100a000 rwxp 00000000 00:00 0 
b100a000-b119b000 rwxs 00000000 00:04 20643852   /SYSV00000000 (deleted)
b119b000-b1200000 rwxs 00000000 00:04 20611083   /SYSV00000000 (deleted)
b1200000-b12e8000 rwxp 00000000 00:00 0 
b12e8000-b1300000 ---p 00000000 00:00 0 
b131c000-b131d000 ---p 00000000 00:00 0 
b131d000-b132d000 rwxp 00000000 00:00 0 
b132d000-b1335000 r-xp 00000000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b1335000-b1336000 r-xp 00007000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b1336000-b1337000 rwxp 00008000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b1337000-b134e000 r-xs 003c2000 08:01 274284     /home/hutriv/.minecraft/bin/minecraft.jar
b134e000-b1351000 r-xs 0001f000 08:01 274283     /home/hutriv/.minecraft/bin/lwjgl_util.jar
b1351000-b1354000 ---p 00000000 00:00 0 
b1354000-b13a2000 rwxp 00000000 00:00 0 
b13a2000-b13a5000 ---p 00000000 00:00 0 
b13a5000-b13f3000 rwxp 00000000 00:00 0 
b13f3000-b1584000 rwxs 00000000 00:04 19234826   /SYSV00000000 (deleted)
b1586000-b158b000 r-xs 00033000 08:01 274282     /home/hutriv/.minecraft/bin/jinput.jar
b158b000-b1594000 r-xs 000ac000 08:01 274281     /home/hutriv/.minecraft/bin/lwjgl.jar
b1594000-b1800000 rwxp 00000000 00:00 0 
b1800000-b18fa000 rwxp 00000000 00:00 0 
b18fa000-b1900000 ---p 00000000 00:00 0 
b1904000-b190a000 r-xp 00000000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b190a000-b190b000 r-xp 00005000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b190b000-b190c000 rwxp 00006000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b190c000-b196c000 rwxs 00000000 00:04 18907142   /SYSV00000000 (deleted)
b196c000-b196f000 r-xs 000cc000 08:01 280947     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/localedata.jar
b196f000-b1972000 ---p 00000000 00:00 0 
b1972000-b19c0000 rwxp 00000000 00:00 0 
b19c0000-b19c3000 ---p 00000000 00:00 0 
b19c3000-b1a11000 rwxp 00000000 00:00 0 
b1a11000-b1a19000 r-xs 00115000 08:01 2245514    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/resources.jar
b1a19000-b1a1f000 r-xs 00095000 08:01 2245562    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jsse.jar
b1a1f000-b1a22000 ---p 00000000 00:00 0 
b1a22000-b1a70000 rwxp 00000000 00:00 0 
b1a70000-b1a73000 ---p 00000000 00:00 0 
b1a73000-b1ac1000 rwxp 00000000 00:00 0 
b1ac1000-b1ac4000 ---p 00000000 00:00 0 
b1ac4000-b1b12000 rwxp 00000000 00:00 0 
b1b12000-b1b13000 ---p 00000000 00:00 0 
b1b13000-b2313000 rwxp 00000000 00:00 0 
b2313000-b2314000 ---p 00000000 00:00 0 
b2314000-b2b14000 rwxp 00000000 00:00 0 
b2b14000-b2b2c000 r-xp 00000000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b2c000-b2b2d000 r-xp 00017000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b2d000-b2b2e000 rwxp 00018000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b2e000-b2b3e000 r-xp 00000000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b3e000-b2b3f000 ---p 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b3f000-b2b40000 r-xp 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b40000-b2b41000 rwxp 00011000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b41000-b2b44000 r-xs 00027000 08:01 280946     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/sunjce_provider.jar
b2b44000-b2b49000 r-xp 00000000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b49000-b2b4a000 r-xp 00004000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b4a000-b2b4b000 rwxp 00005000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b4b000-b2b4d000 r-xp 00000000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b4d000-b2b4e000 r-xp 00001000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b4e000-b2b4f000 rwxp 00002000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b4f000-b2b52000 r-xs 00013000 08:01 2245530    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jce.jar
b2b52000-b2b65000 r-xp 00000000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b65000-b2b66000 r-xp 00012000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b66000-b2b67000 rwxp 00013000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b67000-b2b77000 r-xp 00000000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b77000-b2b78000 r-xp 0000f000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b78000-b2b79000 rwxp 00010000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2b79000-b2bc0000 r-xp 00000000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bc0000-b2bc1000 r-xp 00046000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bc1000-b2bc2000 rwxp 00047000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bc2000-b2bd7000 r-xp 00000000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2bd7000-b2bd8000 r-xp 00015000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2bd8000-b2bd9000 rwxp 00016000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2bd9000-b2c03000 r-xp 00000000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2c03000-b2c04000 r-xp 00029000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2c04000-b2c05000 rwxp 0002a000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2c05000-b2c44000 r-xp 00000000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c44000-b2c45000 r-xp 0003f000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c45000-b2c46000 rwxp 00040000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c48000-b2c4c000 r-xp 00000000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2c4c000-b2c4d000 r-xp 00004000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2c4d000-b2c4e000 rwxp 00005000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2c4e000-b2c55000 r-xp 00000000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2c55000-b2c56000 r-xp 00006000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2c56000-b2c57000 rwxp 00007000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2c57000-b2ca9000 r-xp 00000000 08:01 527586     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b2ca9000-b2d00000 r-xp 00000000 08:01 527633     /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b2d00000-b2e00000 rwxp 00000000 00:00 0 
b2e00000-b2e05000 r-xp 00000000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e05000-b2e06000 ---p 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e06000-b2e07000 r-xp 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e07000-b2e08000 rwxp 00006000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e08000-b2e0a000 r-xp 00000000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e0a000-b2e0b000 r-xp 00001000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e0b000-b2e0c000 rwxp 00002000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e0c000-b2e0d000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b2e0d000-b2e13000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b2e13000-b2e15000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b2e15000-b2e18000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b2e18000-b2e1b000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b2e1b000-b2e1c000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b2e1c000-b2e20000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b2e20000-b2e21000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b2e21000-b2e22000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b2e22000-b2e23000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b2e23000-b2e27000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b2e27000-b2e2b000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b2e2b000-b2e32000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b2e32000-b2e3d000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b2e3d000-b2e40000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b2e40000-b2e42000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b2e42000-b2e43000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b2e43000-b2e65000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b2e65000-b2e69000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b2e69000-b2e6c000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b2e6c000-b2e79000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b2e79000-b2e7f000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b2e7f000-b2e82000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b2e82000-b2e8a000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b2e8c000-b2ed8000 r-xp 00000000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b2ed8000-b2ed9000 r-xp 0004b000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b2ed9000-b2eda000 rwxp 0004c000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b2eda000-b2edd000 ---p 00000000 00:00 0 
b2edd000-b2f2b000 rwxp 00000000 00:00 0 
b2f2b000-b2f2e000 ---p 00000000 00:00 0 
b2f2e000-b2f7c000 rwxp 00000000 00:00 0 
b2f7c000-b2fb5000 r-xp 00000000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2fb5000-b2fb7000 rwxp 00038000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2fba000-b2fbf000 r-xp 00000000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fbf000-b2fc0000 r-xp 00004000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fc0000-b2fc1000 rwxp 00005000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fc1000-b2fc8000 r-xs 00000000 08:01 2225514    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b2fc8000-b2fd8000 rwxs d0000000 00:05 8271       /dev/ati/card0
b2fd8000-b2fdf000 r-xp 00000000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b2fdf000-b2fe0000 rwxp 00006000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b2fe0000-b2ffc000 r-xp 00000000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2ffc000-b2ffd000 r-xp 0001b000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2ffd000-b2ffe000 rwxp 0001c000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b2ffe000-b30c7000 r-xp 00000000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b30c7000-b30d3000 rwxp 000c8000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b30d3000-b30e8000 rwxp 00000000 00:00 0 
b30e8000-b30ed000 r-xp 00000000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b30ed000-b30ee000 r-xp 00004000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b30ee000-b30ef000 rwxp 00005000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b30f2000-b30f5000 r-xp 00000000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b30f5000-b30f6000 r-xp 00002000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b30f6000-b30f7000 rwxp 00003000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b30f7000-b30f9000 rwxs 00002000 00:05 8271       /dev/ati/card0
b30f9000-b30fa000 r-xp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b30fa000-b30fb000 rwxp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b30fb000-b3152000 r-xp 00000000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b3152000-b3153000 r-xp 00056000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b3153000-b3154000 rwxp 00057000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b3154000-b315b000 r-xp 00000000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b315b000-b315c000 rwxp 00006000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b315c000-b3170000 r-xp 00000000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b3170000-b3171000 rwxp 00013000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b3171000-b319e000 r-xp 00000000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b319e000-b319f000 r-xp 0002c000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b319f000-b31a0000 rwxp 0002d000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b31a0000-b31a6000 r-xp 00000000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31a6000-b31a7000 r-xp 00005000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31a7000-b31a8000 rwxp 00006000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31a8000-b31d1000 r-xp 00000000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31d1000-b31d2000 r-xp 00028000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31d2000-b31d3000 rwxp 00029000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31d3000-b31db000 r-xp 00000000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b31db000-b31dc000 r-xp 00008000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b31dc000-b31dd000 rwxp 00009000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b31dd000-b31ee000 r-xp 00000000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b31ee000-b31ef000 r-xp 00010000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b31ef000-b31f0000 rwxp 00011000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b31f0000-b31f8000 r-xp 00000000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b31f8000-b31f9000 r-xp 00007000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b31f9000-b31fa000 rwxp 00008000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b31fa000-b3209000 r-xp 00000000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3209000-b320a000 r-xp 0000e000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b320a000-b320b000 rwxp 0000f000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b320b000-b320f000 r-xp 00000000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b320f000-b3210000 r-xp 00003000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3210000-b3211000 rwxp 00004000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3212000-b3217000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b3217000-b3220000 r-xp 00000000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b3220000-b3221000 r-xp 00008000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b3221000-b3222000 rwxp 00009000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b3222000-b3227000 r-xp 00000000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3227000-b3228000 r-xp 00004000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3228000-b3229000 rwxp 00005000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3229000-b3266000 r-xp 00000000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b3266000-b3267000 r-xp 0003c000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b3267000-b3268000 rwxp 0003d000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b3268000-b326d000 r-xp 00000000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b326d000-b326e000 r-xp 00004000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b326e000-b326f000 rwxp 00005000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b326f000-b3273000 r-xp 00000000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b3273000-b3274000 r-xp 00003000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b3274000-b3275000 rwxp 00004000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b3275000-b329b000 r-xp 00000000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b329b000-b329c000 ---p 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b329c000-b329e000 r-xp 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b329e000-b329f000 rwxp 00028000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b329f000-b32b2000 r-xp 00000000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32b2000-b32b3000 r-xp 00012000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32b3000-b32b4000 rwxp 00013000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32b4000-b32b6000 rwxp 00000000 00:00 0 
b32b6000-b32d2000 r-xp 00000000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32d2000-b32d3000 r-xp 0001b000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32d3000-b32d4000 rwxp 0001c000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32d4000-b32e7000 r-xp 00000000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b32e7000-b32e8000 r-xp 00012000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b32e8000-b32e9000 rwxp 00013000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b32e9000-b32f1000 r-xp 00000000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b32f1000-b32f2000 r-xp 00007000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b32f2000-b32f3000 rwxp 00008000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b32f3000-b32f5000 r-xp 00000000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b32f5000-b32f6000 r-xp 00001000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b32f6000-b32f7000 rwxp 00002000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b32f7000-b331f000 r-xp 00000000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b331f000-b3320000 r-xp 00027000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b3320000-b3321000 rwxp 00028000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b3321000-b339f000 r-xp 00000000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b339f000-b33a3000 r-xp 0007d000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b33a3000-b33a4000 rwxp 00081000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b33a4000-b3436000 r-xp 00000000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b3436000-b343a000 r-xp 00091000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b343a000-b343b000 rwxp 00095000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b343b000-b343d000 r-xp 00000000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b343d000-b343e000 r-xp 00001000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b343e000-b343f000 rwxp 00002000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b343f000-b3441000 r-xp 00000000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b3441000-b3442000 r-xp 00001000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b3442000-b3443000 rwxp 00002000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b3443000-b353a000 r-xp 00000000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b353a000-b353b000 r-xp 000f6000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b353b000-b353c000 rwxp 000f7000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b353c000-b3589000 r-xp 00000000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b3589000-b358a000 r-xp 0004d000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b358a000-b358b000 rwxp 0004e000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b358b000-b35bd000 r-xp 00000000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35bd000-b35be000 ---p 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35be000-b35bf000 r-xp 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35bf000-b35c0000 rwxp 00033000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35c0000-b3607000 r-xp 00000000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3607000-b3608000 r-xp 00047000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3608000-b3609000 rwxp 00048000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3609000-b374b000 r-xp 00000000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b374b000-b374d000 r-xp 00142000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b374d000-b374e000 rwxp 00144000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b374e000-b374f000 rwxp 00000000 00:00 0 
b374f000-b3816000 r-xp 00000000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b3816000-b3817000 r-xp 000c7000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b3817000-b3818000 rwxp 000c8000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b3818000-b381a000 rwxp 00000000 00:00 0 
b381a000-b38c5000 r-xp 00000000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38c5000-b38c7000 r-xp 000ab000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38c7000-b38c8000 rwxp 000ad000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38c8000-b3d29000 r-xp 00000000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d29000-b3d2d000 r-xp 00461000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d2d000-b3d2f000 rwxp 00465000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d2f000-b3d31000 rwxp 00000000 00:00 0 
b3d31000-b3d32000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b3d32000-b3d38000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b3d38000-b3d3a000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b3d3a000-b3d3d000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b3d3d000-b3d40000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b3d40000-b3d41000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b3d41000-b3d45000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b3d45000-b3d46000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b3d46000-b3d47000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b3d47000-b3d48000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b3d48000-b3d4c000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b3d4c000-b3d50000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b3d50000-b3d57000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b3d57000-b3d62000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b3d62000-b3d65000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b3d65000-b3d87000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b3d87000-b3d8b000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b3d8b000-b3d8e000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b3d8e000-b3d9b000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b3d9b000-b3da1000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b3da2000-b3da9000 r-xp 00000000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3da9000-b3daa000 r-xp 00006000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3daa000-b3dab000 rwxp 00007000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3dab000-b3dad000 r-xp 00000000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3dad000-b3dae000 r-xp 00001000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3dae000-b3daf000 rwxp 00002000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3daf000-b3db2000 r-xp 00000000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3db2000-b3db3000 r-xp 00002000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3db3000-b3db4000 rwxp 00003000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3db4000-b3ddf000 r-xp 00000000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3ddf000-b3de0000 r-xp 0002a000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3de0000-b3de1000 rwxp 0002b000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3de1000-b3dff000 r-xp 00000000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3dff000-b3e00000 r-xp 0001d000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3e00000-b3e01000 rwxp 0001e000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3e01000-b3e1e000 r-xp 00000000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e1e000-b3e20000 r-xp 0001c000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e20000-b3e21000 rwxp 0001e000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e21000-b3e2c000 r-xp 00000000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e2c000-b3e2d000 r-xp 0000a000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e2d000-b3e2e000 rwxp 0000b000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e2e000-b3e31000 ---p 00000000 00:00 0 
b3e31000-b3e7f000 rwxp 00000000 00:00 0 
b3e7f000-b3e83000 r-xp 00000000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e83000-b3e84000 r-xp 00003000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e84000-b3e85000 rwxp 00004000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3e85000-b3e8e000 r-xp 00000000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e8e000-b3e8f000 r-xp 00008000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e8f000-b3e90000 rwxp 00009000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3e90000-b3e99000 r-xp 00000000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e99000-b3e9a000 r-xp 00008000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e9a000-b3e9b000 rwxp 00009000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3e9c000-b3eaa000 r-xp 00000000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3eaa000-b3eab000 r-xp 0000d000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3eab000-b3eac000 rwxp 0000e000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3eac000-b3f25000 r-xp 00000000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3f25000-b3f2f000 rwxp 00078000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3f2f000-b3f34000 rwxp 00000000 00:00 0 
b3f34000-b3f39000 r-xp 00000000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f39000-b3f3a000 r-xp 00004000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f3a000-b3f3b000 rwxp 00005000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f3b000-b3f3d000 r-xp 00000000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f3d000-b3f3e000 r-xp 00001000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f3e000-b3f3f000 rwxp 00002000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f3f000-b3f5c000 r-xp 00000000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f5c000-b3f5d000 r-xp 0001c000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f5d000-b3f5e000 rwxp 0001d000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f5e000-b3f6c000 r-xp 00000000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f6c000-b3f6d000 r-xp 0000d000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f6d000-b3f6e000 rwxp 0000e000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f6e000-b409f000 r-xp 00000000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b409f000-b40a0000 ---p 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40a0000-b40a1000 r-xp 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40a1000-b40a3000 rwxp 00132000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40a3000-b40a4000 rwxp 00000000 00:00 0 
b40a4000-b40b5000 r-xp 00000000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40b5000-b40b6000 r-xp 00010000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40b6000-b40b7000 rwxp 00011000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40b7000-b40fa000 r-xp 00000000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b40fa000-b40fc000 rwxp 00043000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b40fc000-b40fd000 rwxp 00000000 00:00 0 
b40fd000-b4182000 r-xp 00000000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b4182000-b4189000 rwxp 00085000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b4189000-b41ad000 rwxp 00000000 00:00 0 
b41ad000-b41b0000 ---p 00000000 00:00 0 
b41b0000-b41fe000 rwxp 00000000 00:00 0 
b41fe000-b41ff000 ---p 00000000 00:00 0 
b41ff000-b427f000 rwxp 00000000 00:00 0 
b427f000-b4282000 ---p 00000000 00:00 0 
b4282000-b4300000 rwxp 00000000 00:00 0 
b4300000-b4500000 r-xp 00000000 08:01 2231284    /usr/lib/locale/locale-archive
b4500000-b45ff000 rwxp 00000000 00:00 0 
b45ff000-b4600000 ---p 00000000 00:00 0 
b4600000-b4601000 rwxp 00000000 00:00 0 
b4601000-b4606000 r-xp 00000000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b4606000-b4607000 r-xp 00004000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b4607000-b4608000 rwxp 00005000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b4608000-b4609000 rwxs 00005000 00:05 8271       /dev/ati/card0
b4609000-b460c000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b460c000-b4614000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4614000-b4619000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4619000-b461c000 ---p 00000000 00:00 0 
b461c000-b466a000 rwxp 00000000 00:00 0 
b466a000-b466d000 ---p 00000000 00:00 0 
b466d000-b46bb000 rwxp 00000000 00:00 0 
b46bb000-b46fb000 r-xp 002bd000 08:01 2231284    /usr/lib/locale/locale-archive
b46fb000-b46fe000 ---p 00000000 00:00 0 
b46fe000-b474c000 rwxp 00000000 00:00 0 
b474c000-b474f000 ---p 00000000 00:00 0 
b474f000-b47d1000 rwxp 00000000 00:00 0 
b47d1000-b496d000 r-xs 030c2000 08:01 2245591    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/rt.jar
b496d000-b496e000 ---p 00000000 00:00 0 
b496e000-b49fc000 rwxp 00000000 00:00 0 
b49fc000-b4a16000 rwxp 00000000 00:00 0 
b4a16000-b4a2e000 rwxp 00000000 00:00 0 
b4a2e000-b4a6b000 rwxp 00000000 00:00 0 
b4a6b000-b4a77000 rwxp 00000000 00:00 0 
b4a77000-b4a95000 rwxp 00000000 00:00 0 
b4a95000-b4aad000 rwxp 00000000 00:00 0 
b4aad000-b4ae9000 rwxp 00000000 00:00 0 
b4ae9000-b4aef000 rwxp 00000000 00:00 0 
b4aef000-b4b09000 rwxp 00000000 00:00 0 
b4b09000-b4b22000 rwxp 00000000 00:00 0 
b4b22000-b4b95000 rwxp 00000000 00:00 0 
b4b95000-b4e9d000 rwxp 00000000 00:00 0 
b4e9d000-b6b95000 rwxp 00000000 00:00 0 
b6b95000-b6ba4000 r-xp 00000000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6ba4000-b6ba6000 rwxp 0000e000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6ba6000-b6bb1000 r-xp 00000000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bb1000-b6bb2000 r-xp 0000a000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bb2000-b6bb3000 rwxp 0000b000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bb3000-b6bbd000 r-xp 00000000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6bbd000-b6bbe000 r-xp 00009000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6bbe000-b6bbf000 rwxp 0000a000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6bbf000-b6bc7000 r-xp 00000000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bc7000-b6bc8000 r-xp 00007000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bc8000-b6bc9000 rwxp 00008000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bc9000-b6bde000 r-xp 00000000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6bde000-b6bdf000 r-xp 00015000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6bdf000-b6be0000 rwxp 00016000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6be0000-b6be2000 rwxp 00000000 00:00 0 
b6be2000-b6be4000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b6be4000-b6be5000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b6be5000-b6beb000 rwxp 00000000 00:00 0 
b6beb000-b6bf3000 rwxs 00000000 08:01 402203     /tmp/hsperfdata_hutriv/5487
b6bf3000-b6c16000 r-xp 00000000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6c16000-b6c18000 rwxp 00023000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6c18000-b6c1f000 r-xp 00000000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c1f000-b6c20000 r-xp 00006000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c20000-b6c21000 rwxp 00007000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c21000-b6c24000 ---p 00000000 00:00 0 
b6c24000-b6c72000 rwxp 00000000 00:00 0 
b6c72000-b6c9a000 r-xp 00000000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c9a000-b6c9b000 r-xp 00028000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c9b000-b6c9c000 rwxp 00029000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6c9c000-b717d000 r-xp 00000000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b717d000-b71a0000 rwxp 004e1000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b71a0000-b75bd000 rwxp 00000000 00:00 0 
b75bd000-b7735000 r-xp 00000000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b7735000-b7737000 r-xp 00178000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b7737000-b7738000 rwxp 0017a000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b7738000-b773b000 rwxp 00000000 00:00 0 
b773b000-b773e000 r-xp 00000000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b773e000-b773f000 r-xp 00002000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b773f000-b7740000 rwxp 00003000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b7740000-b7747000 r-xp 00000000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b7747000-b7749000 rwxp 00006000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b7749000-b774a000 rwxp 00000000 00:00 0 
b774a000-b7761000 r-xp 00000000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b7761000-b7762000 r-xp 00016000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b7762000-b7763000 rwxp 00017000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b7763000-b7765000 rwxp 00000000 00:00 0 
b7765000-b7767000 r-xs 00016000 08:01 2231027    /home/hutriv/Minecraft.jar
b7767000-b7768000 r-xp 0043a000 08:01 2231284    /usr/lib/locale/locale-archive
b7768000-b7769000 rwxp 00000000 00:00 0 
b7769000-b776a000 r-xp 00000000 00:00 0 
b776a000-b7775000 r-xp 00000000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b7775000-b7776000 rwxp 0000b000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b7776000-b7778000 rwxp 00000000 00:00 0 
b7778000-b7779000 r-xp 00000000 00:00 0          [vdso]
b7779000-b7797000 r-xp 00000000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b7797000-b7798000 r-xp 0001d000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b7798000-b7799000 rwxp 0001e000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
bfd98000-bfdb9000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/hutriv/Minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=hutriv
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x38f030], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC 7897, NOFILE 4096, AS infinity
load average:1.06 0.48 0.27

/proc/meminfo:
MemTotal:        1024968 kB
MemFree:           66928 kB
Buffers:            2152 kB
Cached:           121988 kB
SwapCached:        29156 kB
Active:           392444 kB
Inactive:         395192 kB
Active(anon):     335124 kB
Inactive(anon):   335368 kB
Active(file):      57320 kB
Inactive(file):    59824 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138184 kB
HighFree:           3604 kB
LowTotal:         886784 kB
LowFree:           63324 kB
SwapTotal:       1046524 kB
SwapFree:         924244 kB
Dirty:               564 kB
Writeback:             0 kB
AnonPages:        638592 kB
Mapped:           132824 kB
Shmem:              6980 kB
Slab:              26480 kB
SReclaimable:      13408 kB
SUnreclaim:        13072 kB
KernelStack:        2944 kB
PageTables:         8304 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1559008 kB
Committed_AS:    2543848 kB
VmallocTotal:     122880 kB
VmallocUsed:       30116 kB
VmallocChunk:      87508 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      106488 kB
DirectMap4M:      802816 kB


CPU:total 2 (1 cores per cpu, 2 threads per core) family 15 model 4 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ht

/proc/cpuinfo:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6387.41
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6388.43
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:



Memory: 4k page, physical 1024968k(66928k free), swap 1046524k(924244k free)

vm_info: Java HotSpot(TM) Client VM (20.6-b01) for linux-x86 JRE (1.6.0_31-b04), built on Jan 20 2012 10:30:33 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sat Apr  7 12:53:13 2012
elapsed time: 25 seconds
```

---

### Post by hutriv on 2012-04-07
THIS IS SPECIFICALLY A MULTIPLAYER ERROR!!
```


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb77a1416, pid=5624, tid=2979421040
#
# JRE version: 6.0_31-b04
# Java VM: Java HotSpot(TM) Client VM (20.6-b01 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=-6 (FPE_FLTOVF), si_addr=0x000015f8

Registers:
EAX=0x00000000, EBX=0x000015f8, ECX=0x00001622, EDX=0x0000000b
ESP=0xb196528c, EBP=0xb1965398, ESI=0x00000020, EDI=0xb778aff4
EIP=0xb77a1416, EFLAGS=0x00200202, CR2=0x00000004

Top of Stack: (sp=0xb196528c)
0xb196528c:   b7781e6e b778aff4 b106d880 b0a4d743
0xb196529c:   0000000b 00000000 00000000 00000000
0xb19652ac:   00001000 00000000 00000000 00000000
0xb19652bc:   00000000 00000000 7fffffff fffffffe
0xb19652cc:   ffffffff ffffffff ffffffff ffffffff
0xb19652dc:   ffffffff ffffffff ffffffff ffffffff
0xb19652ec:   ffffffff ffffffff ffffffff ffffffff
0xb19652fc:   ffffffff ffffffff ffffffff ffffffff 

Instructions: (pc=0xb77a1416)
0xb77a13f6:   00 00 00 00 00 00 00 00 00 00 58 b8 77 00 00 00
0xb77a1406:   cd 80 90 8d 76 00 b8 ad 00 00 00 cd 80 90 cd 80
0xb77a1416:   c3 00 2e 73 68 73 74 72 74 61 62 00 2e 68 61 73
0xb77a1426:   68 00 2e 64 79 6e 73 79 6d 00 2e 64 79 6e 73 74 

Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x000015f8 is an unknown value
ECX=0x00001622 is an unknown value
EDX=0x0000000b is an unknown value
ESP=0xb196528c is an unknown value
EBP=0xb1965398 is an unknown value
ESI=0x00000020 is an unknown value
EDI=0xb778aff4: <offset 0x17ff4> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb7773000


Stack: [0xb1955000,0xb1966000],  sp=0xb196528c,  free space=64k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [+0x416]  __kernel_vsyscall+0x2
C  [libpthread.so.0+0x6d31]  short+0xd1


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 24640K, used 9143K [0x7f080000, 0x80b30000, 0x84480000)
  eden space 21952K,  41% used [0x7f080000, 0x7f96dd00, 0x805f0000)
  from space 2688K,   0% used [0x805f0000, 0x805f0000, 0x80890000)
  to   space 2688K,   0% used [0x80890000, 0x80890000, 0x80b30000)
 tenured generation   total 54532K, used 32717K [0x84480000, 0x879c1000, 0x8ec80000)
   the space 54532K,  59% used [0x84480000, 0x864736e8, 0x86473800, 0x879c1000)
 compacting perm gen  total 12288K, used 9258K [0x8ec80000, 0x8f880000, 0x92c80000)
   the space 12288K,  75% used [0x8ec80000, 0x8f58abd0, 0x8f58ac00, 0x8f880000)
    ro space 10240K,  61% used [0x92c80000, 0x932a9838, 0x932a9a00, 0x93680000)
    rw space 12288K,  60% used [0x93680000, 0x93dba040, 0x93dba200, 0x94280000)

Code Cache  [0xb4bbe000, 0xb4ece000, 0xb6bbe000)
 total_blobs=1825 nmethods=1451 adapters=308 free_code_cache=30347840 largest_free_block=192

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 536176     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/bin/java
09bf7000-0a78b000 rwxp 00000000 00:00 0          [heap]
7f080000-80b30000 rwxp 00000000 00:00 0 
80b30000-84480000 rwxp 00000000 00:00 0 
84480000-879c1000 rwxp 00000000 00:00 0 
879c1000-8ec80000 rwxp 00000000 00:00 0 
8ec80000-8f880000 rwxp 00000000 00:00 0 
8f880000-92c80000 rwxp 00000000 00:00 0 
92c80000-932aa000 r-xs 00001000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
932aa000-93680000 rwxp 00000000 00:00 0 
93680000-93dbb000 rwxp 0062b000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
93dbb000-94280000 rwxp 00000000 00:00 0 
94280000-94362000 rwxp 00d66000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94362000-94680000 rwxp 00000000 00:00 0 
94680000-94688000 r-xs 00e48000 08:01 536238     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/classes.jsa
94688000-94a80000 rwxp 00000000 00:00 0 
9b200000-9b2e0000 rwxp 00000000 00:00 0 
9b2e0000-9b300000 ---p 00000000 00:00 0 
9b300000-9b34f000 rwxp 00000000 00:00 0 
9b34f000-9b400000 ---p 00000000 00:00 0 
9b400000-9b500000 rwxp 00000000 00:00 0 
9b600000-9b700000 rwxp 00000000 00:00 0 
9b800000-9b900000 rwxp 00000000 00:00 0 
9ba00000-9bb00000 rwxp 00000000 00:00 0 
9bc00000-9bd00000 rwxs 09df1000 00:05 8271       /dev/ati/card0
9bd00000-9be00000 rwxs 09df0000 00:05 8271       /dev/ati/card0
9be00000-9bf00000 rwxs 09def000 00:05 8271       /dev/ati/card0
9bf00000-9c000000 rwxp 00000000 00:00 0 
9c0af000-9c0b2000 ---p 00000000 00:00 0 
9c0b2000-9c100000 rwxp 00000000 00:00 0 
9c100000-9c200000 rwxs 09de6000 00:05 8271       /dev/ati/card0
9c200000-9c300000 rwxs 09de5000 00:05 8271       /dev/ati/card0
9c300000-9c400000 rwxs 09de4000 00:05 8271       /dev/ati/card0
9c400000-9c500000 rwxp 00000000 00:00 0 
9c500000-9c600000 rwxs 09de3000 00:05 8271       /dev/ati/card0
9c600000-9c700000 rwxs 09de2000 00:05 8271       /dev/ati/card0
9c700000-9c800000 rwxs 09de1000 00:05 8271       /dev/ati/card0
9c800000-9c900000 rwxs 09de0000 00:05 8271       /dev/ati/card0
9c900000-9ca00000 rwxs 09ddf000 00:05 8271       /dev/ati/card0
9ca00000-9cb00000 rwxs 09df2000 00:05 8271       /dev/ati/card0
9cb00000-9cc00000 rwxs 09ddd000 00:05 8271       /dev/ati/card0
9cc00000-9cd00000 rwxs 09ddc000 00:05 8271       /dev/ati/card0
9cd00000-9ce00000 rwxs 09ddb000 00:05 8271       /dev/ati/card0
9cf00000-9d000000 rwxs 09dd9000 00:05 8271       /dev/ati/card0
9d000000-9d100000 rwxs 09dd8000 00:05 8271       /dev/ati/card0
9d100000-9d200000 rwxs 09dd7000 00:05 8271       /dev/ati/card0
9d200000-9d300000 rwxp 00000000 00:00 0 
9d339000-9d33c000 ---p 00000000 00:00 0 
9d33c000-9d38a000 rwxp 00000000 00:00 0 
9d38a000-9d38d000 ---p 00000000 00:00 0 
9d38d000-9d3db000 rwxp 00000000 00:00 0 
9d3db000-9d3de000 ---p 00000000 00:00 0 
9d3de000-9d42c000 rwxp 00000000 00:00 0 
9d42c000-9d42d000 ---p 00000000 00:00 0 
9d42d000-9d62d000 rwxp 00000000 00:00 0 
9d62d000-9d630000 ---p 00000000 00:00 0 
9d630000-a76be000 rwxp 00000000 00:00 0 
a76be000-a76bf000 ---p 00000000 00:00 0 
a76bf000-a7ebf000 rwxp 00000000 00:00 0 
a7ebf000-a7ec0000 ---p 00000000 00:00 0 
a7ec0000-a86c0000 rwxp 00000000 00:00 0 
a86c0000-ac6c1000 rwxs 00000000 00:12 72983      /run/shm/pulse-shm-53287508
ac6c1000-ac827000 r-xp 00000000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac827000-ac838000 r-xp 00165000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac838000-ac839000 rwxp 00176000 08:01 2226094    /usr/lib/i386-linux-gnu/libvorbisenc.so.2.0.8
ac839000-ac885000 r-xp 00000000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac885000-ac886000 r-xp 0004b000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac886000-ac887000 rwxp 0004c000 08:01 2229060    /usr/lib/i386-linux-gnu/libFLAC.so.8.2.0
ac887000-ac8f2000 r-xp 00000000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac8f2000-ac8f3000 r-xp 0006b000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac8f3000-ac8f4000 rwxp 0006c000 08:01 2229361    /usr/lib/i386-linux-gnu/libsndfile.so.1.0.24
ac8f4000-ac8f8000 rwxp 00000000 00:00 0 
ac8f8000-ac9e4000 r-xp 00000000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ac9e4000-ac9e8000 r-xp 000eb000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ac9e8000-ac9e9000 rwxp 000ef000 08:01 2229141    /usr/lib/i386-linux-gnu/libasound.so.2.0.0
ac9e9000-aca0e000 r-xp 00000000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
aca0e000-aca0f000 rwxp 00025000 08:01 274488     /home/hutriv/.minecraft/bin/natives/libopenal.so
aca0f000-acafc000 rwxp 00000000 00:00 0 
acafc000-accfc000 rwxs c3e5f000 00:05 8271       /dev/ati/card0
accfc000-ae500000 rwxp 00000000 00:00 0 
ae500000-ae600000 rwxp 00000000 00:00 0 
ae600000-ae700000 rwxs 09dcf000 00:05 8271       /dev/ati/card0
ae700000-ae7ff000 rwxp 00000000 00:00 0 
ae7ff000-ae800000 ---p 00000000 00:00 0 
ae800000-ae8fa000 rwxp 00000000 00:00 0 
ae8fa000-ae900000 ---p 00000000 00:00 0 
ae900000-ae9fb000 rwxp 00000000 00:00 0 
ae9fb000-aea00000 ---p 00000000 00:00 0 
aea2a000-af12a000 rwxs 00006000 00:05 8271       /dev/ati/card0
af12a000-b0ee4000 r-xp 00000000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b0ee4000-b0faf000 rwxp 01db9000 08:01 406260     /usr/lib/fglrx/dri/fglrx_dri.so
b0faf000-b106f000 rwxp 00000000 00:00 0 
b106f000-b1200000 rwxs 00000000 00:04 24117260   /SYSV00000000 (deleted)
b1200000-b1300000 rwxp 00000000 00:00 0 
b132d000-b1390000 r-xp 00000000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
b1390000-b1391000 r-xp 00062000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
b1391000-b1392000 rwxp 00063000 08:01 2226018    /usr/lib/i386-linux-gnu/libpulsecommon-1.0.so
b1392000-b13de000 r-xp 00000000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b13de000-b13df000 r-xp 0004b000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b13df000-b13e0000 rwxp 0004c000 08:01 2226016    /usr/lib/i386-linux-gnu/libpulse.so.0.13.4
b13e0000-b1445000 rwxs 00000000 00:04 24084491   /SYSV00000000 (deleted)
b1445000-b1448000 ---p 00000000 00:00 0 
b1448000-b1496000 rwxp 00000000 00:00 0 
b1496000-b1499000 ---p 00000000 00:00 0 
b1499000-b14e7000 rwxp 00000000 00:00 0 
b14e7000-b1678000 rwxs 00000000 00:04 22740998   /SYSV00000000 (deleted)
b1678000-b18e4000 rwxp 00000000 00:00 0 
b18e4000-b1944000 rwxs 00000000 00:04 22609927   /SYSV00000000 (deleted)
b1955000-b1956000 ---p 00000000 00:00 0 
b1956000-b1966000 rwxp 00000000 00:00 0 
b1966000-b196e000 r-xp 00000000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b196e000-b196f000 r-xp 00007000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b196f000-b1970000 rwxp 00008000 08:01 1832438    /lib/i386-linux-gnu/libwrap.so.0.7.6
b1970000-b1987000 r-xs 003c2000 08:01 274284     /home/hutriv/.minecraft/bin/minecraft.jar
b1987000-b198a000 r-xs 0001f000 08:01 274283     /home/hutriv/.minecraft/bin/lwjgl_util.jar
b198a000-b198f000 r-xs 00033000 08:01 274282     /home/hutriv/.minecraft/bin/jinput.jar
b198f000-b1998000 r-xs 000ac000 08:01 274281     /home/hutriv/.minecraft/bin/lwjgl.jar
b1998000-b199b000 r-xs 000cc000 08:01 280947     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/localedata.jar
b199b000-b199e000 ---p 00000000 00:00 0 
b199e000-b19ec000 rwxp 00000000 00:00 0 
b19ec000-b19ef000 ---p 00000000 00:00 0 
b19ef000-b1a3d000 rwxp 00000000 00:00 0 
b1a3d000-b1a45000 r-xs 00115000 08:01 2245514    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/resources.jar
b1a45000-b1a4b000 r-xs 00095000 08:01 2245562    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jsse.jar
b1a4b000-b1a4e000 ---p 00000000 00:00 0 
b1a4e000-b1a9c000 rwxp 00000000 00:00 0 
b1a9c000-b1a9f000 ---p 00000000 00:00 0 
b1a9f000-b1aed000 rwxp 00000000 00:00 0 
b1aed000-b1af0000 ---p 00000000 00:00 0 
b1af0000-b1b3e000 rwxp 00000000 00:00 0 
b1b3e000-b1b3f000 ---p 00000000 00:00 0 
b1b3f000-b233f000 rwxp 00000000 00:00 0 
b233f000-b2340000 ---p 00000000 00:00 0 
b2340000-b2b40000 rwxp 00000000 00:00 0 
b2b40000-b2b58000 r-xp 00000000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b58000-b2b59000 r-xp 00017000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b59000-b2b5a000 rwxp 00018000 08:01 2226764    /usr/lib/libdbusmenu-glib.so.4.0.5
b2b5a000-b2b6a000 r-xp 00000000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b6a000-b2b6b000 ---p 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b6b000-b2b6c000 r-xp 00010000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b6c000-b2b6d000 rwxp 00011000 08:01 2226766    /usr/lib/libdbusmenu-gtk.so.4.0.5
b2b6d000-b2b70000 r-xs 00027000 08:01 280946     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/ext/sunjce_provider.jar
b2b70000-b2b75000 r-xp 00000000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b75000-b2b76000 r-xp 00004000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b76000-b2b77000 rwxp 00005000 08:01 1832429    /lib/i386-linux-gnu/libnss_dns-2.13.so
b2b77000-b2b79000 r-xp 00000000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b79000-b2b7a000 r-xp 00001000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b7a000-b2b7b000 rwxp 00002000 08:01 1831490    /lib/libnss_mdns4_minimal.so.2
b2b7b000-b2b7e000 r-xs 00013000 08:01 2245530    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/jce.jar
b2b7e000-b2b91000 r-xp 00000000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b91000-b2b92000 r-xp 00012000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b92000-b2b93000 rwxp 00013000 08:01 2228469    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b2b93000-b2ba3000 r-xp 00000000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2ba3000-b2ba4000 r-xp 0000f000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2ba4000-b2ba5000 rwxp 00010000 08:01 1831569    /lib/i386-linux-gnu/libudev.so.0.12.0
b2ba5000-b2bec000 r-xp 00000000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bec000-b2bed000 r-xp 00046000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bed000-b2bee000 rwxp 00047000 08:01 1832367    /lib/i386-linux-gnu/libdbus-1.so.3.5.7
b2bf0000-b2bf4000 r-xp 00000000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bf4000-b2bf5000 r-xp 00004000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bf5000-b2bf6000 rwxp 00005000 08:01 2228962    /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
b2bf6000-b2bfd000 r-xp 00000000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2bfd000-b2bfe000 r-xp 00006000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2bfe000-b2bff000 rwxp 00007000 08:01 2228468    /usr/lib/gio/modules/libdconfsettings.so
b2bff000-b2c14000 r-xp 00000000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2c14000-b2c15000 r-xp 00015000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2c15000-b2c16000 rwxp 00016000 08:01 2229025    /usr/lib/gvfs/libgvfscommon.so
b2c16000-b2c55000 r-xp 00000000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c55000-b2c56000 r-xp 0003f000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c56000-b2c57000 rwxp 00040000 08:01 2227036    /usr/lib/libibus-1.0.so.0.0.0
b2c57000-b2ca9000 r-xp 00000000 08:01 527586     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b2ca9000-b2d00000 r-xp 00000000 08:01 527633     /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
b2d00000-b2ded000 rwxp 00000000 00:00 0 
b2ded000-b2e00000 ---p 00000000 00:00 0 
b2e01000-b2e2b000 r-xp 00000000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2e2b000-b2e2c000 r-xp 00029000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2e2c000-b2e2d000 rwxp 0002a000 08:01 2228470    /usr/lib/gio/modules/libgvfsdbus.so
b2e2d000-b2e32000 r-xp 00000000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e32000-b2e33000 ---p 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e33000-b2e34000 r-xp 00005000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e34000-b2e35000 rwxp 00006000 08:01 2229743    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
b2e35000-b2e37000 r-xp 00000000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e37000-b2e38000 r-xp 00001000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e38000-b2e39000 rwxp 00002000 08:01 2229815    /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
b2e39000-b2e3a000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b2e3a000-b2e40000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b2e40000-b2e42000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b2e42000-b2e45000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b2e45000-b2e48000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b2e48000-b2e49000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b2e49000-b2e4d000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b2e4d000-b2e51000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b2e51000-b2e55000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b2e55000-b2e5c000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b2e5c000-b2e67000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b2e67000-b2e6a000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b2e6a000-b2e6c000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b2e6c000-b2e8e000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b2e8e000-b2e92000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b2e92000-b2e95000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b2e95000-b2ea2000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b2ea2000-b2ea8000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b2ea8000-b2eab000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b2eab000-b2eb3000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b2ebb000-b2ec1000 r-xp 00000000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2ec1000-b2ec2000 r-xp 00005000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2ec2000-b2ec3000 rwxp 00006000 08:01 2229266    /usr/lib/i386-linux-gnu/libjson.so.0.0.1
b2ec3000-b2ec6000 ---p 00000000 00:00 0 
b2ec6000-b2f14000 rwxp 00000000 00:00 0 
b2f14000-b2f17000 ---p 00000000 00:00 0 
b2f17000-b2f65000 rwxp 00000000 00:00 0 
b2f65000-b2fa5000 rwxs 00010000 00:05 8271       /dev/ati/card0
b2fa5000-b2fde000 r-xp 00000000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2fde000-b2fe0000 rwxp 00038000 08:01 406334     /usr/lib/fglrx/libatiadlxx.so
b2fe3000-b2fe8000 r-xp 00000000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fe8000-b2fe9000 r-xp 00004000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fe9000-b2fea000 rwxp 00005000 08:01 2226225    /usr/lib/i386-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
b2fea000-b2ff1000 r-xs 00000000 08:01 2225514    /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b2ff1000-b3001000 rwxs d0000000 00:05 8271       /dev/ati/card0
b3001000-b3008000 r-xp 00000000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b3008000-b3009000 rwxp 00006000 08:01 406258     /usr/lib/fglrx/libatiuki.so.1.0
b3009000-b3025000 r-xp 00000000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b3025000-b3026000 r-xp 0001b000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b3026000-b3027000 rwxp 0001c000 08:01 1832378    /lib/i386-linux-gnu/libgcc_s.so.1
b3027000-b30f0000 r-xp 00000000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b30f0000-b30fc000 rwxp 000c8000 08:01 406263     /usr/lib/fglrx/libGL.so.1.2
b30fc000-b3111000 rwxp 00000000 00:00 0 
b3111000-b3116000 r-xp 00000000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b3116000-b3117000 r-xp 00004000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b3117000-b3118000 rwxp 00005000 08:01 2229143    /usr/lib/i386-linux-gnu/libasyncns.so.0.3.1
b311b000-b311e000 r-xp 00000000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b311e000-b311f000 r-xp 00002000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b311f000-b3120000 rwxp 00003000 08:01 274297     /home/hutriv/.minecraft/bin/natives/libjinput-linux.so
b3120000-b3122000 rwxs 00002000 00:05 8271       /dev/ati/card0
b3122000-b3123000 r-xp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b3123000-b3124000 rwxp 00000000 08:01 280998     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjawt.so
b3124000-b317b000 r-xp 00000000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b317b000-b317c000 r-xp 00056000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b317c000-b317d000 rwxp 00057000 08:01 274299     /home/hutriv/.minecraft/bin/natives/liblwjgl.so
b317d000-b3184000 r-xp 00000000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b3184000-b3185000 rwxp 00006000 08:01 280983     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnio.so
b3185000-b3199000 r-xp 00000000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b3199000-b319a000 rwxp 00013000 08:01 280973     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libnet.so
b319a000-b31c7000 r-xp 00000000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b31c7000-b31c8000 r-xp 0002c000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b31c8000-b31c9000 rwxp 0002d000 08:01 2228959    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b31c9000-b31cf000 r-xp 00000000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31cf000-b31d0000 r-xp 00005000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31d0000-b31d1000 rwxp 00006000 08:01 2229309    /usr/lib/i386-linux-gnu/libogg.so.0.7.1
b31d1000-b31fa000 r-xp 00000000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31fa000-b31fb000 r-xp 00028000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31fb000-b31fc000 rwxp 00029000 08:01 2226096    /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
b31fc000-b3204000 r-xp 00000000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3204000-b3205000 r-xp 00008000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3205000-b3206000 rwxp 00009000 08:01 2227104    /usr/lib/libltdl.so.7.3.0
b3206000-b3217000 r-xp 00000000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3217000-b3218000 r-xp 00010000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3218000-b3219000 rwxp 00011000 08:01 2229378    /usr/lib/i386-linux-gnu/libtdb.so.1.2.9
b3219000-b3221000 r-xp 00000000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3221000-b3222000 r-xp 00007000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3222000-b3223000 rwxp 00008000 08:01 2226092    /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
b3223000-b3232000 r-xp 00000000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3232000-b3233000 r-xp 0000e000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3233000-b3234000 rwxp 0000f000 08:01 2224672    /usr/lib/libcanberra.so.0.2.5
b3234000-b3238000 r-xp 00000000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3238000-b3239000 r-xp 00003000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b3239000-b323a000 rwxp 00004000 08:01 2224678    /usr/lib/libcanberra-gtk.so.0.1.8
b323a000-b323b000 rwxs 00005000 00:05 8271       /dev/ati/card0
b323b000-b3240000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b3240000-b3249000 r-xp 00000000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b3249000-b324a000 r-xp 00008000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b324a000-b324b000 rwxp 00009000 08:01 2244786    /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/engines/libpixmap.so
b324b000-b3250000 r-xp 00000000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3250000-b3251000 r-xp 00004000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3251000-b3252000 rwxp 00005000 08:01 2224462    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b3252000-b328f000 r-xp 00000000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b328f000-b3290000 r-xp 0003c000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b3290000-b3291000 rwxp 0003d000 08:01 1832414    /lib/i386-linux-gnu/libpcre.so.3.12.1
b3291000-b3296000 r-xp 00000000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b3296000-b3297000 r-xp 00004000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b3297000-b3298000 rwxp 00005000 08:01 2229208    /usr/lib/i386-linux-gnu/libffi.so.6.0.0
b3298000-b329c000 r-xp 00000000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b329c000-b329d000 r-xp 00003000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b329d000-b329e000 rwxp 00004000 08:01 2229245    /usr/lib/i386-linux-gnu/libgthread-2.0.so.0.3000.0
b329e000-b32c4000 r-xp 00000000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b32c4000-b32c5000 ---p 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b32c5000-b32c7000 r-xp 00026000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b32c7000-b32c8000 rwxp 00028000 08:01 1832373    /lib/i386-linux-gnu/libexpat.so.1.5.2
b32c8000-b32db000 r-xp 00000000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32db000-b32dc000 r-xp 00012000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32dc000-b32dd000 rwxp 00013000 08:01 1835844    /lib/i386-linux-gnu/libresolv-2.13.so
b32dd000-b32df000 rwxp 00000000 00:00 0 
b32df000-b32fb000 r-xp 00000000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32fb000-b32fc000 r-xp 0001b000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32fc000-b32fd000 rwxp 0001c000 08:01 1832423    /lib/i386-linux-gnu/libselinux.so.1
b32fd000-b3310000 r-xp 00000000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3310000-b3311000 r-xp 00012000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3311000-b3312000 rwxp 00013000 08:01 1832440    /lib/i386-linux-gnu/libz.so.1.2.3.4
b3312000-b331a000 r-xp 00000000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b331a000-b331b000 r-xp 00007000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b331b000-b331c000 rwxp 00008000 08:01 2229399    /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b331c000-b331e000 r-xp 00000000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b331e000-b331f000 r-xp 00001000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b331f000-b3320000 rwxp 00002000 08:01 2229403    /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b3320000-b3348000 r-xp 00000000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b3348000-b3349000 r-xp 00027000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b3349000-b334a000 rwxp 00028000 08:01 1832441    /lib/i386-linux-gnu/libpng12.so.0.46.0
b334a000-b33c8000 r-xp 00000000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b33c8000-b33cc000 r-xp 0007d000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b33cc000-b33cd000 rwxp 00081000 08:01 2229329    /usr/lib/i386-linux-gnu/libpixman-1.so.0.22.2
b33cd000-b345f000 r-xp 00000000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b345f000-b3463000 r-xp 00091000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b3463000-b3464000 rwxp 00095000 08:01 2226013    /usr/lib/i386-linux-gnu/libfreetype.so.6.6.2
b3464000-b3466000 r-xp 00000000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b3466000-b3467000 r-xp 00001000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b3467000-b3468000 rwxp 00002000 08:01 2229115    /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b3468000-b346a000 r-xp 00000000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b346a000-b346b000 r-xp 00001000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b346b000-b346c000 rwxp 00002000 08:01 2229111    /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b346c000-b3563000 r-xp 00000000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b3563000-b3564000 r-xp 000f6000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b3564000-b3565000 rwxp 000f7000 08:01 1832382    /lib/i386-linux-gnu/libglib-2.0.so.0.3000.0
b3565000-b35b2000 r-xp 00000000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b35b2000-b35b3000 r-xp 0004d000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b35b3000-b35b4000 rwxp 0004e000 08:01 2229239    /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3000.0
b35b4000-b35e6000 r-xp 00000000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35e6000-b35e7000 ---p 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35e7000-b35e8000 r-xp 00032000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35e8000-b35e9000 rwxp 00033000 08:01 2229210    /usr/lib/i386-linux-gnu/libfontconfig.so.1.4.4
b35e9000-b3630000 r-xp 00000000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3630000-b3631000 r-xp 00047000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3631000-b3632000 rwxp 00048000 08:01 2229311    /usr/lib/i386-linux-gnu/libpango-1.0.so.0.2903.0
b3632000-b3774000 r-xp 00000000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b3774000-b3776000 r-xp 00142000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b3776000-b3777000 rwxp 00144000 08:01 2229227    /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3000.0
b3777000-b3778000 rwxp 00000000 00:00 0 
b3778000-b383f000 r-xp 00000000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b383f000-b3840000 r-xp 000c7000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b3840000-b3841000 rwxp 000c8000 08:01 2229171    /usr/lib/i386-linux-gnu/libcairo.so.2.11000.2
b3841000-b3843000 rwxp 00000000 00:00 0 
b3843000-b38ee000 r-xp 00000000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38ee000-b38f0000 r-xp 000ab000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38f0000-b38f1000 rwxp 000ad000 08:01 2229221    /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.6
b38f1000-b3d52000 r-xp 00000000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d52000-b3d56000 r-xp 00461000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d56000-b3d58000 rwxp 00465000 08:01 2229247    /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.6
b3d58000-b3d5a000 rwxp 00000000 00:00 0 
b3d5a000-b3d5b000 r-xs 00000000 08:01 802429     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b3d5b000-b3d61000 r-xs 00000000 08:01 802426     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b3d61000-b3d63000 r-xs 00000000 08:01 802427     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b3d63000-b3d66000 r-xs 00000000 08:01 802437     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b3d66000-b3d69000 r-xs 00000000 08:01 802414     /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-3
b3d69000-b3d6a000 r-xs 00000000 08:01 802438     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b3d6a000-b3d6e000 r-xs 00000000 08:01 802423     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b3d6e000-b3d6f000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b3d6f000-b3d70000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b3d70000-b3d71000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b3d71000-b3d75000 r-xs 00000000 08:01 802428     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b3d75000-b3d79000 r-xs 00000000 08:01 788068     /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b3d79000-b3d80000 r-xs 00000000 08:01 787610     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b3d80000-b3d8b000 r-xs 00000000 08:01 802412     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b3d8b000-b3d8e000 r-xs 00000000 08:01 802434     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b3d8e000-b3db0000 r-xs 00000000 08:01 788072     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b3db0000-b3db4000 r-xs 00000000 08:01 787124     /var/cache/fontconfig/28d55f7026ece34dafa1c96be10c583a-le32d4.cache-3
b3db4000-b3db7000 r-xs 00000000 08:01 787649     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-le32d4.cache-3
b3db7000-b3dc4000 r-xs 00000000 08:01 802433     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b3dc4000-b3dca000 r-xs 00000000 08:01 788067     /var/cache/fontconfig/153bb866d4d26e7cd19eee2129f8d8d2-le32d4.cache-3
b3dca000-b3dcb000 r-xs 00000000 08:01 802418     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b3dcb000-b3dd2000 r-xp 00000000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3dd2000-b3dd3000 r-xp 00006000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3dd3000-b3dd4000 rwxp 00007000 08:01 2229129    /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b3dd4000-b3dd6000 r-xp 00000000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3dd6000-b3dd7000 r-xp 00001000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3dd7000-b3dd8000 rwxp 00002000 08:01 2229127    /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b3dd8000-b3ddb000 r-xp 00000000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3ddb000-b3ddc000 r-xp 00002000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3ddc000-b3ddd000 rwxp 00003000 08:01 2229231    /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3000.0
b3ddd000-b3e08000 r-xp 00000000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3e08000-b3e09000 r-xp 0002a000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3e09000-b3e0a000 rwxp 0002b000 08:01 2229315    /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.2903.0
b3e0a000-b3e28000 r-xp 00000000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3e28000-b3e29000 r-xp 0001d000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3e29000-b3e2a000 rwxp 0001e000 08:01 2229223    /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2400.0
b3e2a000-b3e47000 r-xp 00000000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e47000-b3e49000 r-xp 0001c000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e49000-b3e4a000 rwxp 0001e000 08:01 2229145    /usr/lib/i386-linux-gnu/libatk-1.0.so.0.20209.1
b3e4a000-b3e55000 r-xp 00000000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e55000-b3e56000 r-xp 0000a000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e56000-b3e57000 rwxp 0000b000 08:01 2229313    /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.2903.0
b3e57000-b3e5a000 ---p 00000000 00:00 0 
b3e5a000-b3ea8000 rwxp 00000000 00:00 0 
b3ea8000-b3eac000 r-xp 00000000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3eac000-b3ead000 r-xp 00003000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3ead000-b3eae000 rwxp 00004000 08:01 2229121    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b3eae000-b3eb7000 r-xp 00000000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3eb7000-b3eb8000 r-xp 00008000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3eb8000-b3eb9000 rwxp 00009000 08:01 2229131    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3eb9000-b3ec2000 r-xp 00000000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3ec2000-b3ec3000 r-xp 00008000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3ec3000-b3ec4000 rwxp 00009000 08:01 2229113    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b3ec4000-b3ec5000 r-xs 00000000 08:01 802411     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b3ec5000-b3ed3000 r-xp 00000000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3ed3000-b3ed4000 r-xp 0000d000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3ed4000-b3ed5000 rwxp 0000e000 08:01 2227196    /usr/lib/liboverlay-scrollbar-0.2.so.0.0.11
b3ed5000-b3f4e000 r-xp 00000000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3f4e000-b3f58000 rwxp 00078000 08:01 280985     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libfontmanager.so
b3f58000-b3f5d000 rwxp 00000000 00:00 0 
b3f5d000-b3f62000 r-xp 00000000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f62000-b3f63000 r-xp 00004000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f63000-b3f64000 rwxp 00005000 08:01 2229117    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b3f64000-b3f66000 r-xp 00000000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f66000-b3f67000 r-xp 00001000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f67000-b3f68000 rwxp 00002000 08:01 2229109    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3f68000-b3f85000 r-xp 00000000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f85000-b3f86000 r-xp 0001c000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f86000-b3f87000 rwxp 0001d000 08:01 2229405    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b3f87000-b3f95000 r-xp 00000000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f95000-b3f96000 r-xp 0000d000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f96000-b3f97000 rwxp 0000e000 08:01 2229125    /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3f97000-b3f9c000 r-xp 00000000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3f9c000-b3f9d000 r-xp 00004000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3f9d000-b3f9e000 rwxp 00005000 08:01 2226669    /usr/lib/libXtst.so.6.1.0
b3f9e000-b40cf000 r-xp 00000000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40cf000-b40d0000 ---p 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40d0000-b40d1000 r-xp 00131000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40d1000-b40d3000 rwxp 00132000 08:01 2229107    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b40d3000-b40d4000 rwxp 00000000 00:00 0 
b40d4000-b40e5000 r-xp 00000000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40e5000-b40e6000 r-xp 00010000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40e6000-b40e7000 rwxp 00011000 08:01 2229119    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b40e7000-b412a000 r-xp 00000000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b412a000-b412c000 rwxp 00043000 08:01 536094     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/xawt/libmawt.so
b412c000-b412d000 rwxp 00000000 00:00 0 
b412d000-b41b2000 r-xp 00000000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b41b2000-b41b9000 rwxp 00085000 08:01 280996     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libawt.so
b41b9000-b41dd000 rwxp 00000000 00:00 0 
b41dd000-b41e0000 ---p 00000000 00:00 0 
b41e0000-b422e000 rwxp 00000000 00:00 0 
b422e000-b422f000 ---p 00000000 00:00 0 
b422f000-b42af000 rwxp 00000000 00:00 0 
b42af000-b42b2000 ---p 00000000 00:00 0 
b42b2000-b4300000 rwxp 00000000 00:00 0 
b4300000-b43ff000 rwxp 00000000 00:00 0 
b43ff000-b4400000 ---p 00000000 00:00 0 
b4400000-b4401000 r-xs 00000000 08:01 802421     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4401000-b4402000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4402000-b4405000 r-xs 00000000 08:01 787648     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-le32d4.cache-3
b4405000-b440d000 r-xs 00000000 08:01 786434     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b440d000-b4412000 r-xs 00000000 08:01 787118     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4412000-b4415000 ---p 00000000 00:00 0 
b4415000-b4493000 rwxp 00000000 00:00 0 
b4493000-b4496000 ---p 00000000 00:00 0 
b4496000-b44e4000 rwxp 00000000 00:00 0 
b44e4000-b4524000 r-xp 002bd000 08:01 2231284    /usr/lib/locale/locale-archive
b4524000-b4724000 r-xp 00000000 08:01 2231284    /usr/lib/locale/locale-archive
b4724000-b4727000 ---p 00000000 00:00 0 
b4727000-b4775000 rwxp 00000000 00:00 0 
b4775000-b4778000 ---p 00000000 00:00 0 
b4778000-b47fa000 rwxp 00000000 00:00 0 
b47fa000-b4996000 r-xs 030c2000 08:01 2245591    /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/rt.jar
b4996000-b4997000 ---p 00000000 00:00 0 
b4997000-b4a25000 rwxp 00000000 00:00 0 
b4a25000-b4a3f000 rwxp 00000000 00:00 0 
b4a3f000-b4a5a000 rwxp 00000000 00:00 0 
b4a5a000-b4a94000 rwxp 00000000 00:00 0 
b4a94000-b4aa2000 rwxp 00000000 00:00 0 
b4aa2000-b4abe000 rwxp 00000000 00:00 0 
b4abe000-b4ad9000 rwxp 00000000 00:00 0 
b4ad9000-b4b12000 rwxp 00000000 00:00 0 
b4b12000-b4b18000 rwxp 00000000 00:00 0 
b4b18000-b4b32000 rwxp 00000000 00:00 0 
b4b32000-b4b4b000 rwxp 00000000 00:00 0 
b4b4b000-b4bbe000 rwxp 00000000 00:00 0 
b4bbe000-b4ed6000 rwxp 00000000 00:00 0 
b4ed6000-b6bbe000 rwxp 00000000 00:00 0 
b6bbe000-b6bcd000 r-xp 00000000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6bcd000-b6bcf000 rwxp 0000e000 08:01 280972     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libzip.so
b6bcf000-b6bda000 r-xp 00000000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bda000-b6bdb000 r-xp 0000a000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bdb000-b6bdc000 rwxp 0000b000 08:01 1832484    /lib/i386-linux-gnu/libnss_files-2.13.so
b6bdc000-b6be6000 r-xp 00000000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6be6000-b6be7000 r-xp 00009000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6be7000-b6be8000 rwxp 0000a000 08:01 1832487    /lib/i386-linux-gnu/libnss_nis-2.13.so
b6be8000-b6bf0000 r-xp 00000000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bf0000-b6bf1000 r-xp 00007000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bf1000-b6bf2000 rwxp 00008000 08:01 1831583    /lib/i386-linux-gnu/libnss_compat-2.13.so
b6bf2000-b6c07000 r-xp 00000000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6c07000-b6c08000 r-xp 00015000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6c08000-b6c09000 rwxp 00016000 08:01 1831582    /lib/i386-linux-gnu/libnsl-2.13.so
b6c09000-b6c0b000 rwxp 00000000 00:00 0 
b6c0b000-b6c0d000 r-xs 00000000 08:01 787650     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-le32d4.cache-3
b6c0d000-b6c0e000 r-xs 00000000 08:01 786167     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b6c0e000-b6c14000 rwxp 00000000 00:00 0 
b6c14000-b6c1c000 rwxs 00000000 08:01 406382     /tmp/hsperfdata_hutriv/5624
b6c1c000-b6c3f000 r-xp 00000000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6c3f000-b6c41000 rwxp 00023000 08:01 280974     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libjava.so
b6c41000-b6c48000 r-xp 00000000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c48000-b6c49000 r-xp 00006000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c49000-b6c4a000 rwxp 00007000 08:01 1835845    /lib/i386-linux-gnu/librt-2.13.so
b6c4a000-b6c4d000 ---p 00000000 00:00 0 
b6c4d000-b6c9b000 rwxp 00000000 00:00 0 
b6c9b000-b6cc3000 r-xp 00000000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6cc3000-b6cc4000 r-xp 00028000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6cc4000-b6cc5000 rwxp 00029000 08:01 1831580    /lib/i386-linux-gnu/libm-2.13.so
b6cc5000-b71a6000 r-xp 00000000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b71a6000-b71c9000 rwxp 004e1000 08:01 536106     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client/libjvm.so
b71c9000-b75e6000 rwxp 00000000 00:00 0 
b75e6000-b775e000 r-xp 00000000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b775e000-b7760000 r-xp 00178000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b7760000-b7761000 rwxp 0017a000 08:01 1831576    /lib/i386-linux-gnu/libc-2.13.so
b7761000-b7764000 rwxp 00000000 00:00 0 
b7764000-b7767000 r-xp 00000000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b7767000-b7768000 r-xp 00002000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b7768000-b7769000 rwxp 00003000 08:01 1831579    /lib/i386-linux-gnu/libdl-2.13.so
b7769000-b7770000 r-xp 00000000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b7770000-b7772000 rwxp 00006000 08:01 280981     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/jli/libjli.so
b7772000-b7773000 rwxp 00000000 00:00 0 
b7773000-b778a000 r-xp 00000000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b778a000-b778b000 r-xp 00016000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b778b000-b778c000 rwxp 00017000 08:01 1835843    /lib/i386-linux-gnu/libpthread-2.13.so
b778c000-b778e000 rwxp 00000000 00:00 0 
b778e000-b7790000 r-xs 00016000 08:01 2231027    /home/hutriv/Minecraft.jar
b7790000-b7791000 r-xp 0043a000 08:01 2231284    /usr/lib/locale/locale-archive
b7791000-b7792000 rwxp 00000000 00:00 0 
b7792000-b7793000 r-xp 00000000 00:00 0 
b7793000-b779e000 r-xp 00000000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b779e000-b779f000 rwxp 0000b000 08:01 280986     /usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/libverify.so
b779f000-b77a1000 rwxp 00000000 00:00 0 
b77a1000-b77a2000 r-xp 00000000 00:00 0          [vdso]
b77a2000-b77c0000 r-xp 00000000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b77c0000-b77c1000 r-xp 0001d000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
b77c1000-b77c2000 rwxp 0001e000 08:01 1831573    /lib/i386-linux-gnu/ld-2.13.so
bfb28000-bfb49000 rwxp 00000000 00:00 0          [stack]

VM Arguments:
java_command: /home/hutriv/Minecraft.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=hutriv
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.31/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x469da0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x38bdd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x38f030], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x38ec10], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:wheezy/sid

uname:Linux 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
libc:glibc 2.13 NPTL 2.13 
rlimit: STACK 8192k, CORE 0k, NPROC 7897, NOFILE 4096, AS infinity
load average:0.90 0.67 0.39

/proc/meminfo:
MemTotal:        1024968 kB
MemFree:           70932 kB
Buffers:            2420 kB
Cached:           124968 kB
SwapCached:        31768 kB
Active:           395204 kB
Inactive:         379632 kB
Active(anon):     329380 kB
Inactive(anon):   324916 kB
Active(file):      65824 kB
Inactive(file):    54716 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        138184 kB
HighFree:           1808 kB
LowTotal:         886784 kB
LowFree:           69124 kB
SwapTotal:       1046524 kB
SwapFree:         900232 kB
Dirty:              3424 kB
Writeback:             0 kB
AnonPages:        622932 kB
Mapped:           134304 kB
Shmem:              6880 kB
Slab:              25472 kB
SReclaimable:      12152 kB
SUnreclaim:        13320 kB
KernelStack:        2960 kB
PageTables:         8344 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1559008 kB
Committed_AS:    2563848 kB
VmallocTotal:     122880 kB
VmallocUsed:       30116 kB
VmallocChunk:      87508 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:      155640 kB
DirectMap4M:      753664 kB


CPU:total 2 (1 cores per cpu, 2 threads per core) family 15 model 4 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ht

/proc/cpuinfo:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6387.41
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping	: 1
cpu MHz		: 3193.708
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips	: 6388.43
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:



Memory: 4k page, physical 1024968k(70932k free), swap 1046524k(900232k free)

vm_info: Java HotSpot(TM) Client VM (20.6-b01) for linux-x86 JRE (1.6.0_31-b04), built on Jan 20 2012 10:30:33 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sat Apr  7 12:57:37 2012
elapsed time: 30 seconds
```

---

### Post by uRock on 2012-04-07
Hello and welcome to the forums. 

Please use code tags by highlighting the text and clicking the # sign in the toolbar.

---

### Post by hutriv on 2012-04-07
Thanks, will do from now on. Sorry for not, I decided to finally post in the forums since this problem has wasted over 5 hours of precious time.

---

