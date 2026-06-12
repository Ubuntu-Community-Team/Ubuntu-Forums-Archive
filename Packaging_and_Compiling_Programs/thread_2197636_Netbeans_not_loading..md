---
title: "Netbeans not loading."
date: 2014-01-04
forum: Packaging and Compiling Programs
---

### Post by Rtedmonston on 2014-01-04
Hello, wondering if anyone could help me with an issue I'm having with Netbeans, I installed it today because my class requires it (IT programming), and the issue I have is, well, here's the log dump: 

```

(java:4512): Gtk-WARNING **: Unable to locate theme engine in module_path: "hcengine",
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb02df432, pid=3960, tid=2990299968
#
# JRE version: 6.0_27-b27
# Java VM: OpenJDK Client VM (20.0-b12 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.12.6
# Distribution: Ubuntu 13.10, package 6b27-1.12.6-1ubuntu2.1
# Problematic frame:
# C  [libgio-2.0.so.0+0x10d432]  _fini+0x13d3e
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x00000000

Registers:
EAX=0xb1386200, EBX=0xb7735000, ECX=0xb23c5b40, EDX=0xb02df430
ESP=0xb23c533c, EBP=0x00000003, ESI=0xb23c5be8, EDI=0xb773519c
EIP=0xb02df432, EFLAGS=0x00010286, CR2=0x00000000

Top of Stack: (sp=0xb23c533c)
0xb23c533c:   b7723b66 b1386200 00000000 00000000
0xb23c534c:   00000000 00000000 00000000 b7735180
0xb23c535c:   00000004 00000000 00000000 b7723ad9
0xb23c536c:   b7735000 00000000 00000000 b23c5468
0xb23c537c:   b7723d86 b23c53a4 00000000 00000000
0xb23c538c:   00000000 00000000 00000000 00000000
0xb23c539c:   00000000 00000000 b7735000 00000000
0xb23c53ac:   003d0f00 b23c5468 4f92930e d34f1904 

Instructions: (pc=0xb02df432)
0xb02df412:   52 00 47 5f 43 4f 4e 56 45 52 54 45 52 5f 43 4f
0xb02df422:   4e 56 45 52 54 45 44 00 63 6f 6e 76 65 72 74 65
0xb02df432:   64 00 47 5f 43 4f 4e 56 45 52 54 45 52 5f 46 49
0xb02df442:   4e 49 53 48 45 44 00 47 5f 43 4f 4e 56 45 52 54 

Register to memory mapping:

EAX=0xb1386200 is an unknown value
EBX=0xb7735000: <offset 0x18000> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb771d000
ECX=0xb23c5b40 is an unknown value
EDX=0xb02df430: <offset 0x10d430> in /usr/lib/i386-linux-gnu/libgio-2.0.so.0 at 0xb01d2000
ESP=0xb23c533c is an unknown value
EBP=0x00000003 is an unknown value
ESI=0xb23c5be8 is an unknown value
EDI=0xb773519c: <offset 0x1819c> in /lib/i386-linux-gnu/libpthread.so.0 at 0xb771d000


Stack: [0xb21c5000,0xb23c6000],  sp=0xb23c533c,  free space=2048k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libgio-2.0.so.0+0x10d432]  _fini+0x13d3e


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 9792K, used 3258K [0x4aa80000, 0x4b520000, 0x5aa80000)
  eden space 8704K,  29% used [0x4aa80000, 0x4ad062d8, 0x4b300000)
  from space 1088K,  61% used [0x4b300000, 0x4b3a8800, 0x4b410000)
  to   space 1088K,   0% used [0x4b410000, 0x4b410000, 0x4b520000)
 tenured generation   total 21888K, used 17521K [0x5aa80000, 0x5bfe0000, 0x7aa80000)
   the space 21888K,  80% used [0x5aa80000, 0x5bb9c7a8, 0x5bb9c800, 0x5bfe0000)
 compacting perm gen  total 32768K, used 11219K [0x7aa80000, 0x7ca80000, 0x92a80000)
   the space 32768K,  34% used [0x7aa80000, 0x7b574dc8, 0x7b574e00, 0x7ca80000)
    ro space 10240K,  74% used [0x92a80000, 0x931e8b28, 0x931e8c00, 0x93480000)
    rw space 12288K,  60% used [0x93480000, 0x93bcee48, 0x93bcf000, 0x94080000)

Code Cache  [0xb4700000, 0xb49b8000, 0xb6700000)
 total_blobs=1554 nmethods=1306 adapters=183 free_code_cache=30720064 largest_free_block=384

Dynamic libraries:
08048000-08051000 r-xp 00000000 08:01 42337344   /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08051000-08052000 r--p 00008000 08:01 42337344   /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 42337344   /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java
0936f000-09390000 rw-p 00000000 00:00 0          [heap]
4aa80000-4b520000 rw-p 00000000 00:00 0 
4b520000-5aa80000 rw-p 00000000 00:00 0 
5aa80000-5bfe0000 rw-p 00000000 00:00 0 
5bfe0000-7aa80000 rw-p 00000000 00:00 0 
7aa80000-7ca80000 rw-p 00000000 00:00 0 
7ca80000-92a80000 rw-p 00000000 00:00 0 
92a80000-931e9000 r--s 00001000 08:01 42730602   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
931e9000-93480000 rw-p 00000000 00:00 0 
93480000-93bcf000 rw-p 0076a000 08:01 42730602   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
93bcf000-94080000 rw-p 00000000 00:00 0 
94080000-9417d000 rw-p 00eb9000 08:01 42730602   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
9417d000-94480000 rw-p 00000000 00:00 0 
94480000-94488000 r-xs 00fb6000 08:01 42730602   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/classes.jsa
94488000-94880000 rw-p 00000000 00:00 0 
ac1f9000-ac1fc000 ---p 00000000 00:00 0 
ac1fc000-ac3fa000 rw-p 00000000 00:00 0          [stack:3992]
ac3fa000-ac3fd000 ---p 00000000 00:00 0 
ac3fd000-ac5fb000 rw-p 00000000 00:00 0          [stack:3991]
ac5fb000-ac5fe000 ---p 00000000 00:00 0 
ac5fe000-ac7fc000 rw-p 00000000 00:00 0          [stack:3990]
ac7fc000-ac7ff000 ---p 00000000 00:00 0 
ac7ff000-ac9fd000 rw-p 00000000 00:00 0          [stack:3989]
ac9fd000-aca00000 ---p 00000000 00:00 0 
aca00000-acbfe000 rw-p 00000000 00:00 0          [stack:3988]
acbfe000-acc01000 ---p 00000000 00:00 0 
acc01000-acdff000 rw-p 00000000 00:00 0          [stack:3986]
acdff000-ace02000 ---p 00000000 00:00 0 
ace02000-ad000000 rw-p 00000000 00:00 0          [stack:3985]
ad000000-ad027000 rw-p 00000000 00:00 0 
ad027000-ad100000 ---p 00000000 00:00 0 
ad1a5000-ad1d0000 r--s 00448000 08:01 45744369   /usr/share/netbeans/java5/modules/org-netbeans-modules-form.jar
ad1d0000-ad1d1000 ---p 00000000 00:00 0 
ad1d1000-ad9d1000 rw-p 00000000 00:00 0 
ad9d1000-ad9d2000 ---p 00000000 00:00 0 
ad9d2000-ae1d2000 rw-p 00000000 00:00 0          [stack:3982]
ae1d2000-ae1d3000 ---p 00000000 00:00 0 
ae1d3000-ae9d3000 rw-p 00000000 00:00 0          [stack:3981]
ae9d3000-ae9e4000 r-xp 00000000 08:01 32244579   /lib/i386-linux-gnu/libudev.so.1.3.5
ae9e4000-ae9e5000 r--p 00010000 08:01 32244579   /lib/i386-linux-gnu/libudev.so.1.3.5
ae9e5000-ae9e6000 rw-p 00011000 08:01 32244579   /lib/i386-linux-gnu/libudev.so.1.3.5
ae9e6000-aea18000 r-xp 00000000 08:01 41159082   /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
aea18000-aea1a000 r--p 00032000 08:01 41159082   /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
aea1a000-aea1b000 rw-p 00034000 08:01 41159082   /usr/lib/i386-linux-gnu/gvfs/libgvfscommon.so
aea1b000-aea4b000 r-xp 00000000 08:01 41157646   /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
aea4b000-aea4c000 r--p 0002f000 08:01 41157646   /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
aea4c000-aea4d000 rw-p 00030000 08:01 41157646   /usr/lib/i386-linux-gnu/gio/modules/libgvfsdbus.so
aea4d000-aeaa1000 r-xp 00000000 08:01 41157271   /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
aeaa1000-aeaa2000 r--p 00054000 08:01 41157271   /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
aeaa2000-aeaa3000 rw-p 00055000 08:01 41157271   /usr/lib/i386-linux-gnu/libibus-1.0.so.5.0.503
aeabd000-aeac3000 r-xp 00000000 08:01 41159640   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
aeac3000-aeac4000 r--p 00005000 08:01 41159640   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
aeac4000-aeac5000 rw-p 00006000 08:01 41159640   /usr/lib/i386-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so
aeac5000-aeb17000 r--p 00000000 08:01 42205239   /usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf
aeb17000-aeb6e000 r--p 00000000 08:01 42207062   /usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf
aeb6e000-aeb76000 r--s 00000000 08:01 39326941   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
aeb76000-aeb7c000 r--s 00000000 08:01 39323762   /var/cache/fontconfig/a6d8cf8e4ec09cdbc8633c31745a07dd-le32d4.cache-4
aeb7c000-aeb80000 r--s 00000000 08:01 39328474   /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
aeb94000-aeb99000 r--s 00000000 08:01 39328466   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
aeb99000-aeba2000 r--s 00000000 08:01 39322116   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
aeba2000-aebb1000 r--s 00000000 08:01 39328453   /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
aebb1000-aebe0000 r--s 00000000 08:01 39323178   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-4
aebe0000-aebe5000 r--s 00000000 08:01 39328101   /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-4
aebe5000-aebec000 r--s 00000000 08:01 39323694   /var/cache/fontconfig/52f7bdb7ce746bfd7eaa1985bd9cfa93-le32d4.cache-4
aebec000-aebfc000 r--s 00000000 08:01 39328063   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-4
aebfc000-aec03000 r--s 00000000 08:01 39323692   /var/cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-4
aeccc000-aed57000 rw-s 00000000 00:04 3014665    /SYSV00000000 (deleted)
aed57000-aeddd000 rw-p 00000000 00:00 0 
aeddd000-aedde000 ---p 00000000 00:00 0 
aedde000-af5de000 rw-p 00000000 00:00 0          [stack:3980]
af5de000-af5df000 ---p 00000000 00:00 0 
af5df000-afddf000 rw-p 00000000 00:00 0          [stack:3979]
afddf000-afe1e000 r--p 00000000 08:01 42205497   /usr/share/glib-2.0/schemas/gschemas.compiled
afe1e000-afe25000 r-xp 00000000 08:01 41161882   /usr/lib/i386-linux-gnu/libogg.so.0.8.1
afe25000-afe26000 r--p 00006000 08:01 41161882   /usr/lib/i386-linux-gnu/libogg.so.0.8.1
afe26000-afe27000 rw-p 00007000 08:01 41161882   /usr/lib/i386-linux-gnu/libogg.so.0.8.1
afe27000-afe50000 r-xp 00000000 08:01 41162573   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
afe50000-afe51000 ---p 00029000 08:01 41162573   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
afe51000-afe52000 r--p 00029000 08:01 41162573   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
afe52000-afe53000 rw-p 0002a000 08:01 41162573   /usr/lib/i386-linux-gnu/libvorbis.so.0.4.5
afe53000-afe5c000 r-xp 00000000 08:01 41162580   /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
afe5c000-afe5d000 r--p 00008000 08:01 41162580   /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
afe5d000-afe5e000 rw-p 00009000 08:01 41162580   /usr/lib/i386-linux-gnu/libltdl.so.7.3.0
afe5e000-afe70000 r-xp 00000000 08:01 41161987   /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
afe70000-afe71000 ---p 00012000 08:01 41161987   /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
afe71000-afe72000 r--p 00012000 08:01 41161987   /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
afe72000-afe73000 rw-p 00013000 08:01 41161987   /usr/lib/i386-linux-gnu/libtdb.so.1.2.11
afe73000-afe7b000 r-xp 00000000 08:01 41162577   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
afe7b000-afe7c000 r--p 00007000 08:01 41162577   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
afe7c000-afe7d000 rw-p 00008000 08:01 41162577   /usr/lib/i386-linux-gnu/libvorbisfile.so.3.3.4
afe7d000-afe86000 r--s 00000000 08:01 39322115   /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4
afe86000-afe8b000 r--p 00000000 08:01 37489460   /home/kelsey/.config/dconf/user
afe8b000-afe95000 r-xp 00000000 08:01 41159814   /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
afe95000-afe96000 r--p 00009000 08:01 41159814   /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
afe96000-afe97000 rw-p 0000a000 08:01 41159814   /usr/lib/i386-linux-gnu/gio/modules/libdconfsettings.so
afe97000-afea5000 r-xp 00000000 08:01 41160208   /usr/lib/i386-linux-gnu/libunity-gtk2-parser.so.0.0.0
afea5000-afea6000 r--p 0000d000 08:01 41160208   /usr/lib/i386-linux-gnu/libunity-gtk2-parser.so.0.0.0
afea6000-afea7000 rw-p 0000e000 08:01 41160208   /usr/lib/i386-linux-gnu/libunity-gtk2-parser.so.0.0.0
afea9000-afeb8000 r-xp 00000000 08:01 41161863   /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
afeb8000-afeb9000 r--p 0000e000 08:01 41161863   /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
afeb9000-afeba000 rw-p 0000f000 08:01 41161863   /usr/lib/i386-linux-gnu/libcanberra.so.0.2.5
afeba000-afebf000 r-xp 00000000 08:01 41163573   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
afebf000-afec0000 r--p 00004000 08:01 41163573   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
afec0000-afec1000 rw-p 00005000 08:01 41163573   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libcanberra-gtk-module.so
afec1000-afed9000 r-xp 00000000 08:01 41156806   /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
afed9000-afeda000 ---p 00018000 08:01 41156806   /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
afeda000-afedb000 r--p 00018000 08:01 41156806   /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
afedb000-afedc000 rw-p 00019000 08:01 41156806   /usr/lib/i386-linux-gnu/libgraphite2.so.3.0.1
afedc000-aff1b000 r-xp 00000000 08:01 32244644   /lib/i386-linux-gnu/libpcre.so.3.13.1
aff1b000-aff1c000 r--p 0003f000 08:01 32244644   /lib/i386-linux-gnu/libpcre.so.3.13.1
aff1c000-aff1d000 rw-p 00040000 08:01 32244644   /lib/i386-linux-gnu/libpcre.so.3.13.1
aff1d000-aff42000 r-xp 00000000 08:01 32243771   /lib/i386-linux-gnu/libexpat.so.1.6.0
aff42000-aff43000 ---p 00025000 08:01 32243771   /lib/i386-linux-gnu/libexpat.so.1.6.0
aff43000-aff45000 r--p 00025000 08:01 32243771   /lib/i386-linux-gnu/libexpat.so.1.6.0
aff45000-aff46000 rw-p 00027000 08:01 32243771   /lib/i386-linux-gnu/libexpat.so.1.6.0
aff46000-aff97000 r-xp 00000000 08:01 41157291   /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
aff97000-aff98000 r--p 00051000 08:01 41157291   /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
aff98000-aff99000 rw-p 00052000 08:01 41157291   /usr/lib/i386-linux-gnu/libharfbuzz.so.0.919.0
aff99000-affac000 r-xp 00000000 08:01 32245007   /lib/i386-linux-gnu/libresolv-2.17.so
affac000-affad000 r--p 00013000 08:01 32245007   /lib/i386-linux-gnu/libresolv-2.17.so
affad000-affae000 rw-p 00014000 08:01 32245007   /lib/i386-linux-gnu/libresolv-2.17.so
affae000-affb0000 rw-p 00000000 00:00 0 
affb0000-affd0000 r-xp 00000000 08:01 32244557   /lib/i386-linux-gnu/libselinux.so.1
affd0000-affd1000 r--p 0001f000 08:01 32244557   /lib/i386-linux-gnu/libselinux.so.1
affd1000-affd2000 rw-p 00020000 08:01 32244557   /lib/i386-linux-gnu/libselinux.so.1
affd2000-b0076000 r-xp 00000000 08:01 41158725   /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
b0076000-b007b000 r--p 000a4000 08:01 41158725   /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
b007b000-b007c000 rw-p 000a9000 08:01 41158725   /usr/lib/i386-linux-gnu/libpixman-1.so.0.30.2
b007c000-b017e000 r-xp 00000000 08:01 32243793   /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
b017e000-b017f000 r--p 00101000 08:01 32243793   /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
b017f000-b0180000 rw-p 00102000 08:01 32243793   /lib/i386-linux-gnu/libglib-2.0.so.0.3800.1
b0180000-b01d0000 r-xp 00000000 08:01 41156983   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
b01d0000-b01d1000 r--p 0004f000 08:01 41156983   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
b01d1000-b01d2000 rw-p 00050000 08:01 41156983   /usr/lib/i386-linux-gnu/libgobject-2.0.so.0.3800.1
b01d2000-b033e000 r-xp 00000000 08:01 41156990   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
b033e000-b033f000 ---p 0016c000 08:01 41156990   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
b033f000-b0341000 r--p 0016c000 08:01 41156990   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
b0341000-b0342000 rw-p 0016e000 08:01 41156990   /usr/lib/i386-linux-gnu/libgio-2.0.so.0.3800.1
b0342000-b0343000 rw-p 00000000 00:00 0 
b0343000-b0460000 r-xp 00000000 08:01 41159538   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
b0460000-b0462000 r--p 0011d000 08:01 41159538   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
b0462000-b0463000 rw-p 0011f000 08:01 41159538   /usr/lib/i386-linux-gnu/libcairo.so.2.11200.16
b0463000-b0464000 rw-p 00000000 00:00 0 
b0464000-b08cb000 r-xp 00000000 08:01 41164511   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
b08cb000-b08cf000 r--p 00466000 08:01 41164511   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
b08cf000-b08d1000 rw-p 0046a000 08:01 41164511   /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0.2400.20
b08d1000-b08d3000 rw-p 00000000 00:00 0 
b08d3000-b08d6000 ---p 00000000 00:00 0 
b08d6000-b0ad4000 rw-p 00000000 00:00 0          [stack:3978]
b0ad4000-b0b00000 r--s 00303000 08:01 41556370   /usr/share/java/svnkit-1.7.5.jar
b0b00000-b0bfb000 rw-p 00000000 00:00 0 
b0bfb000-b0c00000 ---p 00000000 00:00 0 
b0c00000-b0c04000 r-xp 00000000 08:01 41161859   /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
b0c04000-b0c05000 r--p 00003000 08:01 41161859   /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
b0c05000-b0c06000 rw-p 00004000 08:01 41161859   /usr/lib/i386-linux-gnu/libcanberra-gtk.so.0.1.9
b0c06000-b0c09000 r--s 0002a000 08:01 45744425   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-refactoring.jar
b0c09000-b0c26000 r--s 002c1000 08:01 45744421   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-project.jar
b0c26000-b0c36000 r--s 000c1000 08:01 41554881   /usr/share/java/freemarker-2.3.19.jar
b0c36000-b0c37000 r--s 00005000 08:01 45618814   /usr/share/netbeans/ide14/modules/org-netbeans-libs-freemarker.jar
b0c37000-b0c39000 r--s 00000000 08:01 45744424   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-ant.jar
b0c39000-b0c3a000 r--s 00000000 08:01 45618864   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-kit.jar
b0c3a000-b0c3c000 r--s 00004000 08:01 45618885   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-drivers.jar
b0c3c000-b0c40000 r--s 00055000 08:01 45618887   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-mysql.jar
b0c40000-b0c45000 r--s 00047000 08:01 45618863   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-sql-editor.jar
b0c45000-b0c49000 r--s 00035000 08:01 45618905   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-core.jar
b0c49000-b0c4e000 r--s 00060000 08:01 45618948   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-dataview.jar
b0c4e000-b0c64000 r--s 00108000 08:01 41556376   /usr/share/java/swingx1-1.0.jar
b0c64000-b0c65000 r--s 00001000 08:01 45618808   /usr/share/netbeans/ide14/modules/org-netbeans-libs-swingx.jar
b0c65000-b0c6a000 r--s 0006c000 08:01 45618836   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-sql-visualeditor.jar
b0c6a000-b0c76000 r--s 000f1000 08:01 45618104   /usr/share/netbeans/platform13/modules/org-netbeans-api-visual.jar
b0c76000-b0c86000 r--s 00159000 08:01 45744350   /usr/share/netbeans/java5/modules/org-netbeans-modules-debugger-jpda-ui.jar
b0c86000-b0c88000 r--s 00000000 08:01 39328508   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
b0c88000-b0c8e000 r-xp 00000000 08:01 41157968   /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
b0c8e000-b0c8f000 r--p 00006000 08:01 41157968   /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
b0c8f000-b0c90000 rw-p 00007000 08:01 41157968   /usr/lib/i386-linux-gnu/libdatrie.so.1.2.0
b0c90000-b0c95000 r--s 00074000 08:01 45744307   /usr/share/netbeans/java5/modules/org-netbeans-modules-debugger-jpda-projects.jar
b0c95000-b0c98000 r--s 00000000 08:01 39328449   /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
b0c98000-b0c9c000 r--s 00046000 08:01 45744368   /usr/share/netbeans/java5/modules/org-netbeans-modules-form-j2ee.jar
b0c9c000-b0c9d000 r--s 00000000 08:01 45744317   /usr/share/netbeans/java5/modules/org-netbeans-modules-form-kit.jar
b0c9d000-b0ca7000 r--s 00149000 08:01 45618829   /usr/share/netbeans/ide14/modules/org-netbeans-modules-html-editor.jar
b0ca7000-b0ca9000 r--s 00008000 08:01 45744347   /usr/share/netbeans/java5/modules/org-netbeans-modules-hudson-ant.jar
b0ca9000-b0caa000 r--s 00005000 08:01 45618822   /usr/share/netbeans/ide14/modules/org-netbeans-modules-hudson-mercurial.jar
b0caa000-b0cab000 r--s 00006000 08:01 45618902   /usr/share/netbeans/ide14/modules/org-netbeans-modules-hudson-subversion.jar
b0cab000-b0cb2000 r--s 00063000 08:01 45618904   /usr/share/netbeans/ide14/modules/org-netbeans-modules-hudson.jar
b0cb2000-b0cb4000 r--s 00018000 08:01 45744361   /usr/share/netbeans/java5/modules/org-netbeans-modules-i18n-form.jar
b0cb4000-b0cb5000 r--s 00000000 08:01 45750203   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-ide-branding-kit.jar
b0cb5000-b0cb6000 r--s 00001000 08:01 45750206   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-ide-branding.jar
b0cb6000-b0cb8000 r--s 00014000 08:01 45750205   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-autoupdate-pluginimporter.jar
b0cb8000-b0cc9000 r--s 001f8000 08:01 45744351   /usr/share/netbeans/java5/modules/org-netbeans-modules-j2ee-persistence.jar
b0cc9000-b0ccb000 r--s 0000f000 08:01 45744345   /usr/share/netbeans/java5/modules/org-netbeans-modules-j2ee-core-utilities.jar
b0ccb000-b0ccc000 r--s 00006000 08:01 45618839   /usr/share/netbeans/ide14/modules/org-netbeans-modules-dbapi.jar
b0ccc000-b0cd4000 r--s 0007b000 08:01 45744359   /usr/share/netbeans/java5/modules/org-netbeans-modules-dbschema.jar
b0cd4000-b0cd7000 r--s 0003f000 08:01 45618918   /usr/share/netbeans/ide14/modules/ext/ddl.jar
b0cd7000-b0ce8000 r--s 00152000 08:01 45618941   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db.jar
b0ce8000-b0cec000 r--s 0002a000 08:01 45618953   /usr/share/netbeans/ide14/modules/org-netbeans-modules-db-metadata-model.jar
b0cec000-b0ced000 r--s 00001000 08:01 45744332   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-kit.jar
b0ced000-b0d01000 r--s 000a3000 08:01 45744340   /usr/share/netbeans/java5/modules/docs/org-netbeans-modules-java-helpset.jar
b0d02000-b0d03000 r--s 00000000 08:01 45744308   /usr/share/netbeans/java5/modules/org-netbeans-modules-ant-kit.jar
b0d03000-b0d05000 r--s 00000000 08:01 45618872   /usr/share/netbeans/ide14/modules/org-netbeans-modules-ide-kit.jar
b0d05000-b0d07000 r--s 00043000 08:01 45618838   /usr/share/netbeans/ide14/modules/org-netbeans-modules-defaults.jar
b0d07000-b0d09000 r--s 0001d000 08:01 45618883   /usr/share/netbeans/ide14/modules/org-netbeans-modules-extbrowser.jar
b0d09000-b0d0b000 r--s 00021000 08:01 45618923   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-macros.jar
b0d0b000-b0d0d000 r--s 00008000 08:01 45618915   /usr/share/netbeans/ide14/modules/org-netbeans-core-ide.jar
b0d0d000-b0d0e000 r--s 00000000 08:01 45618114   /usr/share/netbeans/platform13/modules/org-netbeans-modules-core-kit.jar
b0d0e000-b0d0f000 r--s 00000000 08:01 45750209   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-core-windows_nb.jar
b0d0f000-b0d1b000 r--s 00160000 08:01 45618100   /usr/share/netbeans/platform13/modules/org-netbeans-core-windows.jar
b0d1b000-b0d22000 r--s 0006e000 08:01 41554875   /usr/share/java/org.apache.felix.framework.jar
b0d22000-b0d23000 r--s 00000000 08:01 45618075   /usr/share/netbeans/platform13/modules/org-netbeans-libs-felix.jar
b0d23000-b0d27000 r--s 00016000 08:01 41556242   /usr/share/java/osgi.core-4.3.0.jar
b0d27000-b0d2e000 r--s 00031000 08:01 41556247   /usr/share/java/osgi.compendium.jar
b0d2e000-b0d2f000 r--s 00000000 08:01 45618088   /usr/share/netbeans/platform13/modules/org-netbeans-libs-osgi.jar
b0d30000-b0d32000 r--s 0000d000 08:01 45618933   /usr/share/netbeans/ide14/modules/org-netbeans-modules-dlight-terminal.jar
b0d32000-b0d3a000 r-xp 00000000 08:01 41157972   /usr/lib/i386-linux-gnu/libthai.so.0.2.0
b0d3a000-b0d3b000 r--p 00007000 08:01 41157972   /usr/lib/i386-linux-gnu/libthai.so.0.2.0
b0d3b000-b0d3c000 rw-p 00008000 08:01 41157972   /usr/lib/i386-linux-gnu/libthai.so.0.2.0
b0d3c000-b0d3d000 r--s 00000000 08:01 45618936   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-kit.jar
b0d3d000-b0d42000 r--s 00062000 08:01 45618903   /usr/share/netbeans/ide14/modules/org-netbeans-modules-html.jar
b0d42000-b0d46000 r--s 00039000 08:01 45618812   /usr/share/netbeans/ide14/modules/org-netbeans-modules-html-editor-lib.jar
b0d46000-b0d48000 r--s 00016000 08:01 45618897   /usr/share/netbeans/ide14/modules/org-netbeans-modules-image.jar
b0d48000-b0d4a000 r--s 00016000 08:01 41554879   /usr/share/java/flute-1.1-SNAPSHOT.jar
b0d4a000-b0d4c000 r--s 00002000 08:01 41556354   /usr/share/java/sac-1.3.jar
b0d4c000-b0d56000 r--s 00087000 08:01 45618854   /usr/share/netbeans/ide14/modules/org-netbeans-modules-css-visual.jar
b0d56000-b0d59000 r--s 0003d000 08:01 45618106   /usr/share/netbeans/platform13/modules/org-netbeans-core-output2.jar
b0d59000-b0d60000 r--s 000b9000 08:01 45618959   /usr/share/netbeans/ide14/modules/org-netbeans-modules-css-editor.jar
b0d60000-b0d61000 r--s 00001000 08:01 45618858   /usr/share/netbeans/ide14/modules/org-netbeans-core-browser.jar
b0d61000-b0d62000 r--s 00003000 08:01 45618938   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-actions.jar
b0d62000-b0d64000 r--s 00013000 08:01 45618930   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-bookmarks.jar
b0d64000-b0d67000 r--s 00025000 08:01 45744341   /usr/share/netbeans/java5/modules/org-netbeans-modules-ant-debugger.jar
b0d68000-b0d6b000 r--s 00000000 08:01 39328215   /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4
b0d6b000-b0d91000 r-xp 00000000 08:01 32243773   /lib/i386-linux-gnu/libpng12.so.0.49.0
b0d91000-b0d92000 r--p 00025000 08:01 32243773   /lib/i386-linux-gnu/libpng12.so.0.49.0
b0d92000-b0d93000 rw-p 00026000 08:01 32243773   /lib/i386-linux-gnu/libpng12.so.0.49.0
b0d93000-b0dcb000 r-xp 00000000 08:01 41157225   /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
b0dcb000-b0dcc000 r--p 00038000 08:01 41157225   /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
b0dcc000-b0dcd000 rw-p 00039000 08:01 41157225   /usr/lib/i386-linux-gnu/libfontconfig.so.1.7.0
b0dcd000-b0e17000 r-xp 00000000 08:01 41157976   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
b0e17000-b0e18000 ---p 0004a000 08:01 41157976   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
b0e18000-b0e19000 r--p 0004a000 08:01 41157976   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
b0e19000-b0e1a000 rw-p 0004b000 08:01 41157976   /usr/lib/i386-linux-gnu/libpango-1.0.so.0.3200.5
b0e1a000-b0e2d000 r-xp 00000000 08:01 41157890   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
b0e2d000-b0e2e000 r--p 00013000 08:01 41157890   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
b0e2e000-b0e2f000 rw-p 00014000 08:01 41157890   /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0.3200.5
b0e2f000-b0e50000 r-xp 00000000 08:01 41164000   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
b0e50000-b0e51000 r--p 00020000 08:01 41164000   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
b0e51000-b0e52000 rw-p 00021000 08:01 41164000   /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0.2800.1
b0e52000-b0efd000 r-xp 00000000 08:01 41164509   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
b0efd000-b0eff000 r--p 000ab000 08:01 41164509   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
b0eff000-b0f00000 rw-p 000ad000 08:01 41164509   /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.20
b0f00000-b0fcf000 rw-p 00000000 00:00 0 
b0fcf000-b1000000 ---p 00000000 00:00 0 
b1000000-b1003000 r--s 00021000 08:01 45744312   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-debug.jar
b1003000-b1005000 r--s 00061000 08:01 45744329   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-examples.jar
b1005000-b100a000 r--s 0005e000 08:01 45744337   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-freeform.jar
b100a000-b100e000 r--s 00043000 08:01 45744367   /usr/share/netbeans/java5/modules/org-netbeans-modules-ant-freeform.jar
b100e000-b1015000 r--s 00083000 08:01 45744324   /usr/share/netbeans/java5/modules/org-netbeans-modules-beans.jar
b1015000-b101d000 r--s 00081000 08:01 45744320   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-navigation.jar
b101d000-b101f000 r--s 0000e000 08:01 45744306   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-source-ant.jar
b101f000-b1023000 r--s 00052000 08:01 45744338   /usr/share/netbeans/java5/modules/org-netbeans-modules-javadoc.jar
b1023000-b1035000 r--s 00248000 08:01 45744314   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-hints.jar
b1035000-b1039000 r--s 00000000 08:01 39328067   /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-4
b1039000-b1041000 r-xp 00000000 08:01 41159065   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b1041000-b1042000 r--p 00008000 08:01 41159065   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b1042000-b1043000 rw-p 00009000 08:01 41159065   /usr/lib/i386-linux-gnu/libxcb-render.so.0.0.0
b1043000-b1045000 r--s 00004000 08:01 45744335   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-hints-processor.jar
b1045000-b1048000 r--s 00032000 08:01 45744330   /usr/share/netbeans/java5/modules/org-netbeans-modules-javawebstart.jar
b1048000-b104d000 r--s 00097000 08:01 45744366   /usr/share/netbeans/java5/modules/org-netbeans-modules-junit.jar
b104d000-b104e000 r--s 00005000 08:01 45618827   /usr/share/netbeans/ide14/modules/org-netbeans-modules-gototest.jar
b104e000-b104f000 r--s 00000000 08:01 39328548   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
b104f000-b1052000 r--s 00000000 08:01 39323165   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-4
b1052000-b1053000 r--s 00001000 08:01 45750213   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-modules-autoupdate-ui_nb.jar
b1053000-b1054000 r--s 00000000 08:01 39328472   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
b1054000-b1059000 r-xp 00000000 08:01 41156652   /usr/lib/i386-linux-gnu/libffi.so.6.0.1
b1059000-b105a000 r--p 00005000 08:01 41156652   /usr/lib/i386-linux-gnu/libffi.so.6.0.1
b105a000-b105b000 rw-p 00006000 08:01 41156652   /usr/lib/i386-linux-gnu/libffi.so.6.0.1
b105b000-b105f000 r--s 00025000 08:01 45618834   /usr/share/netbeans/ide14/modules/org-netbeans-modules-extexecution.jar
b105f000-b1061000 r--s 00000000 08:01 45744344   /usr/share/netbeans/java5/modules/org-netbeans-modules-junitlib.jar
b1061000-b1068000 r--s 00036000 08:01 41554393   /usr/share/java/junit4-4.11.jar
b1068000-b106a000 r--s 0000a000 08:01 41554369   /usr/share/java/hamcrest-core-1.3.jar
b106a000-b106b000 r--s 00000000 08:01 45618086   /usr/share/netbeans/platform13/modules/org-netbeans-libs-junit4.jar
b106b000-b106d000 r--s 0000c000 08:01 45618085   /usr/share/netbeans/platform13/modules/org-netbeans-modules-keyring-impl.jar
b106d000-b106e000 r--s 00006000 08:01 45618913   /usr/share/netbeans/ide14/modules/org-netbeans-modules-languages-diff.jar
b106e000-b1070000 r--s 00005000 08:01 45618895   /usr/share/netbeans/ide14/modules/org-netbeans-modules-languages-manifest.jar
b1070000-b1072000 r--s 0001b000 08:01 45618843   /usr/share/netbeans/ide14/modules/org-netbeans-modules-languages-yaml.jar
b1072000-b1077000 r--s 00034000 08:01 41556235   /usr/share/java/jvyamlb-0.2.5.jar
b1077000-b1078000 r--s 00000000 08:01 45618899   /usr/share/netbeans/ide14/modules/org-netbeans-libs-jvyamlb.jar
b1078000-b1079000 r--s 00002000 08:01 41554415   /usr/share/java/bytelist-1.0.6.jar
b1079000-b107a000 r--s 00000000 08:01 45618894   /usr/share/netbeans/ide14/modules/org-netbeans-libs-bytelist.jar
b107a000-b107b000 r--s 00002000 08:01 45618950   /usr/share/netbeans/ide14/modules/org-netbeans-modules-lexer-nbbridge.jar
b107b000-b107e000 r--s 0002f000 08:01 45618824   /usr/share/netbeans/ide14/modules/org-netbeans-modules-localhistory.jar
b107e000-b1080000 r--s 0000d000 08:01 45618890   /usr/share/netbeans/ide14/modules/docs/org-netbeans-modules-mercurial.jar
b1080000-b108f000 r--s 00187000 08:01 45618801   /usr/share/netbeans/ide14/modules/org-netbeans-modules-mercurial.jar
b108f000-b1092000 r--s 00032000 08:01 45618118   /usr/share/netbeans/platform13/modules/org-netbeans-modules-print.jar
b1092000-b1094000 r--s 00001000 08:01 45618846   /usr/share/netbeans/ide14/modules/org-netbeans-modules-print-editor.jar
b1094000-b1096000 r--s 0001a000 08:01 45618108   /usr/share/netbeans/platform13/modules/org-netbeans-modules-progress-ui.jar
b1096000-b1097000 r--s 00004000 08:01 45744310   /usr/share/netbeans/java5/modules/org-netbeans-modules-projectimport-eclipse-j2se.jar
b1097000-b109a000 r--s 0004a000 08:01 45744334   /usr/share/netbeans/java5/modules/org-netbeans-modules-projectimport-eclipse-core.jar
b109a000-b109e000 r--s 00049000 08:01 45744327   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-j2seplatform.jar
b109e000-b109f000 r--s 00001000 08:01 45618823   /usr/share/netbeans/ide14/modules/org-netbeans-modules-projectui-buildmenu.jar
b109f000-b10ab000 r--s 00149000 08:01 45744309   /usr/share/netbeans/java5/modules/org-netbeans-modules-refactoring-java.jar
b10ab000-b10b2000 r--s 00105000 08:01 45618840   /usr/share/netbeans/ide14/modules/org-netbeans-modules-schema2beans.jar
b10b2000-b10b5000 r--s 00031000 08:01 45618092   /usr/share/netbeans/platform13/modules/org-netbeans-modules-settings.jar
b10b5000-b10b7000 r--s 00005000 08:01 45618803   /usr/share/netbeans/ide14/modules/org-netbeans-modules-spellchecker-bindings-htmlxml.jar
b10b7000-b10b9000 r--s 00008000 08:01 45618888   /usr/share/netbeans/ide14/modules/org-netbeans-modules-html-lexer.jar
b10b9000-b10ba000 r--s 00006000 08:01 45744318   /usr/share/netbeans/java5/modules/org-netbeans-modules-spellchecker-bindings-java.jar
b10ba000-b10bb000 r--s 0000e000 08:01 45744355   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-editor-lib.jar
b10bb000-b10bf000 r--s 00029000 08:01 45618910   /usr/share/netbeans/ide14/modules/org-netbeans-modules-spellchecker.jar
b10bf000-b10d5000 r--s 00244000 08:01 45618907   /usr/share/netbeans/ide14/modules/org-netbeans-modules-subversion.jar
b10d5000-b10d7000 r--s 00000000 08:01 39328363   /var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
b10dd000-b10df000 r-xp 00000000 08:01 41159536   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b10df000-b10e0000 r--p 00001000 08:01 41159536   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b10e0000-b10e1000 rw-p 00002000 08:01 41159536   /usr/lib/i386-linux-gnu/libxcb-shm.so.0.0.0
b10e1000-b10e3000 r-xp 00000000 08:01 41162025   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b10e3000-b10e4000 r--p 00001000 08:01 41162025   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b10e4000-b10e5000 rw-p 00002000 08:01 41162025   /usr/lib/i386-linux-gnu/libXdamage.so.1.1.0
b10e5000-b10e7000 r-xp 00000000 08:01 41162453   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b10e7000-b10e8000 r--p 00001000 08:01 41162453   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b10e8000-b10e9000 rw-p 00002000 08:01 41162453   /usr/lib/i386-linux-gnu/libXcomposite.so.1.0.0
b10e9000-b10f2000 r--s 00046000 08:01 41555263   /usr/share/java/jna-platform-3.2.7.jar
b10f2000-b10fa000 r--s 00041000 08:01 41556360   /usr/share/java/svn-javahl.jar
b10fa000-b1100000 r--s 0006e000 08:01 45744427   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-kit.jar
b1100000-b11fa000 rw-p 00000000 00:00 0 
b11fa000-b1200000 ---p 00000000 00:00 0 
b1200000-b1201000 r--s 00003000 08:01 45618881   /usr/share/netbeans/ide14/modules/org-netbeans-modules-spellchecker-bindings-properties.jar
b1201000-b1202000 r--s 00000000 08:01 39328467   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
b1202000-b1203000 r--s 00001000 08:01 45618799   /usr/share/netbeans/ide14/modules/org-netbeans-modules-spellchecker-kit.jar
b1203000-b1204000 r--s 00000000 08:01 39328450   /var/cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
b1204000-b1207000 r--s 00016000 08:01 45618893   /usr/share/netbeans/ide14/modules/docs/org-netbeans-modules-subversion.jar
b1207000-b120b000 r--s 00032000 08:01 41554892   /usr/share/java/ini4j-0.5.2-SNAPSHOT.jar
b120b000-b120c000 r--s 00000000 08:01 39328400   /var/cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
b120c000-b1210000 r--s 00024000 08:01 41556373   /usr/share/java/svnClientAdapter-1.8.16.jar
b1210000-b1211000 r--s 00001000 08:01 45618908   /usr/share/netbeans/ide14/modules/org-netbeans-libs-svnClientAdapter.jar
b1211000-b1215000 r--s 00020000 08:01 41554408   /usr/share/java/bsaf-1.9.jar
b1215000-b1219000 r--s 0008e000 08:01 45744333   /usr/share/netbeans/java5/modules/org-netbeans-modules-swingapp.jar
b1219000-b121f000 r--s 00075000 08:01 45618943   /usr/share/netbeans/ide14/modules/org-netbeans-modules-properties.jar
b121f000-b1220000 r--s 00000000 08:01 41556319   /usr/share/java/AbsoluteLayout-7.0.jar
b1220000-b1227000 r--s 00094000 08:01 41554403   /usr/share/java/beansbinding-1.2.1.jar
b1227000-b1228000 r--s 00000000 08:01 45744353   /usr/share/netbeans/java5/modules/org-jdesktop-beansbinding.jar
b1228000-b1229000 r--s 00005000 08:01 45744304   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-guards.jar
b1229000-b1231000 r--s 000cc000 08:01 45744342   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-j2seproject.jar
b1231000-b1233000 r--s 00000000 08:01 45744362   /usr/share/netbeans/java5/modules/org-netbeans-modules-ant-browsetask.jar
b1233000-b1234000 r--s 00001000 08:01 45744354   /usr/share/netbeans/java5/modules/org-netbeans-modules-debugger-jpda-ant.jar
b1234000-b1237000 r--s 00026000 08:01 45744319   /usr/share/netbeans/java5/modules/org-netbeans-api-debugger-jpda.jar
b1237000-b123e000 r--s 0004c000 08:01 45744313   /usr/share/netbeans/java5/modules/org-netbeans-modules-j2ee-persistenceapi.jar
b123e000-b1241000 r--s 00017000 08:01 45744303   /usr/share/netbeans/java5/modules/org-netbeans-modules-j2ee-metadata-model-support.jar
b1241000-b1242000 r--s 00002000 08:01 45744364   /usr/share/netbeans/java5/modules/org-netbeans-modules-j2ee-metadata.jar
b1242000-b1245000 r--s 00022000 08:01 41554301   /usr/share/java/antlr3-runtime.jar
b1245000-b1247000 r--s 00000000 08:01 45618931   /usr/share/netbeans/ide14/modules/org-netbeans-libs-antlr3-runtime.jar
b1247000-b124f000 r--s 0009f000 08:01 45744348   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-api-common.jar
b124f000-b1252000 r--s 00026000 08:01 45744322   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-sourceui.jar
b1252000-b1253000 r--s 0000b000 08:01 45618851   /usr/share/netbeans/ide14/modules/org-netbeans-modules-target-iterator.jar
b1253000-b1254000 r--s 00000000 08:01 45618817   /usr/share/netbeans/ide14/modules/org-netbeans-modules-tasklist-kit.jar
b1254000-b1256000 r--s 00006000 08:01 45618879   /usr/share/netbeans/ide14/modules/org-netbeans-modules-tasklist-projectint.jar
b1256000-b1258000 r--s 0000b000 08:01 45618951   /usr/share/netbeans/ide14/modules/org-netbeans-modules-tasklist-todo.jar
b1258000-b125d000 r--s 00052000 08:01 45618926   /usr/share/netbeans/ide14/modules/org-netbeans-modules-tasklist-ui.jar
b125d000-b1260000 r--s 00026000 08:01 45618874   /usr/share/netbeans/ide14/modules/org-netbeans-modules-terminal.jar
b1260000-b1266000 r--s 00050000 08:01 45618830   /usr/share/netbeans/ide14/modules/org-netbeans-lib-terminalemulator.jar
b1266000-b1267000 r--s 00000000 08:01 45750218   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-uihandler-exceptionreporter.jar
b1267000-b126a000 r--s 00039000 08:01 45750201   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-uihandler.jar
b126a000-b126c000 r--s 0000e000 08:01 45750204   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-lib-uihandler.jar
b126c000-b126d000 r--s 00004000 08:01 45750217   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-updatecenters.jar
b126d000-b1270000 r--s 00030000 08:01 45618111   /usr/share/netbeans/platform13/modules/ext/updater.jar
b1270000-b1275000 r--s 00087000 08:01 45618077   /usr/share/netbeans/platform13/modules/org-netbeans-modules-autoupdate-services.jar
b1275000-b127f000 r--s 00042000 08:01 45618891   /usr/share/netbeans/ide14/modules/docs/org-netbeans-modules-usersguide.jar
b127f000-b1280000 r--s 00003000 08:01 45618841   /usr/share/netbeans/ide14/modules/org-netbeans-modules-usersguide.jar
b1280000-b1281000 r--s 00003000 08:01 45618847   /usr/share/netbeans/ide14/modules/org-netbeans-modules-utilities-project.jar
b1281000-b1287000 r--s 0007c000 08:01 45618862   /usr/share/netbeans/ide14/modules/org-netbeans-modules-utilities.jar
b1287000-b1289000 r--s 0000d000 08:01 45618069   /usr/share/netbeans/platform13/modules/org-netbeans-modules-sendopts.jar
b1289000-b128a000 r--s 00001000 08:01 45618835   /usr/share/netbeans/ide14/modules/org-netbeans-modules-versioning-indexingbridge.jar
b128a000-b128f000 r--s 00018000 08:01 45618892   /usr/share/netbeans/ide14/modules/docs/org-netbeans-modules-versioning-system-cvss.jar
b128f000-b129f000 r--s 00156000 08:01 45618876   /usr/share/netbeans/ide14/modules/org-netbeans-modules-versioning-system-cvss.jar
b129f000-b12a2000 r--s 00034000 08:01 41554869   /usr/share/java/jsch-0.1.48.jar
b12a2000-b12a3000 r--s 00001000 08:01 45618844   /usr/share/netbeans/ide14/modules/org-netbeans-libs-jsch.jar
b12a3000-b12a4000 r--s 0000f000 08:01 41556237   /usr/share/java/jzlib-1.1.2.jar
b12a4000-b12ac000 r--s 00083000 08:01 45618912   /usr/share/netbeans/ide14/modules/org-netbeans-lib-cvsclient.jar
b12ac000-b12b6000 r--s 000bb000 08:01 45618852   /usr/share/netbeans/ide14/modules/org-netbeans-modules-versioning-util.jar
b12b6000-b12ba000 r--s 00059000 08:01 45618811   /usr/share/netbeans/ide14/modules/org-netbeans-modules-versioning.jar
b12ba000-b12bc000 r--s 00003000 08:01 45618932   /usr/share/netbeans/ide14/modules/org-netbeans-modules-spellchecker-apimodule.jar
b12bc000-b12be000 r--s 0000e000 08:01 45618861   /usr/share/netbeans/ide14/modules/org-netbeans-modules-web-common.jar
b12be000-b12c3000 r--s 0006d000 08:01 45750202   /usr/share/netbeans/7.0.1/nb/modules/org-netbeans-modules-welcome.jar
b12c3000-b12ce000 r--s 000d1000 08:01 45618816   /usr/share/netbeans/ide14/modules/org-netbeans-modules-projectui.jar
b12ce000-b12d1000 r--s 00029000 08:01 45618079   /usr/share/netbeans/platform13/modules/org-netbeans-modules-favorites.jar
b12d1000-b12d6000 r--s 00044000 08:01 45618928   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-multiview.jar
b12d6000-b12ea000 r--s 00255000 08:01 45744331   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-source.jar
b12ea000-b1300000 r--s 00183000 08:01 41556387   /usr/share/java/javac-impl-7.0.1.jar
b1300000-b1400000 rw-p 00000000 00:00 0 
b1400000-b1401000 r--s 00000000 08:01 45618869   /usr/share/netbeans/ide14/modules/org-netbeans-libs-jzlib.jar
b1401000-b1404000 r--s 00019000 08:01 45618078   /usr/share/netbeans/platform13/modules/org-netbeans-core-execution.jar
b1404000-b1407000 r--s 0001e000 08:01 45618070   /usr/share/netbeans/platform13/modules/org-netbeans-core-multiview.jar
b1407000-b1409000 r--s 00032000 08:01 45618868   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-schema-completion.jar
b1409000-b140c000 r--s 00035000 08:01 45744321   /usr/share/netbeans/java5/modules/org-netbeans-modules-xml-tools-java.jar
b140c000-b140e000 r--s 0000e000 08:01 45618878   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-indent-project.jar
b140e000-b1410000 r--s 0000a000 08:01 45744305   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-lexer.jar
b1410000-b1411000 r--s 00004000 08:01 45744336   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-preprocessorbridge.jar
b1411000-b1412000 r--s 00001000 08:01 45744365   /usr/share/netbeans/java5/modules/org-netbeans-libs-javacimpl.jar
b1412000-b1418000 r--s 0001b000 08:01 41556386   /usr/share/java/javac-api-7.0.1.jar
b1418000-b1419000 r--s 00002000 08:01 45744349   /usr/share/netbeans/java5/modules/org-netbeans-libs-javacapi.jar
b1419000-b1420000 r--s 00080000 08:01 45744325   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-project.jar
b1420000-b1426000 r--s 00085000 08:01 45618939   /usr/share/netbeans/ide14/modules/org-netbeans-modules-project-ant.jar
b1426000-b142b000 r--s 00038000 08:01 45618906   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-catalog.jar
b142b000-b142e000 r--s 00020000 08:01 45744326   /usr/share/netbeans/java5/modules/org-netbeans-modules-java-platform.jar
b142e000-b1432000 r--s 00038000 08:01 45618857   /usr/share/netbeans/ide14/modules/org-netbeans-modules-project-libraries.jar
b1432000-b1433000 r--s 00000000 08:01 39326609   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
b1438000-b143a000 r--s 0001c000 08:01 45744346   /usr/share/netbeans/java5/modules/org-netbeans-modules-classfile.jar
b143a000-b143b000 r--s 00000000 08:01 39328092   /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-4
b143b000-b143c000 r--s 00000000 08:01 39328068   /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-4
b143c000-b143e000 r--s 00019000 08:01 45618810   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-tools.jar
b143e000-b1445000 r--s 0005d000 08:01 45618917   /usr/share/netbeans/ide14/modules/ext/org-netbeans-tax.jar
b1445000-b144b000 r--s 00058000 08:01 45618919   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-tax.jar
b144b000-b1464000 r--s 00132000 08:01 41554244   /usr/share/java/xercesImpl-2.11.0.jar
b1464000-b146d000 r--s 00031000 08:01 41554236   /usr/share/java/xml-apis-1.4.01.jar
b146d000-b146e000 r--s 00000000 08:01 45618826   /usr/share/netbeans/ide14/modules/org-netbeans-libs-xerces.jar
b146e000-b1472000 r--s 00046000 08:01 45618884   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-xdm.jar
b1472000-b1475000 r--s 0002b000 08:01 45618929   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xsl.jar
b1475000-b1477000 r--s 00014000 08:01 41554342   /usr/share/java/servlet-api-2.5.jar
b1477000-b1478000 r--s 00000000 08:01 45618807   /usr/share/netbeans/ide14/modules/org-netbeans-modules-servletapi.jar
b1478000-b147e000 r--s 00066000 08:01 45618914   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml.jar
b147e000-b1481000 r--s 00031000 08:01 45618935   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-retriever.jar
b1481000-b1483000 r--s 00015000 08:01 41554232   /usr/share/java/xml-resolver-1.2.jar
b1483000-b1484000 r--s 00000000 08:01 45618873   /usr/share/netbeans/ide14/modules/org-apache-xml-resolver.jar
b1484000-b1489000 r--s 00061000 08:01 45618944   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-axi.jar
b1489000-b1491000 r--s 0007b000 08:01 45618934   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-schema-model.jar
b1491000-b1494000 r--s 0002a000 08:01 45618942   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-xam.jar
b1494000-b149c000 r--s 00097000 08:01 45618937   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-text.jar
b149c000-b149e000 r--s 00011000 08:01 45618911   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-bracesmatching.jar
b149e000-b14a0000 r--s 0001c000 08:01 45618867   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-structure.jar
b14a0000-b14a3000 r--s 0001d000 08:01 45618952   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-deprecated-pre65formatting.jar
b14a3000-b14a4000 r--s 00006000 08:01 45618805   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-lexer.jar
b14a4000-b14b1000 r--s 000e8000 08:01 45618856   /usr/share/netbeans/ide14/modules/org-netbeans-modules-csl-api.jar
b14b1000-b14b8000 r--s 00063000 08:01 45618821   /usr/share/netbeans/ide14/modules/org-netbeans-modules-refactoring-api.jar
b14b8000-b14ba000 r--s 0000f000 08:01 45618875   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-guards.jar
b14ba000-b14bf000 r--s 00045000 08:01 45618870   /usr/share/netbeans/ide14/modules/org-netbeans-modules-jumpto.jar
b14bf000-b14c0000 r--s 00001000 08:01 45618083   /usr/share/netbeans/platform13/modules/org-netbeans-core-nativeaccess.jar
b14c0000-b14c2000 r--s 00007000 08:01 45618125   /usr/share/netbeans/platform13/modules/org-netbeans-core-netigso.jar
b14c2000-b14c4000 r--s 00008000 08:01 45744311   /usr/share/netbeans/java5/modules/org-netbeans-modules-ant-grammar.jar
b14c4000-b14c6000 r--s 00026000 08:01 45744426   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-crudsample.jar
b14c6000-b14c8000 r--s 00000000 08:01 45618183   /usr/share/netbeans/harness/modules/org-netbeans-modules-apisupport-harness.jar
b14ca000-b14cb000 r--s 00000000 08:01 39328017   /var/cache/fontconfig/0c9eb80ebd1c36541ebe2852d3bb0c49-le32d4.cache-4
b14cb000-b14de000 r--s 000f8000 08:01 41556239   /usr/share/java/lucene-core-2.9.4.jar
b14de000-b14df000 r--s 00000000 08:01 45618855   /usr/share/netbeans/ide14/modules/org-netbeans-libs-lucene.jar
b14df000-b14e4000 r--s 00058000 08:01 45618113   /usr/share/netbeans/platform13/modules/org-netbeans-modules-masterfs.jar
b14e4000-b14e7000 r--s 0001e000 08:01 41555184   /usr/share/java/jna-3.2.7.jar
b14e7000-b14e8000 r--s 00024000 08:01 45744422   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-osgidemo.jar
b14e8000-b14e9000 r--s 00011000 08:01 45744423   /usr/share/netbeans/apisupport3/modules/org-netbeans-modules-apisupport-paintapp.jar
b14e9000-b14ec000 r--s 00017000 08:01 45618909   /usr/share/netbeans/ide14/modules/org-netbeans-api-java-classpath.jar
b14ec000-b14f0000 r--s 00053000 08:01 45618091   /usr/share/netbeans/platform13/modules/org-netbeans-core-ui.jar
b14f0000-b14f3000 r--s 0003f000 08:01 45618925   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-codetemplates.jar
b14f3000-b14f7000 r--s 00034000 08:01 41556363   /usr/share/java/trilead-ssh2-6401.jar
b14f7000-b1500000 r--s 000db000 08:01 45618850   /usr/share/netbeans/ide14/modules/org-netbeans-modules-diff.jar
b1500000-b15fa000 rw-p 00000000 00:00 0 
b15fa000-b1600000 ---p 00000000 00:00 0 
b1600000-b1601000 r--s 00000000 08:01 45750212   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-core-ui_nb.jar
b1601000-b1605000 r--s 0005a000 08:01 45618900   /usr/share/netbeans/ide14/modules/org-netbeans-modules-options-editor.jar
b1605000-b1608000 r--s 0003c000 08:01 45618068   /usr/share/netbeans/platform13/modules/org-netbeans-modules-options-keymap.jar
b1608000-b1611000 r--s 000a3000 08:01 45618849   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor.jar
b1611000-b1612000 r--s 0001c000 08:01 41556321   /usr/share/java/swing-layout-1.0.4.jar
b1612000-b1614000 r--s 00000000 08:01 45618080   /usr/share/netbeans/platform13/modules/org-jdesktop-layout.jar
b1614000-b1618000 r--s 00041000 08:01 45618958   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-settings-storage.jar
b1618000-b1621000 r--s 0008e000 08:01 41554312   /usr/share/java/jhall-2.0.05.ds1.jar
b1621000-b1624000 r--s 00025000 08:01 45618074   /usr/share/netbeans/platform13/modules/org-netbeans-modules-javahelp.jar
b1624000-b1625000 r--s 00000000 08:01 45750208   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-modules-options-api_nb.jar
b1625000-b1629000 r--s 0004f000 08:01 45618093   /usr/share/netbeans/platform13/modules/org-netbeans-modules-options-api.jar
b1629000-b162a000 r--s 00000000 08:01 45750210   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-core_nb.jar
b162a000-b1630000 r--s 00072000 08:01 45618107   /usr/share/netbeans/platform13/modules/org-netbeans-core.jar
b1630000-b1631000 r--s 00001000 08:01 45618097   /usr/share/netbeans/platform13/modules/org-netbeans-modules-keyring.jar
b1631000-b1633000 r--s 00011000 08:01 45618815   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-errorstripe.jar
b1633000-b1634000 r--s 00002000 08:01 45618845   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-errorstripe-api.jar
b1634000-b1637000 r--s 0001c000 08:01 45618853   /usr/share/netbeans/ide14/modules/org-netbeans-modules-xml-core.jar
b1637000-b1639000 r--s 00011000 08:01 45618819   /usr/share/netbeans/ide14/modules/org-netbeans-api-xml.jar
b1639000-b1647000 r--s 000b9000 08:01 45618818   /usr/share/netbeans/ide14/modules/org-netbeans-spi-debugger-ui.jar
b1647000-b164b000 r--s 00038000 08:01 45618860   /usr/share/netbeans/ide14/modules/org-netbeans-modules-projectuiapi.jar
b164b000-b164e000 r--s 00038000 08:01 45618813   /usr/share/netbeans/ide14/modules/org-netbeans-api-debugger.jar
b164e000-b1651000 r--s 00034000 08:01 45618954   /usr/share/netbeans/ide14/modules/org-netbeans-spi-editor-hints.jar
b1651000-b1661000 r--s 00178000 08:01 45618866   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-lib.jar
b1661000-b1663000 r--s 0000f000 08:01 45618949   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-indent.jar
b1663000-b1665000 r--s 0001b000 08:01 45618946   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-fold.jar
b1665000-b166d000 r--s 000a8000 08:01 45618871   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-lib2.jar
b166d000-b1671000 r--s 00061000 08:01 45618806   /usr/share/netbeans/ide14/modules/org-netbeans-modules-lexer.jar
b1671000-b1673000 r--s 00017000 08:01 45618859   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-util.jar
b1673000-b1675000 r--s 00010000 08:01 45618940   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-settings.jar
b1675000-b1677000 r--s 0000c000 08:01 45618825   /usr/share/netbeans/ide14/modules/org-netbeans-spi-navigator.jar
b1677000-b167c000 r--s 00053000 08:01 45618922   /usr/share/netbeans/ide14/modules/org-netbeans-spi-palette.jar
b167d000-b167f000 r--s 0001c000 08:01 45618116   /usr/share/netbeans/platform13/modules/org-netbeans-spi-quicksearch.jar
b167f000-b1680000 r--s 00002000 08:01 45618120   /usr/share/netbeans/platform13/modules/org-netbeans-api-annotations-common.jar
b1680000-b1681000 r--s 00007000 08:01 45618099   /usr/share/netbeans/platform13/modules/org-netbeans-core-io-ui.jar
b1681000-b1685000 r--s 00042000 08:01 45618945   /usr/share/netbeans/ide14/modules/org-netbeans-spi-viewmodel.jar
b1685000-b1687000 r--s 00023000 08:01 45618848   /usr/share/netbeans/ide14/modules/org-netbeans-swing-dirchooser.jar
b1687000-b168b000 r--s 00032000 08:01 45618898   /usr/share/netbeans/ide14/modules/org-netbeans-modules-projectapi.jar
b168b000-b168e000 r--s 0002c000 08:01 45618098   /usr/share/netbeans/platform13/modules/org-netbeans-swing-plaf.jar
b168e000-b168f000 r--s 00006000 08:01 45618089   /usr/share/netbeans/platform13/modules/org-openide-execution.jar
b168f000-b1690000 r--s 00008000 08:01 45618123   /usr/share/netbeans/platform13/modules/org-openide-io.jar
b1690000-b169a000 r--s 000f4000 08:01 45618101   /usr/share/netbeans/platform13/modules/org-openide-loaders.jar
b169a000-b169e000 r--s 00027000 08:01 45618115   /usr/share/netbeans/platform13/modules/org-openide-actions.jar
b169e000-b16ab000 r--s 00142000 08:01 45618076   /usr/share/netbeans/platform13/modules/org-openide-explorer.jar
b16ab000-b16b8000 r--s 000b0000 08:01 45618126   /usr/share/netbeans/platform13/modules/org-netbeans-swing-tabcontrol.jar
b16b8000-b16ba000 r--s 00000000 08:01 39326727   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-4
b16ba000-b16bb000 r--s 00000000 08:01 37491706   /home/kelsey/.cache/fontconfig/bc3ab073c8b8f89d832a4c726bf2d75b-le32d4.cache-4
b16bb000-b16c4000 r-xp 00000000 08:01 41161722   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b16c4000-b16c5000 r--p 00008000 08:01 41161722   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b16c5000-b16c6000 rw-p 00009000 08:01 41161722   /usr/lib/i386-linux-gnu/libXrandr.so.2.2.0
b16c6000-b16c8000 r-xp 00000000 08:01 41161683   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b16c8000-b16c9000 r--p 00001000 08:01 41161683   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b16c9000-b16ca000 rw-p 00002000 08:01 41161683   /usr/lib/i386-linux-gnu/libXinerama.so.1.0.0
b16ca000-b16e8000 r-xp 00000000 08:01 41159491   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
b16e8000-b16ea000 r--p 0001d000 08:01 41159491   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
b16ea000-b16eb000 rw-p 0001f000 08:01 41159491   /usr/lib/i386-linux-gnu/libatk-1.0.so.0.21009.1
b16eb000-b16f6000 r-xp 00000000 08:01 41157946   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
b16f6000-b16f7000 r--p 0000a000 08:01 41157946   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
b16f7000-b16f8000 rw-p 0000b000 08:01 41157946   /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0.3200.5
b16f8000-b16fb000 r-xp 00000000 08:01 41156964   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
b16fb000-b16fc000 r--p 00002000 08:01 41156964   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
b16fc000-b16fd000 rw-p 00003000 08:01 41156964   /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0.3800.1
b16fd000-b16fe000 r--s 00000000 00:14 112551     /run/user/1000/dconf/user
b16fe000-b1702000 r-xp 00000000 08:01 41156640   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libunity-gtk-module.so
b1702000-b1703000 r--p 00003000 08:01 41156640   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libunity-gtk-module.so
b1703000-b1704000 rw-p 00004000 08:01 41156640   /usr/lib/i386-linux-gnu/gtk-2.0/modules/libunity-gtk-module.so
b1704000-b1715000 r-xp 00000000 08:01 41157244   /usr/lib/i386-linux-gnu/gtk-2.0/modules/liboverlay-scrollbar.so
b1715000-b1716000 r--p 00010000 08:01 41157244   /usr/lib/i386-linux-gnu/gtk-2.0/modules/liboverlay-scrollbar.so
b1716000-b1717000 rw-p 00011000 08:01 41157244   /usr/lib/i386-linux-gnu/gtk-2.0/modules/liboverlay-scrollbar.so
b171e000-b1722000 r--s 00033000 08:01 45618877   /usr/share/netbeans/ide14/modules/org-netbeans-modules-gsf-testrunner.jar
b1722000-b172a000 r--s 000b6000 08:01 45618081   /usr/share/netbeans/platform13/modules/org-netbeans-modules-autoupdate-ui.jar
b172b000-b1732000 r-xp 00000000 08:01 42468698   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libmanagement.so
b1732000-b1733000 r--p 00006000 08:01 42468698   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libmanagement.so
b1733000-b1734000 rw-p 00007000 08:01 42468698   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libmanagement.so
b1735000-b1736000 r--s 00000000 08:01 45750211   /usr/share/netbeans/7.0.1/nb/modules/locale/org-netbeans-spi-quicksearch_nb.jar
b1736000-b173f000 r--s 000b7000 08:01 45618842   /usr/share/netbeans/ide14/modules/org-netbeans-modules-parsing-api.jar
b173f000-b1743000 r--s 00033000 08:01 45618901   /usr/share/netbeans/ide14/modules/org-netbeans-modules-editor-completion.jar
b1743000-b1746000 ---p 00000000 00:00 0 
b1746000-b1944000 rw-p 00000000 00:00 0          [stack:3987]
b1944000-b1947000 ---p 00000000 00:00 0 
b1947000-b1b45000 rw-p 00000000 00:00 0          [stack:3976]
b1b45000-b1b48000 ---p 00000000 00:00 0 
b1b48000-b1d46000 rw-p 00000000 00:00 0          [stack:3975]
b1d46000-b1d4a000 r-xp 00000000 08:01 41159174   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b1d4a000-b1d4b000 r--p 00003000 08:01 41159174   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b1d4b000-b1d4c000 rw-p 00004000 08:01 41159174   /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
b1d4c000-b1d55000 r-xp 00000000 08:01 41159789   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b1d55000-b1d56000 r--p 00008000 08:01 41159789   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b1d56000-b1d57000 rw-p 00009000 08:01 41159789   /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
b1d57000-b1d58000 r--s 00000000 08:01 39328548   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
b1d58000-b1d60000 r--s 00000000 08:01 39326941   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
b1d60000-b1d62000 r--s 00000000 08:01 39328508   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
b1d62000-b1d68000 r--s 00000000 08:01 39323762   /var/cache/fontconfig/a6d8cf8e4ec09cdbc8633c31745a07dd-le32d4.cache-4
b1d68000-b1d6c000 r--s 00000000 08:01 39328474   /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
b1d6c000-b1d6d000 r--s 00000000 08:01 39328472   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
b1d6d000-b1d6e000 r--s 00000000 08:01 39328467   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
b1d6e000-b1d73000 r--s 00000000 08:01 39328466   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
b1d73000-b1d7c000 r--s 00000000 08:01 39322116   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
b1d7c000-b1d8b000 r--s 00000000 08:01 39328453   /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
b1d8b000-b1d8c000 r--s 00000000 08:01 39328450   /var/cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
b1d8c000-b1d8f000 r--s 00000000 08:01 39328449   /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
b1d8f000-b1d91000 r--s 00000000 08:01 39328363   /var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
b1d91000-b1dc0000 r--s 00000000 08:01 39323178   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-4
b1dc0000-b1dc5000 r--s 00000000 08:01 39328101   /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-4
b1dc5000-b1dd5000 r--s 00000000 08:01 39328063   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-4
b1dd5000-b1dd6000 r--s 00002000 08:01 45618924   /usr/share/netbeans/ide14/modules/org-netbeans-libs-svnClientAdapter-javahl.jar
b1dd6000-b1dd7000 r--s 00001000 08:01 45618865   /usr/share/netbeans/ide14/modules/org-netbeans-libs-svnClientAdapter-svnkit.jar
b1dd7000-b1ddb000 r--s 0004a000 08:01 45618103   /usr/share/netbeans/platform13/modules/org-openide-text.jar
b1ddb000-b1ddd000 r--s 00009000 08:01 45618122   /usr/share/netbeans/platform13/modules/org-netbeans-modules-editor-mimelookup.jar
b1ddd000-b1de0000 r--s 0002b000 08:01 45618090   /usr/share/netbeans/platform13/modules/org-netbeans-swing-outline.jar
b1de0000-b1de3000 r--s 0001d000 08:01 45618072   /usr/share/netbeans/platform13/modules/org-openide-windows.jar
b1de3000-b1de8000 r--s 00061000 08:01 45618095   /usr/share/netbeans/platform13/modules/org-openide-nodes.jar
b1de8000-b1deb000 r--s 00025000 08:01 45618094   /usr/share/netbeans/platform13/modules/org-openide-dialogs.jar
b1deb000-b1ded000 r--s 0000c000 08:01 45618096   /usr/share/netbeans/platform13/modules/org-netbeans-api-progress.jar
b1ded000-b1df2000 r--s 0006c000 08:01 45618102   /usr/share/netbeans/platform13/modules/org-openide-awt.jar
b1df2000-b1dfc000 r-xp 00000000 08:01 42468695   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjpeg.so
b1dfc000-b1dfd000 r--p 00009000 08:01 42468695   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjpeg.so
b1dfd000-b1dfe000 rw-p 0000a000 08:01 42468695   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjpeg.so
b1dfe000-b1dff000 r--s 00000000 08:01 39328548   /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-4
b1dff000-b1e07000 r--s 00000000 08:01 39326941   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-4
b1e07000-b1e09000 r--s 00000000 08:01 39328508   /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-4
b1e09000-b1e0f000 r--s 00000000 08:01 39323762   /var/cache/fontconfig/a6d8cf8e4ec09cdbc8633c31745a07dd-le32d4.cache-4
b1e0f000-b1e13000 r--s 00000000 08:01 39328474   /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le32d4.cache-4
b1e13000-b1e14000 r--s 00000000 08:01 39328472   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-4
b1e14000-b1e15000 r--s 00000000 08:01 39328467   /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-4
b1e15000-b1e1a000 r--s 00000000 08:01 39328466   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-4
b1e1a000-b1e23000 r--s 00000000 08:01 39322116   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-4
b1e23000-b1e32000 r--s 00000000 08:01 39328453   /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le32d4.cache-4
b1e32000-b1e33000 r--s 00000000 08:01 39328450   /var/cache/fontconfig/1ac9eb803944fde146138c791f5cc56a-le32d4.cache-4
b1e33000-b1e36000 r--s 00000000 08:01 39328449   /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le32d4.cache-4
b1e36000-b1e38000 r--s 00000000 08:01 39328363   /var/cache/fontconfig/767a8244fc0220cfb567a839d0392e0b-le32d4.cache-4
b1e38000-b1e3b000 r--s 00000000 08:01 39328215   /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4
b1e3b000-b1e6a000 r--s 00000000 08:01 39323178   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-4
b1e6a000-b1e7a000 r--s 00000000 08:01 39328063   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-4
b1e7a000-b1e7b000 r--s 00000000 08:01 39328400   /var/cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
b1e7b000-b1e7e000 r--s 00000000 08:01 39328215   /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le32d4.cache-4
b1e7e000-b1e82000 r--s 00000000 08:01 39328067   /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-4
b1e82000-b1e89000 r--s 00000000 08:01 39323694   /var/cache/fontconfig/52f7bdb7ce746bfd7eaa1985bd9cfa93-le32d4.cache-4
b1e89000-b1e8b000 r--s 00008000 08:01 45618084   /usr/share/netbeans/platform13/modules/org-netbeans-modules-queries.jar
b1e8b000-b1ebf000 r-xp 00000000 08:01 42468702   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/liblcms.so
b1ebf000-b1ec0000 r--p 00033000 08:01 42468702   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/liblcms.so
b1ec0000-b1ec1000 rw-p 00034000 08:01 42468702   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/liblcms.so
b1ec1000-b1ec3000 rw-p 00000000 00:00 0 
b1ec3000-b1ec4000 r--s 00000000 08:01 39326609   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
b1ec4000-b1ec5000 r--s 00000000 08:01 39328092   /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-4
b1ec5000-b1ec6000 r--s 00000000 08:01 39328068   /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-4
b1ec6000-b1ecd000 r--s 00000000 08:01 39323692   /var/cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-4
b1ecd000-b1ed6000 r--s 00000000 08:01 39322115   /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4
b1ed6000-b1ed7000 r--s 00000000 08:01 39328017   /var/cache/fontconfig/0c9eb80ebd1c36541ebe2852d3bb0c49-le32d4.cache-4
b1ed7000-b1ed9000 r--s 00000000 08:01 39326727   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-4
b1ed9000-b1edc000 r--s 00000000 08:01 39323165   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-4
b1edc000-b1edd000 r--s 00000000 08:01 37491706   /home/kelsey/.cache/fontconfig/bc3ab073c8b8f89d832a4c726bf2d75b-le32d4.cache-4
b1edd000-b1ee0000 ---p 00000000 00:00 0 
b1ee0000-b20de000 rw-p 00000000 00:00 0          [stack:3974]
b20de000-b2178000 r-xp 00000000 08:01 41157335   /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
b2178000-b217c000 r--p 00099000 08:01 41157335   /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
b217c000-b217d000 rw-p 0009d000 08:01 41157335   /usr/lib/i386-linux-gnu/libfreetype.so.6.10.1
b217d000-b21c3000 r-xp 00000000 08:01 42468697   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libfontmanager.so
b21c3000-b21c4000 r--p 00046000 08:01 42468697   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libfontmanager.so
b21c4000-b21c5000 rw-p 00047000 08:01 42468697   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libfontmanager.so
b21c5000-b21c8000 ---p 00000000 00:00 0 
b21c8000-b23c6000 rw-p 00000000 00:00 0          [stack:3973]
b23c6000-b23c9000 ---p 00000000 00:00 0 
b23c9000-b25c7000 rw-p 00000000 00:00 0          [stack:3972]
b25c7000-b26f7000 r-xp 00000000 08:01 41159070   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b26f7000-b26f8000 ---p 00130000 08:01 41159070   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b26f8000-b26f9000 r--p 00130000 08:01 41159070   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b26f9000-b26fb000 rw-p 00131000 08:01 41159070   /usr/lib/i386-linux-gnu/libX11.so.6.3.0
b26fb000-b26fc000 rw-p 00000000 00:00 0 
b26fc000-b26ff000 ---p 00000000 00:00 0 
b26ff000-b28fd000 rw-p 00000000 00:00 0          [stack:3971]
b28fd000-b2900000 ---p 00000000 00:00 0 
b2900000-b2afe000 rw-p 00000000 00:00 0          [stack:3970]
b2afe000-b2b01000 ---p 00000000 00:00 0 
b2b01000-b2cff000 rw-p 00000000 00:00 0          [stack:3969]
b2cff000-b2d02000 ---p 00000000 00:00 0 
b2d02000-b2f00000 rw-p 00000000 00:00 0          [stack:3967]
b2f00000-b3000000 rw-p 00000000 00:00 0 
b3000000-b3021000 rw-p 00000000 00:00 0 
b3021000-b3100000 ---p 00000000 00:00 0 
b3100000-b3121000 rw-p 00000000 00:00 0 
b3121000-b3200000 ---p 00000000 00:00 0 
b3200000-b3201000 r--s 00000000 08:01 39328400   /var/cache/fontconfig/dc05db6664285cc2f12bf69c139ae4c3-le32d4.cache-4
b3201000-b3202000 r--s 00000000 08:01 39326609   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-4
b3202000-b3207000 r--s 00000000 08:01 39328101   /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le32d4.cache-4
b3207000-b320c000 r-xp 00000000 08:01 41161754   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b320c000-b320d000 r--p 00004000 08:01 41161754   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b320d000-b320e000 rw-p 00005000 08:01 41161754   /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
b320e000-b322d000 r-xp 00000000 08:01 41160147   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b322d000-b322e000 r--p 0001f000 08:01 41160147   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b322e000-b322f000 rw-p 00020000 08:01 41160147   /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
b322f000-b323e000 r-xp 00000000 08:01 41160299   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b323e000-b323f000 r--p 0000e000 08:01 41160299   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b323f000-b3240000 rw-p 0000f000 08:01 41160299   /usr/lib/i386-linux-gnu/libXi.so.6.1.0
b3240000-b32d3000 r-xp 00000000 08:01 42468674   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libawt.so
b32d3000-b32d4000 r--p 00092000 08:01 42468674   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libawt.so
b32d4000-b32db000 rw-p 00093000 08:01 42468674   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libawt.so
b32db000-b32ff000 rw-p 00000000 00:00 0 
b32ff000-b3302000 ---p 00000000 00:00 0 
b3302000-b3500000 rw-p 00000000 00:00 0          [stack:3965]
b3500000-b3700000 r--p 00000000 08:01 41164293   /usr/lib/locale/locale-archive
b3700000-b3731000 rw-p 00000000 00:00 0 
b3731000-b3800000 ---p 00000000 00:00 0 
b3800000-b3801000 r--s 00000000 08:01 39328092   /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le32d4.cache-4
b3801000-b3802000 r--s 00000000 08:01 39328068   /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le32d4.cache-4
b3802000-b3806000 r--s 00000000 08:01 39328067   /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le32d4.cache-4
b3806000-b3808000 r-xp 00000000 08:01 41160145   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3808000-b3809000 r--p 00001000 08:01 41160145   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b3809000-b380a000 rw-p 00002000 08:01 41160145   /usr/lib/i386-linux-gnu/libXau.so.6.0.0
b380a000-b3813000 r-xp 00000000 08:01 41159930   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3813000-b3814000 r--p 00008000 08:01 41159930   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3814000-b3815000 rw-p 00009000 08:01 41159930   /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
b3815000-b381c000 r--s 00000000 08:01 39323694   /var/cache/fontconfig/52f7bdb7ce746bfd7eaa1985bd9cfa93-le32d4.cache-4
b381c000-b3823000 r--s 00000000 08:01 39323692   /var/cache/fontconfig/3f7329c5293ffd510edef78f73874cfd-le32d4.cache-4
b3823000-b382c000 r--s 00000000 08:01 39322115   /var/cache/fontconfig/d589a48862398ed80a3d6066f4f56f4c-le32d4.cache-4
b382c000-b382f000 r--s 00000000 08:01 39323165   /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-4
b382f000-b387a000 r-xp 00000000 08:01 42863378   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/xawt/libmawt.so
b387a000-b387b000 r--p 0004a000 08:01 42863378   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/xawt/libmawt.so
b387b000-b387d000 rw-p 0004b000 08:01 42863378   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/xawt/libmawt.so
b387d000-b387e000 rw-p 00000000 00:00 0 
b387e000-b387f000 ---p 00000000 00:00 0 
b387f000-b38ff000 rw-p 00000000 00:00 0          [stack:3968]
b38ff000-b3902000 ---p 00000000 00:00 0 
b3902000-b3b00000 rw-p 00000000 00:00 0          [stack:3964]
b3b00000-b3c00000 rw-p 00000000 00:00 0 
b3c00000-b3c01000 r--s 00000000 08:01 39328017   /var/cache/fontconfig/0c9eb80ebd1c36541ebe2852d3bb0c49-le32d4.cache-4
b3c01000-b3c12000 r-xp 00000000 08:01 41161824   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b3c12000-b3c13000 r--p 00010000 08:01 41161824   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b3c13000-b3c14000 rw-p 00011000 08:01 41161824   /usr/lib/i386-linux-gnu/libXext.so.6.4.0
b3c14000-b3c1c000 r-xp 00000000 08:01 42468686   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnio.so
b3c1c000-b3c1d000 r--p 00007000 08:01 42468686   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnio.so
b3c1d000-b3c1e000 rw-p 00008000 08:01 42468686   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnio.so
b3c1e000-b3c7e000 r--s 00dc1000 08:01 45750233   /usr/lib/jvm/java-6-openjdk-i386/lib/tools.jar
b3c7e000-b3c81000 ---p 00000000 00:00 0 
b3c81000-b3cff000 rw-p 00000000 00:00 0          [stack:3966]
b3cff000-b3d02000 ---p 00000000 00:00 0 
b3d02000-b3f00000 rw-p 00000000 00:00 0          [stack:3963]
b3f00000-b3f40000 rw-p 00000000 00:00 0 
b3f40000-b4000000 ---p 00000000 00:00 0 
b4000000-b4002000 r--s 00000000 08:01 39326727   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-4
b4002000-b4007000 r-xp 00000000 08:01 41162590   /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
b4007000-b4008000 r--p 00004000 08:01 41162590   /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
b4008000-b4009000 rw-p 00005000 08:01 41162590   /usr/lib/i386-linux-gnu/libXtst.so.6.1.0
b4009000-b401f000 r-xp 00000000 08:01 42468693   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnet.so
b401f000-b4020000 r--p 00015000 08:01 42468693   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnet.so
b4020000-b4021000 rw-p 00016000 08:01 42468693   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libnet.so
b4021000-b4027000 r--s 0001f000 08:01 45750231   /usr/lib/jvm/java-6-openjdk-i386/lib/dt.jar
b4027000-b402a000 r--s 00046000 08:01 45750167   /usr/share/netbeans/7.0.1/nb/core/org-netbeans-upgrader.jar
b402a000-b402b000 ---p 00000000 00:00 0 
b402b000-b40de000 rw-p 00000000 00:00 0          [stack:3962]
b40de000-b4272000 r--s 03822000 08:01 42468708   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/rt.jar
b4272000-b4283000 rw-p 00000000 00:00 0 
b4283000-b4333000 rw-p 00000000 00:00 0 
b4333000-b433e000 rw-p 00000000 00:00 0 
b433e000-b4434000 rw-p 00000000 00:00 0 
b4434000-b443a000 rw-p 00000000 00:00 0 
b443a000-b44b4000 rw-p 00000000 00:00 0 
b44b4000-b44bf000 rw-p 00000000 00:00 0 
b44bf000-b45b4000 rw-p 00000000 00:00 0 
b45b4000-b45c4000 rw-p 00000000 00:00 0 
b45c4000-b4674000 rw-p 00000000 00:00 0 
b4674000-b468b000 rw-p 00000000 00:00 0 
b468b000-b4700000 rw-p 00000000 00:00 0 
b4700000-b49b8000 rwxp 00000000 00:00 0 
b49b8000-b67ee000 rw-p 00000000 00:00 0 
b67ee000-b6800000 ---p 00000000 00:00 0 
b6800000-b6801000 r--s 00000000 08:01 37491706   /home/kelsey/.cache/fontconfig/bc3ab073c8b8f89d832a4c726bf2d75b-le32d4.cache-4
b6801000-b6802000 r--s 00047000 08:01 45750169   /usr/share/netbeans/7.0.1/nb/core/locale/core_nb.jar
b6802000-b6809000 r--s 000a0000 08:01 45618003   /usr/share/netbeans/platform13/core/org-openide-filesystems.jar
b6809000-b680e000 r--s 00099000 08:01 45618002   /usr/share/netbeans/platform13/core/core.jar
b680e000-b6811000 r--s 00034000 08:01 41556343   /usr/share/java/org-openide-util-lookup-7.0.jar
b6811000-b6818000 r--s 0007d000 08:01 41556345   /usr/share/java/org-openide-util-7.0.jar
b6818000-b6819000 r--s 00007000 08:01 41556349   /usr/share/java/org-openide-modules-7.0.jar
b6819000-b6820000 r--s 000fc000 08:01 41167458   /usr/lib/jvm/java-6-openjdk-common/jre/lib/resources.jar
b6820000-b6823000 r--s 00045000 08:01 45618132   /usr/share/netbeans/platform13/lib/boot.jar
b6823000-b6826000 r--s 00077000 08:01 41167440   /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/localedata.jar
b6826000-b6828000 r--s 00001000 08:01 41167438   /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/dnsns.jar
b6828000-b682c000 r--s 00039000 08:01 41167442   /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/sunpkcs11.jar
b682c000-b682f000 r--s 00031000 08:01 41167441   /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/sunjce_provider.jar
b682f000-b6831000 r--s 00006000 08:01 41554222   /usr/share/java/java-atk-wrapper.jar
b6831000-b683c000 r-xp 00000000 08:01 32245021   /lib/i386-linux-gnu/libnss_files-2.17.so
b683c000-b683d000 r--p 0000a000 08:01 32245021   /lib/i386-linux-gnu/libnss_files-2.17.so
b683d000-b683e000 rw-p 0000b000 08:01 32245021   /lib/i386-linux-gnu/libnss_files-2.17.so
b683e000-b6848000 r-xp 00000000 08:01 32245017   /lib/i386-linux-gnu/libnss_nis-2.17.so
b6848000-b6849000 r--p 00009000 08:01 32245017   /lib/i386-linux-gnu/libnss_nis-2.17.so
b6849000-b684a000 rw-p 0000a000 08:01 32245017   /lib/i386-linux-gnu/libnss_nis-2.17.so
b684a000-b685f000 r-xp 00000000 08:01 32245002   /lib/i386-linux-gnu/libnsl-2.17.so
b685f000-b6860000 r--p 00014000 08:01 32245002   /lib/i386-linux-gnu/libnsl-2.17.so
b6860000-b6861000 rw-p 00015000 08:01 32245002   /lib/i386-linux-gnu/libnsl-2.17.so
b6861000-b6863000 rw-p 00000000 00:00 0 
b6863000-b686a000 r-xp 00000000 08:01 32245012   /lib/i386-linux-gnu/libnss_compat-2.17.so
b686a000-b686b000 r--p 00006000 08:01 32245012   /lib/i386-linux-gnu/libnss_compat-2.17.so
b686b000-b686c000 rw-p 00007000 08:01 32245012   /lib/i386-linux-gnu/libnss_compat-2.17.so
b686c000-b686f000 r--s 0000f000 08:01 41167439   /usr/lib/jvm/java-6-openjdk-common/jre/lib/ext/pulse-java.jar
b686f000-b6870000 r--p 005e0000 08:01 41164293   /usr/lib/locale/locale-archive
b6870000-b687d000 rw-p 00000000 00:00 0 
b687d000-b6884000 r-xp 00000000 08:01 42468688   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
b6884000-b6885000 r--p 00006000 08:01 42468688   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
b6885000-b6886000 rw-p 00007000 08:01 42468688   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libzip.so
b6886000-b68ad000 r-xp 00000000 08:01 42468675   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
b68ad000-b68ae000 r--p 00026000 08:01 42468675   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
b68ae000-b68b0000 rw-p 00027000 08:01 42468675   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libjava.so
b68b0000-b68b7000 r-xp 00000000 08:01 32244759   /lib/i386-linux-gnu/librt-2.17.so
b68b7000-b68b8000 r--p 00006000 08:01 32244759   /lib/i386-linux-gnu/librt-2.17.so
b68b8000-b68b9000 rw-p 00007000 08:01 32244759   /lib/i386-linux-gnu/librt-2.17.so
b68b9000-b68bc000 ---p 00000000 00:00 0 
b68bc000-b6aba000 rw-p 00000000 00:00 0          [stack:3961]
b6aba000-b6ad5000 r-xp 00000000 08:01 32243750   /lib/i386-linux-gnu/libgcc_s.so.1
b6ad5000-b6ad6000 r--p 0001a000 08:01 32243750   /lib/i386-linux-gnu/libgcc_s.so.1
b6ad6000-b6ad7000 rw-p 0001b000 08:01 32243750   /lib/i386-linux-gnu/libgcc_s.so.1
b6ad7000-b6b18000 r-xp 00000000 08:01 32245015   /lib/i386-linux-gnu/libm-2.17.so
b6b18000-b6b19000 r--p 00040000 08:01 32245015   /lib/i386-linux-gnu/libm-2.17.so
b6b19000-b6b1a000 rw-p 00041000 08:01 32245015   /lib/i386-linux-gnu/libm-2.17.so
b6b1a000-b6bf7000 r-xp 00000000 08:01 41157084   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
b6bf7000-b6bfb000 r--p 000dc000 08:01 41157084   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
b6bfb000-b6bfc000 rw-p 000e0000 08:01 41157084   /usr/lib/i386-linux-gnu/libstdc++.so.6.0.18
b6bfc000-b6c03000 rw-p 00000000 00:00 0 
b6c03000-b7108000 r-xp 00000000 08:01 42730186   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
b7108000-b711d000 r--p 00504000 08:01 42730186   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
b711d000-b712a000 rw-p 00519000 08:01 42730186   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client/libjvm.so
b712a000-b7544000 rw-p 00000000 00:00 0 
b7544000-b755c000 r-xp 00000000 08:01 32244559   /lib/i386-linux-gnu/libz.so.1.2.8
b755c000-b755d000 r--p 00017000 08:01 32244559   /lib/i386-linux-gnu/libz.so.1.2.8
b755d000-b755e000 rw-p 00018000 08:01 32244559   /lib/i386-linux-gnu/libz.so.1.2.8
b755e000-b770c000 r-xp 00000000 08:01 32245009   /lib/i386-linux-gnu/libc-2.17.so
b770c000-b770e000 r--p 001ae000 08:01 32245009   /lib/i386-linux-gnu/libc-2.17.so
b770e000-b770f000 rw-p 001b0000 08:01 32245009   /lib/i386-linux-gnu/libc-2.17.so
b770f000-b7712000 rw-p 00000000 00:00 0 
b7712000-b7715000 r-xp 00000000 08:01 32245010   /lib/i386-linux-gnu/libdl-2.17.so
b7715000-b7716000 r--p 00002000 08:01 32245010   /lib/i386-linux-gnu/libdl-2.17.so
b7716000-b7717000 rw-p 00003000 08:01 32245010   /lib/i386-linux-gnu/libdl-2.17.so
b7717000-b771a000 r-xp 00000000 08:01 42468678   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
b771a000-b771b000 r--p 00002000 08:01 42468678   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
b771b000-b771c000 rw-p 00003000 08:01 42468678   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/jli/libjli.so
b771c000-b771d000 rw-p 00000000 00:00 0 
b771d000-b7734000 r-xp 00000000 08:01 32245014   /lib/i386-linux-gnu/libpthread-2.17.so
b7734000-b7735000 r--p 00016000 08:01 32245014   /lib/i386-linux-gnu/libpthread-2.17.so
b7735000-b7736000 rw-p 00017000 08:01 32245014   /lib/i386-linux-gnu/libpthread-2.17.so
b7736000-b7738000 rw-p 00000000 00:00 0 
b7738000-b7740000 rw-s 00000000 08:01 45089196   /tmp/hsperfdata_kelsey/3960
b7740000-b7741000 rw-p 00000000 00:00 0 
b7741000-b7742000 r--p 00000000 00:00 0 
b7742000-b774f000 r-xp 00000000 08:01 42468687   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
b774f000-b7750000 ---p 0000d000 08:01 42468687   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
b7750000-b7751000 r--p 0000d000 08:01 42468687   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
b7751000-b7752000 rw-p 0000e000 08:01 42468687   /usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/libverify.so
b7752000-b7754000 rw-p 00000000 00:00 0 
b7754000-b7755000 r-xp 00000000 00:00 0          [vdso]
b7755000-b7775000 r-xp 00000000 08:01 32245005   /lib/i386-linux-gnu/ld-2.17.so
b7775000-b7776000 r--p 0001f000 08:01 32245005   /lib/i386-linux-gnu/ld-2.17.so
b7776000-b7777000 rw-p 00020000 08:01 32245005   /lib/i386-linux-gnu/ld-2.17.so
bf7ee000-bf810000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Djdk.home=/usr/lib/jvm/java-6-openjdk-i386 -Djava.library.path=/usr/lib/jni -Dnetbeans.system_http_proxy=DIRECT -Dnetbeans.system_http_non_proxy_hosts= -Dnetbeans.dirs=/usr/share/netbeans/7.0.1/nb:/usr/share/netbeans/7.0.1/bin/../ergonomics:/usr/share/netbeans/7.0.1/ide:/usr/share/netbeans/7.0.1/java:/usr/share/netbeans/7.0.1/bin/../xml:/usr/share/netbeans/7.0.1/apisupport:/usr/share/netbeans/7.0.1/bin/../webcommon:/usr/share/netbeans/7.0.1/bin/../websvccommon:/usr/share/netbeans/7.0.1/bin/../enterprise:/usr/share/netbeans/7.0.1/bin/../mobility:/usr/share/netbeans/7.0.1/bin/../profiler:/usr/share/netbeans/7.0.1/bin/../ruby:/usr/share/netbeans/7.0.1/bin/../python:/usr/share/netbeans/7.0.1/bin/../php:/usr/share/netbeans/7.0.1/bin/../visualweb:/usr/share/netbeans/7.0.1/bin/../soa:/usr/share/netbeans/7.0.1/bin/../identity:/usr/share/netbeans/7.0.1/bin/../uml:/usr/share/netbeans/7.0.1/harness:/usr/share/netbeans/7.0.1/bin/../cnd:/usr/share/netbeans/7.0.1/bin/../dlight:/usr/share/netbeans/7.0.1/bin/../groovy:/usr/share/netbeans/7.0.1/bin/../extra:/usr/share/netbeans/7.0.1/bin/../javafx:/usr/share/netbeans/7.0.1/bin/../javacard: -Dnetbeans.home=/usr/share/netbeans/7.0.1/platform -Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade -Dnetbeans.accept_license_class=org.netbeans.license.AcceptLicense -XX:MaxPermSize=384m -Xmx768m -Xss2m -Xms32m -XX:PermSize=32m -Dapple.laf.useScreenMenuBar=true -Dapple.awt.graphics.UseQuartz=true -Dsun.java2d.noddraw=true -Dsun.java2d.pmoffscreen=false -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/kelsey/.netbeans/7.0/var/log/heapdump.hprof 
java_command: org.netbeans.Main --userdir /home/kelsey/.netbeans/7.0 --branding nb
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk-i386/jre/lib/i386:/usr/lib/jvm/java-6-openjdk-i386/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ecac0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ecac0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30c510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x30c510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30c510], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30c260], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30ee70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGTERM: [libjvm.so+0x30ee70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30ee70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 13.10 (saucy)
uname:Linux 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
libc:glibc 2.17 NPTL 2.17 
rlimit: STACK 8192k, CORE 0k, NPROC 31094, NOFILE 4096, AS infinity
load average:0.34 0.31 0.41

/proc/meminfo:
MemTotal:        3997672 kB
MemFree:         2627144 kB
Buffers:           74248 kB
Cached:           686564 kB
SwapCached:            0 kB
Active:           726140 kB
Inactive:         546180 kB
Active(anon):     512392 kB
Inactive(anon):     6900 kB
Active(file):     213748 kB
Inactive(file):   539280 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       3141512 kB
HighFree:        1919120 kB
LowTotal:         856160 kB
LowFree:          708024 kB
SwapTotal:       4052988 kB
SwapFree:        4052988 kB
Dirty:               320 kB
Writeback:             0 kB
AnonPages:        511948 kB
Mapped:           140408 kB
Shmem:              7788 kB
Slab:              57920 kB
SReclaimable:      38184 kB
SUnreclaim:        19736 kB
KernelStack:        4104 kB
PageTables:         8204 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6051824 kB
Committed_AS:    3298956 kB
VmallocTotal:     122880 kB
VmallocUsed:       19512 kB
VmallocChunk:     100260 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       10232 kB
DirectMap2M:      903168 kB


CPU:total 4 (2 cores per cpu, 2 threads per core) family 6 model 37 stepping 5, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1, sse4.2, popcnt, ht

Memory: 4k page, physical 3997672k(2627144k free), swap 4052988k(4052988k free)

vm_info: OpenJDK Client VM (20.0-b12) for linux-x86 JRE (1.6.0_27-b27), built on Nov 15 2013 14:48:41 by "buildd" with gcc 4.8.1

time: Sat Jan  4 16:31:49 2014
elapsed time: 2 seconds
```


It installed fine with no problems with software center, tried the fix for installing GTK2+ engine packages and nothing. Tried changing default directory in netbeans.conf to point it to the older directory, no change. re-installed the whole thing and rebooted a few times, still nothing. I'm intermediate with Ubuntu, under version 3.11.0-15 right now.

Anyone can give me some insight what's missing please?

Thanks.

---

### Post by QIII on 2014-01-04
A question first:  Are you really using Java/OpenJDK 6?

---

### Post by Rtedmonston on 2014-01-04
> **QIII said:**
> A question first:  Are you really using Java/OpenJDK 6?


Yes, I have Java OpenJDK Java Runtime 6 & 7 installed. Before i had just 6, first time it gave me that error.

---

### Post by Rtedmonston on 2014-01-04
Nvm, had wrong version installed, I feel like a derp. Issue resolved, close thread now please.

---

### Post by QIII on 2014-01-04
No problem.  If you only derp once a day, you are far better than me!

We don't usually close threads without cause, but if you want you can mark it solved with the "Thread tools" button.

---

