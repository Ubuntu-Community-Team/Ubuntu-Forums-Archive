---
title: "jre error"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-05-03
Hi friends,
i try to run kettle data integration tool, iam getting following error.

```
A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x01bf3cba, pid=2148, tid=2308959088
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.13
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.13-0ubuntu1~10.04.1
# Problematic frame:
# C  [libmozjs.so+0x1acba]  js_NextActiveContext+0x16
#
# An error report file with more information is saved as:
# /home/jug/Desktop/Kettle/data-integration/hs_err_pid2148.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#
Aborted

Error log file:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x01bf3cba, pid=2148, tid=2308959088
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Server VM (19.0-b09 mixed mode linux-x86 )
# Derivative: IcedTea6 1.9.13
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.13-0ubuntu1~10.04.1
# Problematic frame:
# C  [libmozjs.so+0x1acba]  js_NextActiveContext+0x16
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
#

---------------  T H R E A D  ---------------

Current thread is native thread

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x0000019c

Registers:
EAX=0xfffffffc, EBX=0x03dd9ff4, ECX=0x899fe30c, EDX=0x8aac0c80
ESP=0x899fe300, EBP=0x899fe318, ESI=0x899fe30c, EDI=0x8aac0b18
EIP=0x01bf3cba, CR2=0x0000019c, EFLAGS=0x00010286

Register to memory mapping:

EAX=0xfffffffc
0xfffffffc is pointing to unknown location

EBX=0x03dd9ff4
0x03dd9ff4: <offset 0xc61ff4> in /usr/lib/xulrunner-1.9.1.3/libxul.so at 0x03178000

ECX=0x899fe30c
0x899fe30c is pointing to unknown location

EDX=0x8aac0c80
0x8aac0c80 is pointing to unknown location

ESP=0x899fe300
0x899fe300 is pointing to unknown location

EBP=0x899fe318
0x899fe318 is pointing to unknown location

ESI=0x899fe30c
0x899fe30c is pointing to unknown location

EDI=0x8aac0b18
0x8aac0b18 is pointing to unknown location


Top of Stack: (sp=0x899fe300)
0x899fe300:   899fe358 00bf4230 8aac2898 fffffffc
0x899fe310:   8a4fd2c8 8aac0b18 899fe358 0333a57b
0x899fe320:   8aac0b18 00000000 8aac2898 8aac2898
0x899fe330:   8a570380 00000001 899fe358 02349df0
0x899fe340:   8a570380 00000000 00000000 02359ff4
0x899fe350:   8aac2d78 00000001 899fe398 023500b7
0x899fe360:   8a4fd2c8 8aac2d78 00000000 00000000
0x899fe370:   00000000 00000000 00000000 8aac2e28 

Instructions: (pc=0x01bf3cba)
0x01bf3caa:   ec 10 8b 45 0c 8b 7d 08 8d 75 f4 89 45 f4 eb 09
0x01bf3cba:   83 b8 a0 01 00 00 00 75 11 50 56 6a 00 57 e8 57 

Stack: [0x891fe000,0x899ff000],  sp=0x899fe300,  free space=8192k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libmozjs.so+0x1acba]  js_NextActiveContext+0x16
C  [libxul.so+0x1c257b]
C  [libnspr4.so+0x280b7]
C  [libpthread.so.0+0x596e]


---------------  P R O C E S S  ---------------

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 95936K, used 16078K [0xa9ba0000, 0xb4640000, 0xb4640000)
  eden space 92672K, 13% used [0xa9ba0000,0xaa8265d0,0xaf620000)
  from space 3264K, 99% used [0xaf620000,0xaf94d560,0xaf950000)
  to   space 4864K, 0% used [0xb4180000,0xb4180000,0xb4640000)
 PSOldGen        total 30912K, used 4572K [0x94640000, 0x96470000, 0xa9ba0000)
  object space 30912K, 14% used [0x94640000,0x94ab7278,0x96470000)
 PSPermGen       total 19584K, used 19502K [0x8c640000, 0x8d960000, 0x94640000)
  object space 19584K, 99% used [0x8c640000,0x8d94b9b8,0x8d960000)

Dynamic libraries:
00110000-00123000 r-xp 00000000 08:01 537        /lib/libz.so.1.2.3.3
00123000-00124000 r--p 00012000 08:01 537        /lib/libz.so.1.2.3.3
00124000-00125000 rw-p 00013000 08:01 537        /lib/libz.so.1.2.3.3
00125000-00278000 r-xp 00000000 08:01 1994530    /lib/tls/i686/cmov/libc-2.11.1.so
00278000-00279000 ---p 00153000 08:01 1994530    /lib/tls/i686/cmov/libc-2.11.1.so
00279000-0027b000 r--p 00153000 08:01 1994530    /lib/tls/i686/cmov/libc-2.11.1.so
0027b000-0027c000 rw-p 00155000 08:01 1994530    /lib/tls/i686/cmov/libc-2.11.1.so
0027c000-0027f000 rw-p 00000000 00:00 0 
0027f000-002a3000 r-xp 00000000 08:01 1994534    /lib/tls/i686/cmov/libm-2.11.1.so
002a3000-002a4000 r--p 00023000 08:01 1994534    /lib/tls/i686/cmov/libm-2.11.1.so
002a4000-002a5000 rw-p 00024000 08:01 1994534    /lib/tls/i686/cmov/libm-2.11.1.so
002a5000-002ad000 r-xp 00000000 08:01 1994541    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002ad000-002ae000 r--p 00007000 08:01 1994541    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002ae000-002af000 rw-p 00008000 08:01 1994541    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
002af000-002b9000 r-xp 00000000 08:01 1994539    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002b9000-002ba000 r--p 00009000 08:01 1994539    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002ba000-002bb000 rw-p 0000a000 08:01 1994539    /lib/tls/i686/cmov/libnss_files-2.11.1.so
002bb000-002bf000 r-xp 00000000 08:01 86666      /usr/lib/libgthread-2.0.so.0.2400.1
002bf000-002c0000 r--p 00003000 08:01 86666      /usr/lib/libgthread-2.0.so.0.2400.1
002c0000-002c1000 rw-p 00004000 08:01 86666      /usr/lib/libgthread-2.0.so.0.2400.1
002c1000-002cf000 r-xp 00000000 08:01 122        /usr/lib/libXext.so.6.4.0
002cf000-002d0000 r--p 0000d000 08:01 122        /usr/lib/libXext.so.6.4.0
002d0000-002d1000 rw-p 0000e000 08:01 122        /usr/lib/libXext.so.6.4.0
002d1000-002dd000 r-xp 00000000 08:01 134        /usr/lib/libXi.so.6.1.0
002dd000-002de000 r--p 0000c000 08:01 134        /usr/lib/libXi.so.6.1.0
002de000-002df000 rw-p 0000d000 08:01 134        /usr/lib/libXi.so.6.1.0
002df000-002e3000 r-xp 00000000 08:01 2142       /usr/lib/libXfixes.so.3.1.0
002e3000-002e4000 r--p 00003000 08:01 2142       /usr/lib/libXfixes.so.3.1.0
002e4000-002e5000 rw-p 00004000 08:01 2142       /usr/lib/libXfixes.so.3.1.0
002e7000-0030b000 r-xp 00000000 08:01 5917202    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0030b000-0030c000 r--p 00023000 08:01 5917202    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0030c000-0030e000 rw-p 00024000 08:01 5917202    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0030e000-00316000 r-xp 00000000 08:01 2181       /usr/lib/libXcursor.so.1.0.2
00316000-00317000 r--p 00007000 08:01 2181       /usr/lib/libXcursor.so.1.0.2
00317000-00318000 rw-p 00008000 08:01 2181       /usr/lib/libXcursor.so.1.0.2
00318000-0031b000 r-xp 00000000 08:01 86665      /usr/lib/libgmodule-2.0.so.0.2400.1
0031b000-0031c000 r--p 00002000 08:01 86665      /usr/lib/libgmodule-2.0.so.0.2400.1
0031c000-0031d000 rw-p 00003000 08:01 86665      /usr/lib/libgmodule-2.0.so.0.2400.1
0031d000-0031f000 r-xp 00000000 08:01 84         /usr/lib/libXau.so.6.0.0
0031f000-00320000 r--p 00001000 08:01 84         /usr/lib/libXau.so.6.0.0
00320000-00321000 rw-p 00002000 08:01 84         /usr/lib/libXau.so.6.0.0
00321000-00336000 r-xp 00000000 08:01 1994544    /lib/tls/i686/cmov/libpthread-2.11.1.so
00336000-00337000 r--p 00014000 08:01 1994544    /lib/tls/i686/cmov/libpthread-2.11.1.so
00337000-00338000 rw-p 00015000 08:01 1994544    /lib/tls/i686/cmov/libpthread-2.11.1.so
00338000-0033a000 rw-p 00000000 00:00 0 
0033a000-00352000 r-xp 00000000 08:01 1505       /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00352000-00353000 r--p 00017000 08:01 1505       /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00353000-00354000 rw-p 00018000 08:01 1505       /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00354000-0035c000 r-xp 00000000 08:01 3323       /usr/lib/libfusion-1.2.so.0.8.0
0035c000-0035d000 r--p 00007000 08:01 3323       /usr/lib/libfusion-1.2.so.0.8.0
0035d000-0035e000 rw-p 00008000 08:01 3323       /usr/lib/libfusion-1.2.so.0.8.0
0035e000-00361000 r-xp 00000000 08:01 1807       /usr/lib/libxcb-render-util.so.0.0.0
00361000-00362000 r--p 00002000 08:01 1807       /usr/lib/libxcb-render-util.so.0.0.0
00362000-00363000 rw-p 00003000 08:01 1807       /usr/lib/libxcb-render-util.so.0.0.0
00363000-00369000 r-xp 00000000 08:01 1801       /usr/lib/libxcb-render.so.0.0.0
00369000-0036a000 r--p 00005000 08:01 1801       /usr/lib/libxcb-render.so.0.0.0
0036a000-0036b000 rw-p 00006000 08:01 1801       /usr/lib/libxcb-render.so.0.0.0
0036b000-00371000 r-xp 00000000 08:01 1994537    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00371000-00372000 r--p 00006000 08:01 1994537    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00372000-00373000 rw-p 00007000 08:01 1994537    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
00373000-003c8000 r-xp 00000000 08:01 5518839    /tmp/swtlib-32/libswt-pi-gtk-3557.so
003c8000-003cb000 rw-p 00054000 08:01 5518839    /tmp/swtlib-32/libswt-pi-gtk-3557.so
003cb000-003e4000 r-xp 00000000 08:01 964        /usr/lib/libatk-1.0.so.0.3009.1
003e4000-003e5000 ---p 00019000 08:01 964        /usr/lib/libatk-1.0.so.0.3009.1
003e5000-003e6000 r--p 00019000 08:01 964        /usr/lib/libatk-1.0.so.0.3009.1
003e6000-003e7000 rw-p 0001a000 08:01 964        /usr/lib/libatk-1.0.so.0.3009.1
003e7000-0040c000 r-xp 00000000 08:01 2112       /usr/lib/libpangoft2-1.0.so.0.2800.0
0040c000-0040d000 r--p 00024000 08:01 2112       /usr/lib/libpangoft2-1.0.so.0.2800.0
0040d000-0040e000 rw-p 00025000 08:01 2112       /usr/lib/libpangoft2-1.0.so.0.2800.0
0040e000-0044e000 r-xp 00000000 08:01 2100       /usr/lib/libpango-1.0.so.0.2800.0
0044e000-0044f000 ---p 00040000 08:01 2100       /usr/lib/libpango-1.0.so.0.2800.0
0044f000-00450000 r--p 00040000 08:01 2100       /usr/lib/libpango-1.0.so.0.2800.0
00450000-00451000 rw-p 00041000 08:01 2100       /usr/lib/libpango-1.0.so.0.2800.0
00451000-00455000 r-xp 00000000 08:01 88         /usr/lib/libXdmcp.so.6.0.0
00455000-00456000 r--p 00003000 08:01 88         /usr/lib/libXdmcp.so.6.0.0
00456000-00457000 rw-p 00004000 08:01 88         /usr/lib/libXdmcp.so.6.0.0
00457000-0045b000 r-xp 00000000 08:01 706752     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0045b000-0045c000 ---p 00004000 08:01 706752     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0045c000-0045d000 r--p 00004000 08:01 706752     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0045d000-0045e000 rw-p 00005000 08:01 706752     /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
0045f000-00466000 r-xp 00000000 08:01 1994546    /lib/tls/i686/cmov/librt-2.11.1.so
00466000-00467000 r--p 00006000 08:01 1994546    /lib/tls/i686/cmov/librt-2.11.1.so
00467000-00468000 rw-p 00007000 08:01 1994546    /lib/tls/i686/cmov/librt-2.11.1.so
00468000-004fb000 r-xp 00000000 08:01 1504       /usr/lib/libgdk-x11-2.0.so.0.2000.1
004fb000-004fd000 r--p 00093000 08:01 1504       /usr/lib/libgdk-x11-2.0.so.0.2000.1
004fd000-004fe000 rw-p 00095000 08:01 1504       /usr/lib/libgdk-x11-2.0.so.0.2000.1
004fe000-00501000 r-xp 00000000 08:01 2674       /usr/lib/libcanberra-gtk.so.0.1.5
00501000-00502000 r--p 00003000 08:01 2674       /usr/lib/libcanberra-gtk.so.0.1.5
00502000-00503000 rw-p 00004000 08:01 2674       /usr/lib/libcanberra-gtk.so.0.1.5
00503000-00507000 rwxp 00000000 00:00 0 
00507000-00509000 r-xp 00000000 08:01 2208       /usr/lib/libXdamage.so.1.1.0
00509000-0050a000 r--p 00001000 08:01 2208       /usr/lib/libXdamage.so.1.1.0
0050a000-0050b000 rw-p 00002000 08:01 2208       /usr/lib/libXdamage.so.1.1.0
0050b000-00539000 r-xp 00000000 08:01 2367       /usr/lib/libfontconfig.so.1.4.4
00539000-0053a000 r--p 0002d000 08:01 2367       /usr/lib/libfontconfig.so.1.4.4
0053a000-0053b000 rw-p 0002e000 08:01 2367       /usr/lib/libfontconfig.so.1.4.4
0053b000-00549000 r-xp 00000000 08:01 3526       /usr/lib/libcanberra.so.0.2.1
00549000-0054a000 r--p 0000d000 08:01 3526       /usr/lib/libcanberra.so.0.2.1
0054a000-0054b000 rw-p 0000e000 08:01 3526       /usr/lib/libcanberra.so.0.2.1
0054c000-0055f000 r-xp 00000000 08:01 1994536    /lib/tls/i686/cmov/libnsl-2.11.1.so
0055f000-00560000 r--p 00012000 08:01 1994536    /lib/tls/i686/cmov/libnsl-2.11.1.so
00560000-00561000 rw-p 00013000 08:01 1994536    /lib/tls/i686/cmov/libnsl-2.11.1.so
00561000-00563000 rw-p 00000000 00:00 0 
00563000-0056a000 r-xp 00000000 08:01 3292       /usr/lib/libvorbisfile.so.3.3.2
0056a000-0056b000 r--p 00006000 08:01 3292       /usr/lib/libvorbisfile.so.3.3.2
0056b000-0056c000 rw-p 00007000 08:01 3292       /usr/lib/libvorbisfile.so.3.3.2
0056c000-00571000 r-xp 00000000 08:01 1107       /usr/lib/libogg.so.0.6.0
00571000-00572000 r--p 00004000 08:01 1107       /usr/lib/libogg.so.0.6.0
00572000-00573000 rw-p 00005000 08:01 1107       /usr/lib/libogg.so.0.6.0
00576000-0057e000 r-xp 00000000 08:01 1812       /usr/lib/libXrender.so.1.3.0
0057e000-0057f000 r--p 00007000 08:01 1812       /usr/lib/libXrender.so.1.3.0
0057f000-00580000 rw-p 00008000 08:01 1812       /usr/lib/libXrender.so.1.3.0
00580000-005bd000 r-xp 00000000 08:01 86664      /usr/lib/libgobject-2.0.so.0.2400.1
005bd000-005be000 r--p 0003c000 08:01 86664      /usr/lib/libgobject-2.0.so.0.2400.1
005be000-005bf000 rw-p 0003d000 08:01 86664      /usr/lib/libgobject-2.0.so.0.2400.1
005bf000-005c1000 r-xp 00000000 08:01 918618     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
005c1000-005c2000 r--p 00001000 08:01 918618     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
005c2000-005c3000 rw-p 00002000 08:01 918618     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
005c6000-005c8000 r-xp 00000000 08:01 2210       /usr/lib/libXinerama.so.1.0.0
005c8000-005c9000 r--p 00001000 08:01 2210       /usr/lib/libXinerama.so.1.0.0
005c9000-005ca000 rw-p 00002000 08:01 2210       /usr/lib/libXinerama.so.1.0.0
005ca000-005f9000 r-xp 00000000 08:01 1312       /lib/libpcre.so.3.12.1
005f9000-005fa000 r--p 0002e000 08:01 1312       /lib/libpcre.so.3.12.1
005fa000-005fb000 rw-p 0002f000 08:01 1312       /lib/libpcre.so.3.12.1
005fb000-00613000 r-xp 00000000 08:01 95         /usr/lib/libxcb.so.1.1.0
00613000-00614000 r--p 00017000 08:01 95         /usr/lib/libxcb.so.1.1.0
00614000-00615000 rw-p 00018000 08:01 95         /usr/lib/libxcb.so.1.1.0
00615000-0061c000 r-xp 00000000 08:01 581        /usr/lib/libltdl.so.7.2.1
0061c000-0061d000 r--p 00006000 08:01 581        /usr/lib/libltdl.so.7.2.1
0061d000-0061e000 rw-p 00007000 08:01 581        /usr/lib/libltdl.so.7.2.1
0061f000-0062b000 r-xp 00000000 08:01 5917218    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
0062b000-0062c000 r--p 0000b000 08:01 5917218    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
0062c000-0062d000 rw-p 0000c000 08:01 5917218    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
0062d000-00684000 r-xp 00000000 08:01 1799       /usr/lib/libpixman-1.so.0.16.4
00684000-00686000 r--p 00057000 08:01 1799       /usr/lib/libpixman-1.so.0.16.4
00686000-00687000 rw-p 00059000 08:01 1799       /usr/lib/libpixman-1.so.0.16.4
00687000-0068d000 r-xp 00000000 08:01 5518840    /tmp/swtlib-32/libswt-atk-gtk-3557.so
0068d000-0068e000 rw-p 00005000 08:01 5518840    /tmp/swtlib-32/libswt-atk-gtk-3557.so
00691000-00697000 r-xp 00000000 08:01 2477       /usr/lib/libXrandr.so.2.2.0
00697000-00698000 r--p 00005000 08:01 2477       /usr/lib/libXrandr.so.2.2.0
00698000-00699000 rw-p 00006000 08:01 2477       /usr/lib/libXrandr.so.2.2.0
00699000-0069e000 r-xp 00000000 08:01 679211     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
0069e000-0069f000 r--p 00004000 08:01 679211     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
0069f000-006a0000 rw-p 00005000 08:01 679211     /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
006a0000-006a5000 r-xp 00000000 08:01 5518841    /tmp/swtlib-32/libswt-xpcominit-gtk-3557.so
006a5000-006a7000 rw-p 00005000 08:01 5518841    /tmp/swtlib-32/libswt-xpcominit-gtk-3557.so
006a7000-006b1000 r-xp 00000000 08:01 2109       /usr/lib/libpangocairo-1.0.so.0.2800.0
006b1000-006b2000 r--p 00009000 08:01 2109       /usr/lib/libpangocairo-1.0.so.0.2800.0
006b2000-006b3000 rw-p 0000a000 08:01 2109       /usr/lib/libpangocairo-1.0.so.0.2800.0
006b3000-007cc000 r-xp 00000000 08:01 119        /usr/lib/libX11.so.6.3.0
007cc000-007cd000 r--p 00118000 08:01 119        /usr/lib/libX11.so.6.3.0
007cd000-007cf000 rw-p 00119000 08:01 119        /usr/lib/libX11.so.6.3.0
007cf000-007d0000 rw-p 00000000 00:00 0 
007d0000-007d3000 r-xp 00000000 08:01 2291       /usr/lib/xulrunner-1.9.2.18/libxpcom.so
007d3000-007d4000 r--p 00002000 08:01 2291       /usr/lib/xulrunner-1.9.2.18/libxpcom.so
007d4000-007d5000 rw-p 00003000 08:01 2291       /usr/lib/xulrunner-1.9.2.18/libxpcom.so
007d7000-007d8000 r-xp 00000000 00:00 0          [vdso]
007d8000-0084f000 r-xp 00000000 08:01 1814       /usr/lib/libcairo.so.2.10800.10
0084f000-00851000 r--p 00076000 08:01 1814       /usr/lib/libcairo.so.2.10800.10
00851000-00852000 rw-p 00078000 08:01 1814       /usr/lib/libcairo.so.2.10800.10
00852000-00862000 r-xp 00000000 08:01 1994545    /lib/tls/i686/cmov/libresolv-2.11.1.so
00862000-00863000 r--p 00010000 08:01 1994545    /lib/tls/i686/cmov/libresolv-2.11.1.so
00863000-00864000 rw-p 00011000 08:01 1994545    /lib/tls/i686/cmov/libresolv-2.11.1.so
00864000-00866000 rw-p 00000000 00:00 0 
00866000-0086a000 r-xp 00000000 08:01 141        /usr/lib/libXtst.so.6.1.0
0086a000-0086b000 r--p 00003000 08:01 141        /usr/lib/libXtst.so.6.1.0
0086b000-0086c000 rw-p 00004000 08:01 141        /usr/lib/libXtst.so.6.1.0
0086c000-00906000 r-xp 00000000 08:01 86667      /usr/lib/libgio-2.0.so.0.2400.1
00906000-00907000 ---p 0009a000 08:01 86667      /usr/lib/libgio-2.0.so.0.2400.1
00907000-00908000 r--p 0009a000 08:01 86667      /usr/lib/libgio-2.0.so.0.2400.1
00908000-00909000 rw-p 0009b000 08:01 86667      /usr/lib/libgio-2.0.so.0.2400.1
00909000-0090a000 rw-p 00000000 00:00 0 
0090a000-0091e000 r-xp 00000000 08:01 2766       /usr/lib/libdirect-1.2.so.0.8.0
0091e000-0091f000 r--p 00013000 08:01 2766       /usr/lib/libdirect-1.2.so.0.8.0
0091f000-00920000 rw-p 00014000 08:01 2766       /usr/lib/libdirect-1.2.so.0.8.0
00920000-00943000 r-xp 00000000 08:01 1115       /lib/libpng12.so.0.42.0
00943000-00944000 r--p 00022000 08:01 1115       /lib/libpng12.so.0.42.0
00944000-00945000 rw-p 00023000 08:01 1115       /lib/libpng12.so.0.42.0
00945000-00952000 r-xp 00000000 08:01 1752       /usr/lib/libtdb.so.1.2.0
00952000-00953000 r--p 0000c000 08:01 1752       /usr/lib/libtdb.so.1.2.0
00953000-00954000 rw-p 0000d000 08:01 1752       /usr/lib/libtdb.so.1.2.0
00957000-00959000 r-xp 00000000 08:01 2154       /usr/lib/libXcomposite.so.1.0.0
00959000-0095a000 r--p 00001000 08:01 2154       /usr/lib/libXcomposite.so.1.0.0
0095a000-0095b000 rw-p 00002000 08:01 2154       /usr/lib/libXcomposite.so.1.0.0
0095b000-009cc000 r-xp 00000000 08:01 1777       /usr/lib/libfreetype.so.6.3.22
009cc000-009d0000 r--p 00070000 08:01 1777       /usr/lib/libfreetype.so.6.3.22
009d0000-009d1000 rw-p 00074000 08:01 1777       /usr/lib/libfreetype.so.6.3.22
009d1000-009ea000 r-xp 00000000 08:01 625        /lib/libselinux.so.1
009ea000-009eb000 r--p 00018000 08:01 625        /lib/libselinux.so.1
009eb000-009ec000 rw-p 00019000 08:01 625        /lib/libselinux.so.1
009ec000-009f6000 r-xp 00000000 08:01 589        /lib/libudev.so.0.6.1
009f6000-009f7000 r--p 00009000 08:01 589        /lib/libudev.so.0.6.1
009f7000-009f8000 rw-p 0000a000 08:01 589        /lib/libudev.so.0.6.1
009f8000-009ff000 r-xp 00000000 08:01 6039761    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
009ff000-00a00000 r--p 00006000 08:01 6039761    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00a00000-00a01000 rw-p 00007000 08:01 6039761    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00a03000-00a05000 r-xp 00000000 08:01 1994533    /lib/tls/i686/cmov/libdl-2.11.1.so
00a05000-00a06000 r--p 00001000 08:01 1994533    /lib/tls/i686/cmov/libdl-2.11.1.so
00a06000-00a07000 rw-p 00002000 08:01 1994533    /lib/tls/i686/cmov/libdl-2.11.1.so
00a07000-00a7a000 r-xp 00000000 08:01 3322       /usr/lib/libdirectfb-1.2.so.0.8.0
00a7a000-00a7b000 ---p 00073000 08:01 3322       /usr/lib/libdirectfb-1.2.so.0.8.0
00a7b000-00a7c000 r--p 00073000 08:01 3322       /usr/lib/libdirectfb-1.2.so.0.8.0
00a7c000-00a7d000 rw-p 00074000 08:01 3322       /usr/lib/libdirectfb-1.2.so.0.8.0
00a7d000-00a7e000 rw-p 00000000 00:00 0 
00a7e000-00aa2000 r-xp 00000000 08:01 2496       /lib/libexpat.so.1.5.2
00aa2000-00aa4000 r--p 00024000 08:01 2496       /lib/libexpat.so.1.5.2
00aa4000-00aa5000 rw-p 00026000 08:01 2496       /lib/libexpat.so.1.5.2
00aa5000-00aa7000 r-xp 00000000 08:01 3834       /usr/lib/libplds4.so
00aa7000-00aa8000 r--p 00001000 08:01 3834       /usr/lib/libplds4.so
00aa8000-00aa9000 rw-p 00002000 08:01 3834       /usr/lib/libplds4.so
00aac000-00aaf000 r-xp 00000000 08:01 5917190    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00aaf000-00ab0000 r--p 00003000 08:01 5917190    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00ab0000-00ab1000 rw-p 00004000 08:01 5917190    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/jli/libjli.so
00ab1000-00ad8000 r-xp 00000000 08:01 1162       /usr/lib/libvorbis.so.0.4.3
00ad8000-00ad9000 r--p 00026000 08:01 1162       /usr/lib/libvorbis.so.0.4.3
00ad9000-00ada000 rw-p 00027000 08:01 1162       /usr/lib/libvorbis.so.0.4.3
00ada000-00afe000 r-xp 00000000 08:01 1484331    /usr/lib/gio/modules/libgvfsdbus.so
00afe000-00aff000 r--p 00023000 08:01 1484331    /usr/lib/gio/modules/libgvfsdbus.so
00aff000-00b00000 rw-p 00024000 08:01 1484331    /usr/lib/gio/modules/libgvfsdbus.so
00b00000-00b03000 r-xp 00000000 08:01 2672       /usr/lib/libplc4.so
00b03000-00b04000 r--p 00002000 08:01 2672       /usr/lib/libplc4.so
00b04000-00b05000 rw-p 00003000 08:01 2672       /usr/lib/libplc4.so
00b07000-00b31000 r-xp 00000000 08:01 671036     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00b31000-00b32000 r--p 00029000 08:01 671036     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00b32000-00b33000 rw-p 0002a000 08:01 671036     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00b33000-00b47000 r-xp 00000000 08:01 2986       /usr/lib/libgvfscommon.so.0.0.0
00b47000-00b48000 r--p 00013000 08:01 2986       /usr/lib/libgvfscommon.so.0.0.0
00b48000-00b49000 rw-p 00014000 08:01 2986       /usr/lib/libgvfscommon.so.0.0.0
00b49000-00b4b000 r-xp 00000000 08:01 1994549    /lib/tls/i686/cmov/libutil-2.11.1.so
00b4b000-00b4c000 r--p 00001000 08:01 1994549    /lib/tls/i686/cmov/libutil-2.11.1.so
00b4c000-00b4d000 rw-p 00002000 08:01 1994549    /lib/tls/i686/cmov/libutil-2.11.1.so
00b4d000-00b54000 r-xp 00000000 08:01 5917219    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00b54000-00b55000 r--p 00006000 08:01 5917219    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00b55000-00b56000 rw-p 00007000 08:01 5917219    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00b56000-00b73000 r-xp 00000000 08:01 1350       /lib/libgcc_s.so.1
00b73000-00b74000 r--p 0001c000 08:01 1350       /lib/libgcc_s.so.1
00b74000-00b75000 rw-p 0001d000 08:01 1350       /lib/libgcc_s.so.1
00b76000-00b79000 r-xp 00000000 08:01 5518838    /tmp/swtlib-32/libswt-gtk-3557.so
00b79000-00b7a000 rw-p 00002000 08:01 5518838    /tmp/swtlib-32/libswt-gtk-3557.so
00b7a000-00b7b000 rw-p 00000000 00:00 0 
00b7b000-00bb4000 r-xp 00000000 08:01 969        /usr/lib/libibus.so.1.0.0
00bb4000-00bb5000 r--p 00039000 08:01 969        /usr/lib/libibus.so.1.0.0
00bb5000-00bb6000 rw-p 0003a000 08:01 969        /usr/lib/libibus.so.1.0.0
00bb6000-00bce000 r-xp 00000000 08:01 1181176    /usr/lib/xulrunner-1.9.1.3/libpyxpcom.so
00bce000-00bcf000 r--p 00017000 08:01 1181176    /usr/lib/xulrunner-1.9.1.3/libpyxpcom.so
00bcf000-00bd0000 rw-p 00018000 08:01 1181176    /usr/lib/xulrunner-1.9.1.3/libpyxpcom.so
00bd0000-00bd7000 r-xp 00000000 08:01 3557       /usr/lib/libstartup-notification-1.so.0.0.0
00bd7000-00bd8000 r--p 00006000 08:01 3557       /usr/lib/libstartup-notification-1.so.0.0.0
00bd8000-00bd9000 rw-p 00007000 08:01 3557       /usr/lib/libstartup-notification-1.so.0.0.0
00bd9000-00bdb000 r-xp 00000000 08:01 3553       /usr/lib/libxcb-aux.so.0.0.0
00bdb000-00bdc000 r--p 00001000 08:01 3553       /usr/lib/libxcb-aux.so.0.0.0
00bdc000-00bdd000 rw-p 00002000 08:01 3553       /usr/lib/libxcb-aux.so.0.0.0
00bdd000-00bdf000 r-xp 00000000 08:01 3555       /usr/lib/libxcb-event.so.1.0.0
00bdf000-00be0000 r--p 00001000 08:01 3555       /usr/lib/libxcb-event.so.1.0.0
00be0000-00be1000 rw-p 00002000 08:01 3555       /usr/lib/libxcb-event.so.1.0.0
00be1000-00bfc000 r-xp 00000000 08:01 283        /lib/ld-2.11.1.so
00bfc000-00bfd000 r--p 0001a000 08:01 283        /lib/ld-2.11.1.so
00bfd000-00bfe000 rw-p 0001b000 08:01 283        /lib/ld-2.11.1.so
00bfe000-012c3000 r-xp 00000000 08:01 6039763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
012c3000-012c4000 ---p 006c5000 08:01 6039763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
012c4000-01309000 r--p 006c5000 08:01 6039763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
01309000-01318000 rw-p 0070a000 08:01 6039763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/server/libjvm.so
01318000-01737000 rw-p 00000000 00:00 0 
01737000-017ff000 r-xp 00000000 08:01 86658      /lib/libglib-2.0.so.0.2400.1
017ff000-01800000 r--p 000c7000 08:01 86658      /lib/libglib-2.0.so.0.2400.1
01800000-01801000 rw-p 000c8000 08:01 86658      /lib/libglib-2.0.so.0.2400.1
01801000-01831000 r-xp 00000000 08:01 86905      /usr/lib/libssl3.so
01831000-01833000 r--p 0002f000 08:01 86905      /usr/lib/libssl3.so
01833000-01834000 rw-p 00031000 08:01 86905      /usr/lib/libssl3.so
01834000-01883000 r-xp 00000000 08:01 3565       /usr/lib/libXt.so.6.0.0
01883000-01884000 r--p 0004e000 08:01 3565       /usr/lib/libXt.so.6.0.0
01884000-01887000 rw-p 0004f000 08:01 3565       /usr/lib/libXt.so.6.0.0
01887000-0188e000 r-xp 00000000 08:01 57         /usr/lib/libSM.so.6.0.1
0188e000-0188f000 r--p 00006000 08:01 57         /usr/lib/libSM.so.6.0.1
0188f000-01890000 rw-p 00007000 08:01 57         /usr/lib/libSM.so.6.0.1
01890000-01893000 r-xp 00000000 08:01 2789       /usr/lib/libxcb-atom.so.1.0.0
01893000-01894000 r--p 00002000 08:01 2789       /usr/lib/libxcb-atom.so.1.0.0
01894000-01895000 rw-p 00003000 08:01 2789       /usr/lib/libxcb-atom.so.1.0.0
01895000-01898000 r-xp 00000000 08:01 1181177    /usr/lib/xulrunner-1.9.1.3/libxpcom.so
01898000-01899000 r--p 00002000 08:01 1181177    /usr/lib/xulrunner-1.9.1.3/libxpcom.so
01899000-0189a000 rw-p 00003000 08:01 1181177    /usr/lib/xulrunner-1.9.1.3/libxpcom.so
0189a000-018ae000 r-xp 00000000 08:01 5518842    /tmp/swtlib-32/libswt-xulrunner-gtk-3557.so
018ae000-018b0000 rw-p 00014000 08:01 5518842    /tmp/swtlib-32/libswt-xulrunner-gtk-3557.so
018b0000-018b2000 r-xp 00000000 08:01 591396     /usr/lib/gconv/UTF-16.so
018b2000-018b3000 r--p 00001000 08:01 591396     /usr/lib/gconv/UTF-16.so
018b3000-018b4000 rw-p 00002000 08:01 591396     /usr/lib/gconv/UTF-16.so
0194c000-01983000 r-xp 00000000 08:01 1316       /lib/libdbus-1.so.3.4.0
01983000-01984000 r--p 00036000 08:01 1316       /lib/libdbus-1.so.3.4.0
01984000-01985000 rw-p 00037000 08:01 1316       /lib/libdbus-1.so.3.4.0
01985000-01b7f000 r-xp 00000000 08:01 797        /usr/lib/libpython2.6.so.1.0
01b7f000-01b80000 r--p 001f9000 08:01 797        /usr/lib/libpython2.6.so.1.0
01b80000-01bcf000 rw-p 001fa000 08:01 797        /usr/lib/libpython2.6.so.1.0
01bcf000-01bd9000 rw-p 00000000 00:00 0 
01bd9000-01c9a000 r-xp 00000000 08:01 1181174    /usr/lib/xulrunner-1.9.1.3/libmozjs.so
01c9a000-01c9c000 r--p 000c1000 08:01 1181174    /usr/lib/xulrunner-1.9.1.3/libmozjs.so
01c9c000-01ca0000 rw-p 000c3000 08:01 1181174    /usr/lib/xulrunner-1.9.1.3/libmozjs.so
01cf2000-01d07000 r-xp 00000000 08:01 86904      /usr/lib/libnssutil3.so
01d07000-01d0a000 r--p 00014000 08:01 86904      /usr/lib/libnssutil3.so
01d0a000-01d0b000 rw-p 00017000 08:01 86904      /usr/lib/libnssutil3.so
01d0b000-01e43000 r-xp 00000000 08:01 669517     /lib/i686/cmov/libcrypto.so.0.9.8
01e43000-01e4b000 r--p 00137000 08:01 669517     /lib/i686/cmov/libcrypto.so.0.9.8
01e4b000-01e59000 rw-p 0013f000 08:01 669517     /lib/i686/cmov/libcrypto.so.0.9.8
01e59000-01e5d000 rw-p 00000000 00:00 0 
02328000-02359000 r-xp 00000000 08:01 1095       /usr/lib/libnspr4.so
02359000-0235a000 r--p 00030000 08:01 1095       /usr/lib/libnspr4.so
0235a000-0235b000 rw-p 00031000 08:01 1095       /usr/lib/libnspr4.so
0235b000-0235d000 rw-p 00000000 00:00 0 
02807000-02848000 r-xp 00000000 08:01 1875       /usr/lib/libhunspell-1.2.so.0.0.0
02848000-02849000 r--p 00040000 08:01 1875       /usr/lib/libhunspell-1.2.so.0.0.0
02849000-0284d000 rw-p 00041000 08:01 1875       /usr/lib/libhunspell-1.2.so.0.0.0
02ae0000-02b24000 r-xp 00000000 08:01 669659     /lib/i686/cmov/libssl.so.0.9.8
02b24000-02b25000 r--p 00044000 08:01 669659     /lib/i686/cmov/libssl.so.0.9.8
02b25000-02b28000 rw-p 00045000 08:01 669659     /lib/i686/cmov/libssl.so.0.9.8
02b94000-02ca3000 r-xp 00000000 08:01 86906      /usr/lib/libnss3.so
02ca3000-02ca6000 r--p 0010e000 08:01 86906      /usr/lib/libnss3.so
02ca6000-02ca8000 rw-p 00111000 08:01 86906      /usr/lib/libnss3.so
0315f000-03174000 r-xp 00000000 08:01 50         /usr/lib/libICE.so.6.3.0
03174000-03175000 r--p 00014000 08:01 50         /usr/lib/libICE.so.6.3.0
03175000-03176000 rw-p 00015000 08:01 50         /usr/lib/libICE.so.6.3.0
03176000-03178000 rw-p 00000000 00:00 0 
03178000-03d07000 r-xp 00000000 08:01 1181178    /usr/lib/xulrunner-1.9.1.3/libxul.so
03d07000-03dda000 r--p 00b8f000 08:01 1181178    /usr/lib/xulrunner-1.9.1.3/libxul.so
03dda000-03e00000 rw-p 00c62000 08:01 1181178    /usr/lib/xulrunner-1.9.1.3/libxul.so
03e00000-03e11000 rw-p 00000000 00:00 0 
04f71000-04f93000 r-xp 00000000 08:01 2778       /usr/lib/libsmime3.so
04f93000-04f94000 ---p 00022000 08:01 2778       /usr/lib/libsmime3.so
04f94000-04f96000 r--p 00022000 08:01 2778       /usr/lib/libsmime3.so
04f96000-04f97000 rw-p 00024000 08:01 2778       /usr/lib/libsmime3.so
05033000-05039000 r-xp 00000000 08:01 789193     /usr/lib/xulrunner-1.9.2.18/components/libdbusservice.so
05039000-0503a000 r--p 00006000 08:01 789193     /usr/lib/xulrunner-1.9.2.18/components/libdbusservice.so
0503a000-0503b000 rw-p 00007000 08:01 789193     /usr/lib/xulrunner-1.9.2.18/components/libdbusservice.so
0637f000-06442000 r-xp 00000000 08:01 658        /usr/lib/libasound.so.2.0.0
06442000-06446000 r--p 000c2000 08:01 658        /usr/lib/libasound.so.2.0.0
06446000-06447000 rw-p 000c6000 08:01 658        /usr/lib/libasound.so.2.0.0
06640000-066c0000 r-xp 00000000 08:01 647        /usr/lib/libsqlite3.so.0.8.6
066c0000-066c1000 r--p 0007f000 08:01 647        /usr/lib/libsqlite3.so.0.8.6
066c1000-066c2000 rw-p 00080000 08:01 647        /usr/lib/libsqlite3.so.0.8.6
066c2000-066c3000 rw-p 00000000 00:00 0 
06a08000-0771f000 r-xp 00000000 08:01 2292       /usr/lib/xulrunner-1.9.2.18/libxul.so
0771f000-077ff000 r--p 00d16000 08:01 2292       /usr/lib/xulrunner-1.9.2.18/libxul.so
077ff000-0780c000 rw-p 00df6000 08:01 2292       /usr/lib/xulrunner-1.9.2.18/libxul.so
0780c000-07820000 rw-p 00000000 00:00 0 
08048000-08051000 r-xp 00000000 08:01 6300281    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08051000-08052000 r--p 00008000 08:01 6300281    /usr/lib/jvm/java-6-openjdk/jre/bin/java
08052000-08053000 rw-p 00009000 08:01 6300281    /usr/lib/jvm/java-6-openjdk/jre/bin/java
0820f000-08212000 r-xp 00000000 08:01 946        /lib/libuuid.so.1.3.0
08212000-08213000 r--p 00002000 08:01 946        /lib/libuuid.so.1.3.0
08213000-08214000 rw-p 00003000 08:01 946        /lib/libuuid.so.1.3.0
08920000-08a09000 r-xp 00000000 08:01 2974       /usr/lib/libstdc++.so.6.0.13
08a09000-08a0a000 ---p 000e9000 08:01 2974       /usr/lib/libstdc++.so.6.0.13
08a0a000-08a0e000 r--p 000e9000 08:01 2974       /usr/lib/libstdc++.so.6.0.13
08a0e000-08a0f000 rw-p 000ed000 08:01 2974       /usr/lib/libstdc++.so.6.0.13
08a0f000-08a16000 rw-p 00000000 00:00 0 
08dd2000-0919f000 r-xp 00000000 08:01 1503       /usr/lib/libgtk-x11-2.0.so.0.2000.1
0919f000-091a3000 r--p 003cd000 08:01 1503       /usr/lib/libgtk-x11-2.0.so.0.2000.1
091a3000-091a5000 rw-p 003d1000 08:01 1503       /usr/lib/libgtk-x11-2.0.so.0.2000.1
091a5000-091a7000 rw-p 00000000 00:00 0 
091c9000-091e6000 r-xp 00000000 08:01 85         /usr/lib/libdbus-glib-1.so.2.1.0
091e6000-091e7000 r--p 0001c000 08:01 85         /usr/lib/libdbus-glib-1.so.2.1.0
091e7000-091e8000 rw-p 0001d000 08:01 85         /usr/lib/libdbus-glib-1.so.2.1.0
09a67000-09bb3000 r-xp 00000000 08:01 2290       /usr/lib/xulrunner-1.9.2.18/libmozjs.so
09bb3000-09bb5000 r--p 0014b000 08:01 2290       /usr/lib/xulrunner-1.9.2.18/libmozjs.so
09bb5000-09bba000 rw-p 0014d000 08:01 2290       /usr/lib/xulrunner-1.9.2.18/libmozjs.so
09bba000-09bbb000 rw-p 00000000 00:00 0 
09eda000-0a644000 rw-p 00000000 00:00 0          [heap]
86e00000-86e49000 rw-p 00000000 00:00 0 
86e49000-86f00000 ---p 00000000 00:00 0 
86ffd000-86ffe000 ---p 00000000 00:00 0 
86ffe000-877fe000 rw-p 00000000 00:00 0 
877fe000-877ff000 ---p 00000000 00:00 0 
877ff000-87fff000 rw-p 00000000 00:00 0 
87fff000-88000000 ---p 00000000 00:00 0 
88000000-88800000 rw-p 00000000 00:00 0 
88800000-88900000 rw-p 00000000 00:00 0 
889fd000-889fe000 ---p 00000000 00:00 0 
889fe000-891fe000 rw-p 00000000 00:00 0 
891fe000-891ff000 ---p 00000000 00:00 0 
891ff000-899ff000 rw-p 00000000 00:00 0 
899ff000-89a00000 ---p 00000000 00:00 0 
89a00000-8a200000 rw-p 00000000 00:00 0 
8a200000-8a2fb000 rw-p 00000000 00:00 0 
8a2fb000-8a300000 ---p 00000000 00:00 0 
8a35c000-8a3af000 r--p 00000000 08:01 658316     /usr/lib/xulrunner-1.9.2.18/chrome/en-US.jar
8a3af000-8a3b2000 ---p 00000000 00:00 0 
8a3b2000-8a400000 rw-p 00000000 00:00 0 
8a400000-8a600000 rw-p 00000000 00:00 0 
8a600000-8a6ff000 rw-p 00000000 00:00 0 
8a6ff000-8a700000 ---p 00000000 00:00 0 
8a700000-8a7f5000 rw-p 00000000 00:00 0 
8a7f5000-8a800000 ---p 00000000 00:00 0 
8a800000-8a8f1000 rw-p 00000000 00:00 0 
8a8f1000-8a900000 ---p 00000000 00:00 0 
8a94f000-8a9af000 rw-s 00000000 00:04 786445     /SYSV00000000 (deleted)
8a9af000-8a9b2000 ---p 00000000 00:00 0 
8a9b2000-8aa00000 rw-p 00000000 00:00 0 
8aa00000-8aaff000 rw-p 00000000 00:00 0 
8aaff000-8ab00000 ---p 00000000 00:00 0 
8ab47000-8ab4e000 r--s 00000000 08:01 591202     /usr/lib/gconv/gconv-modules.cache
8ab4e000-8ab4f000 rw-p 00000000 00:00 0 
8ab4f000-8abaf000 rw-s 00000000 00:04 720907     /SYSV00000000 (deleted)
8abaf000-8abb2000 ---p 00000000 00:00 0 
8abb2000-8ac00000 rw-p 00000000 00:00 0 
8ac00000-8ad00000 rw-p 00000000 00:00 0 
8ad05000-8ad06000 rw-p 00000000 00:00 0 
8ad06000-8ad08000 r--s 00002000 08:01 5381769    /home/jug/Desktop/Kettle/data-integration/plugins/jobentries/DummyJob/dummyjob.jar
8ad08000-8ad0e000 r--s 00051000 08:01 5381779    /home/jug/Desktop/Kettle/data-integration/plugins/steps/S3CsvInput/jets3t-0.7.0.jar
8ad0e000-8ad10000 r--s 0000a000 08:01 5381782    /home/jug/Desktop/Kettle/data-integration/plugins/steps/S3CsvInput/s3csvinput.jar
8ad10000-8ad24000 r--p 00000000 08:01 659050     /usr/share/fonts/type1/gsfonts/n019003l.pfb
8ad24000-8ad79000 r--s 00384000 08:01 5249333    /home/jug/Desktop/Kettle/data-integration/libext/odfdom.jar
8ad79000-8ad7b000 r--s 00013000 08:01 5249412    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
8ad7b000-8ae13000 r--p 00000000 08:01 676743     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
8ae13000-8af00000 r--p 00000000 08:01 918127     /usr/lib/locale/en_IN/LC_COLLATE
8af00000-8affb000 rw-p 00000000 00:00 0 
8affb000-8b000000 ---p 00000000 00:00 0 
8b000000-8b0f6000 rw-p 00000000 00:00 0 
8b0f6000-8b100000 ---p 00000000 00:00 0 
8b100000-8b1fd000 rw-p 00000000 00:00 0 
8b1fd000-8b200000 ---p 00000000 00:00 0 
8b200000-8b2fa000 rw-p 00000000 00:00 0 
8b2fa000-8b300000 ---p 00000000 00:00 0 
8b300000-8b301000 r--s 00003000 08:01 5381776    /home/jug/Desktop/Kettle/data-integration/plugins/steps/DummyPlugin/dummy.jar
8b301000-8b303000 r--s 00007000 08:01 5381786    /home/jug/Desktop/Kettle/data-integration/plugins/steps/ShapeFileReader3/shapefilereader3.jar
8b303000-8b305000 r--s 00001000 08:01 5381788    /home/jug/Desktop/Kettle/data-integration/plugins/versioncheck/kettle-version-checker-0.2.0.jar
8b305000-8b307000 r--s 00003000 08:01 5381790    /home/jug/Desktop/Kettle/data-integration/plugins/versioncheck/lib/pentaho-versionchecker.jar
8b307000-8b308000 r--s 00002000 08:01 5381765    /home/jug/Desktop/Kettle/data-integration/plugins/hour-partitioner.jar
8b308000-8b31a000 r--p 00000000 08:01 659053     /usr/share/fonts/type1/gsfonts/n019004l.pfb
8b31a000-8b31d000 rw-s 00000000 00:04 753676     /SYSV00000000 (deleted)
8b31d000-8b31e000 r--s 00000000 08:01 676750     /var/cache/fontconfig/48fef66b76e7de9c5c56a6dcc7723c04-le32d4.cache-3
8b31e000-8b31f000 r--s 00000000 08:01 676749     /var/cache/fontconfig/cb7d13eeb0521c8bf38f4717320dc78b-le32d4.cache-3
8b31f000-8b320000 r--s 00000000 08:01 676747     /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
8b320000-8b321000 r--s 00000000 08:01 676753     /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
8b321000-8b327000 r--s 00000000 08:01 670344     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
8b327000-8b32a000 r--s 00000000 08:01 670278     /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
8b32a000-8b32c000 r--s 00000000 08:01 676752     /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-le32d4.cache-3
8b32c000-8b32f000 r--s 00000000 08:01 676751     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
8b32f000-8b330000 r--s 00000000 08:01 675636     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
8b330000-8b333000 r--s 00000000 08:01 675634     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
8b333000-8b334000 r--s 00000000 08:01 675631     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
8b334000-8b335000 r--s 00000000 08:01 675627     /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
8b335000-8b336000 r--s 00000000 08:01 675551     /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
8b336000-8b33a000 r--s 00000000 08:01 669412     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
8b33a000-8b341000 r--s 00000000 08:01 706763     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
8b341000-8b34c000 r--s 00000000 08:01 672910     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
8b34c000-8b34f000 r--s 00000000 08:01 669410     /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
8b34f000-8b371000 r--s 00000000 08:01 669424     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
8b371000-8b379000 r--s 00000000 08:01 671883     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
8b379000-8b37b000 r--s 00000000 08:01 656994     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
8b37b000-8b37e000 r--s 00000000 08:01 673039     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
8b37e000-8b37f000 r--p 00000000 08:01 1349331    /usr/lib/locale/en_IN/LC_MONETARY
8b37f000-8b380000 r--p 00000000 08:01 1349319    /usr/lib/locale/en_IN/LC_MESSAGES/SYS_LC_MESSAGES
8b380000-8b381000 r--p 00000000 08:01 1049074    /usr/lib/locale/en_IN/LC_PAPER
8b381000-8b382000 r--p 00000000 08:01 1349320    /usr/lib/locale/en_IN/LC_NAME
8b382000-8b383000 r--p 00000000 08:01 1349332    /usr/lib/locale/en_IN/LC_ADDRESS
8b383000-8b384000 r--p 00000000 08:01 1349333    /usr/lib/locale/en_IN/LC_TELEPHONE
8b384000-8b385000 r--p 00000000 08:01 1049078    /usr/lib/locale/en_IN/LC_MEASUREMENT
8b385000-8b386000 r--p 00000000 08:01 1349334    /usr/lib/locale/en_IN/LC_IDENTIFICATION
8b386000-8b3aa000 r--s 00192000 08:01 5249360    /home/jug/Desktop/Kettle/data-integration/libext/rules/drools-core-5.0.1.jar
8b3aa000-8b3b4000 r--s 0008b000 08:01 5249361    /home/jug/Desktop/Kettle/data-integration/libext/rules/mvel2-2.0.10.jar
8b3b4000-8b3bb000 r--s 00019000 08:01 5249358    /home/jug/Desktop/Kettle/data-integration/libext/rules/drools-api-5.0.1.jar
8b3bb000-8b3be000 r--s 0001a000 08:01 5249356    /home/jug/Desktop/Kettle/data-integration/libext/rules/antlr-runtime-3.1.1.jar
8b3be000-8b3d1000 r--s 00108000 08:01 5249359    /home/jug/Desktop/Kettle/data-integration/libext/rules/drools-compiler-5.0.1.jar
8b3d1000-8b3fa000 r--s 00402000 08:01 5249357    /home/jug/Desktop/Kettle/data-integration/libext/rules/core-3.4.2.v_883_R34x.jar
8b3fa000-8b400000 r--s 000fc000 08:01 5249419    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
8b400000-8b4ff000 rw-p 00000000 00:00 0 
8b4ff000-8b500000 ---p 00000000 00:00 0 
8b500000-8b501000 r--s 00000000 08:01 670300     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
8b501000-8b505000 r--s 00048000 08:01 5381709    /home/jug/Desktop/Kettle/data-integration/libext/salesforce/salesforce20.0.jar
8b505000-8b519000 r--s 00173000 08:01 5381705    /home/jug/Desktop/Kettle/data-integration/libext/salesforce/axis.jar
8b519000-8b51b000 r--s 00006000 08:01 5381707    /home/jug/Desktop/Kettle/data-integration/libext/salesforce/jaxrpc.jar
8b51b000-8b51e000 r--s 0000f000 08:01 5381706    /home/jug/Desktop/Kettle/data-integration/libext/salesforce/commons-discovery-0.2.jar
8b51e000-8b522000 r--s 00016000 08:01 5381731    /home/jug/Desktop/Kettle/data-integration/libswt/commands.jar
8b522000-8b535000 r--s 000db000 08:01 5381733    /home/jug/Desktop/Kettle/data-integration/libswt/jface.jar
8b535000-8b537000 r--s 00010000 08:01 5381749    /home/jug/Desktop/Kettle/data-integration/libswt/runtime.jar
8b537000-8b53f000 r--s 00028000 08:01 5249263    /home/jug/Desktop/Kettle/data-integration/libext/feeds/xml-apis.jar
8b53f000-8b541000 r--s 00004000 08:01 5249259    /home/jug/Desktop/Kettle/data-integration/libext/feeds/georss-rome-0.9.8.jar
8b541000-8b544000 r--s 00023000 08:01 5249260    /home/jug/Desktop/Kettle/data-integration/libext/feeds/jdom.jar
8b544000-8b548000 r--s 00032000 08:01 5249262    /home/jug/Desktop/Kettle/data-integration/libext/feeds/rome-1.0.jar
8b548000-8b54a000 r--s 00018000 08:01 5249261    /home/jug/Desktop/Kettle/data-integration/libext/feeds/nekohtml.jar
8b54a000-8b54b000 r--s 0000b000 08:01 5249258    /home/jug/Desktop/Kettle/data-integration/libext/feeds/feed4j.jar
8b54b000-8b558000 r--s 000fa000 08:01 5249311    /home/jug/Desktop/Kettle/data-integration/libext/jfree/jfreechart-1.0.1.jar
8b558000-8b55e000 r--s 00046000 08:01 5249310    /home/jug/Desktop/Kettle/data-integration/libext/jfree/jcommon-1.0.14.jar
8b55e000-8b56c000 r--s 000ee000 08:01 5381727    /home/jug/Desktop/Kettle/data-integration/libext/webservices/xalan-2.4.1.jar
8b56c000-8b572000 r--s 0007a000 08:01 5381726    /home/jug/Desktop/Kettle/data-integration/libext/webservices/wstx-asl-3.2.9.jar
8b572000-8b577000 r--s 00020000 08:01 5381725    /home/jug/Desktop/Kettle/data-integration/libext/webservices/wsdl4j.jar
8b577000-8b579000 r--s 00005000 08:01 5381723    /home/jug/Desktop/Kettle/data-integration/libext/webservices/jsr173_api.jar
8b579000-8b57c000 r--s 00028000 08:01 5381719    /home/jug/Desktop/Kettle/data-integration/libext/web/jetty-util-6.1.21.jar
8b57c000-8b582000 r--s 00026000 08:01 5249348    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-xul-core-3.2.1.jar
8b582000-8b58e000 r--s 00086000 08:01 5249351    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/sqleonardo.jar
8b58e000-8b593000 r--s 0003a000 08:01 5249349    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-xul-swt-3.2.1.jar
8b593000-8b594000 r--s 00001000 08:01 5249345    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-hdfs-vfs-1.0.0.jar
8b594000-8b595000 r--s 00002000 08:01 5249346    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-s3-vfs-1.0.1.jar
8b595000-8b59b000 r--s 00060000 08:01 5249338    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/jets3t-0.7.4.jar
8b59b000-8b59c000 r--s 0000b000 08:01 5249344    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-formula-editor-0.0.1.jar
8b59c000-8b59e000 r--s 00001000 08:01 5249350    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/sqleonardo-swt-wrapper.jar
8b59e000-8b5ad000 r--s 00060000 08:01 5249341    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/libformula-1.2.1.jar
8b5ad000-8b5af000 r--s 0000d000 08:01 5249347    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-vfs-browser-2.0.2.jar
8b5af000-8b5b8000 r--s 00067000 08:01 5249342    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/olap4j-0.9.8.340.jar
8b5b8000-8b5c1000 r--s 00046000 08:01 5249339    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/kettle-vfs-20100924.jar
8b5c1000-8b5c4000 r--s 0001d000 08:01 5249340    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/libbase-1.2.1.jar
8b5c4000-8b5c6000 r--s 00009000 08:01 5249343    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/pentaho-database-4.0.5.jar
8b5c6000-8b5eb000 r--s 0026c000 08:01 5249337    /home/jug/Desktop/Kettle/data-integration/libext/pentaho/hadoop-core-0.20.2.jar
8b5eb000-8b5ed000 r--s 00015000 08:01 5249329    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/eigenbase-xom-1.3.0.13768.jar
8b5ed000-8b5ef000 r--s 00002000 08:01 5249327    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/eigenbase-properties-1.1.0.10924.jar
8b5ef000-8b5f1000 r--s 00003000 08:01 5249332    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/saxon8-xom.jar
8b5f1000-8b5f3000 r--s 0000d000 08:01 5249328    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/eigenbase-resgen-1.3.0.13768.jar
8b5f3000-8b61d000 r--s 00288000 08:01 5249331    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/mondrian-3.2.1.13885.jar
8b61d000-8b620000 r--s 00038000 08:01 5249330    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/javacup-10k.jar
8b620000-8b625000 r--s 00026000 08:01 5249324    /home/jug/Desktop/Kettle/data-integration/libext/mondrian/commons-math-1.1.jar
8b625000-8b62b000 r--s 00068000 08:01 5249302    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/postgresql-8.3-603.jdbc3.jar
8b62b000-8b65c000 r--s 003eb000 08:01 5249294    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/jt400.jar
8b65c000-8b65f000 r--s 0001f000 08:01 5249298    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/monetdb-1.7-jdbc.jar
8b65f000-8b664000 r--s 00032000 08:01 5249297    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/LucidDbClient-minimal.jar
8b664000-8b686000 r--s 0020a000 08:01 5249284    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/derby.jar
8b686000-8b68b000 r--s 00038000 08:01 5249307    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/vertica_3.5_jdk_5.jar
8b68b000-8b690000 r--s 0006c000 08:01 5249299    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/mysql-connector-java-3.1.14-bin.jar
8b690000-8b693000 r--s 00047000 08:01 5249295    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/jtds-1.2.5.jar
8b693000-8b696000 r--s 00025000 08:01 5249306    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/unijdbc.jar
8b696000-8b697000 r--s 00000000 08:01 5249283    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/db2jcc_license_cu.jar
8b697000-8b6a7000 r--s 00169000 08:01 5249300    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/ojdbc14.jar
8b6a7000-8b6aa000 r--s 00012000 08:01 5249291    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/infobright-core-3.3.jar
8b6aa000-8b6b7000 r--s 000fa000 08:01 5249282    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/db2jcc.jar
8b6b7000-8b6bb000 r--s 00045000 08:01 5249290    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/iijdbc.jar
8b6bb000-8b6bf000 r--s 0002e000 08:01 5249292    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/interclient.jar
8b6bf000-8b6c4000 r--s 000a2000 08:01 5249289    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/ifxjdbc.jar
8b6c4000-8b6c6000 r--s 000e3000 08:01 5249303    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/rdbthin.jar
8b6c6000-8b6c7000 r--s 0000c000 08:01 5249287    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/hive-jdbc-0.5.0-pentaho-1.0.0.jar
8b6c7000-8b6ca000 r--s 00052000 08:01 5249281    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/asjava.zip
8b6ca000-8b6cf000 r--s 0006e000 08:01 5249285    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/derbyclient.jar
8b6cf000-8b6d6000 r--s 0005c000 08:01 5249304    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/sapdbc.jar
8b6d6000-8b6df000 r--s 0010c000 08:01 5249286    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/h2.jar
8b6df000-8b6e2000 r--s 000c7000 08:01 5249305    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/sqlitejdbc-v037-nested.jar
8b6e2000-8b6ec000 r--s 00096000 08:01 5249293    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/jaybird-full-2.1.0.jar
8b6ec000-8b6ee000 r--s 00015000 08:01 5249308    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/xdbjdbc.jar
8b6ee000-8b6f5000 r--s 00095000 08:01 5249288    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/hsqldb.jar
8b6f5000-8b6f9000 r--s 00033000 08:01 5249296    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/kingbasejdbc.jar
8b6f9000-8b700000 r--s 0018b000 08:01 5249301    /home/jug/Desktop/Kettle/data-integration/libext/JDBC/orai18n.jar
8b700000-8b7fc000 rw-p 00000000 00:00 0 
8b7fc000-8b800000 ---p 00000000 00:00 0 
8b800000-8b802000 r--s 00015000 08:01 5381732    /home/jug/Desktop/Kettle/data-integration/libswt/common.jar
8b802000-8b806000 r--s 00026000 08:01 5249271    /home/jug/Desktop/Kettle/data-integration/libext/hive/libthrift.jar
8b806000-8b829000 r--s 00255000 08:01 5249266    /home/jug/Desktop/Kettle/data-integration/libext/hive/hadoop-core-0.20.0.jar
8b829000-8b84b000 r--s 001c8000 08:01 5249267    /home/jug/Desktop/Kettle/data-integration/libext/hive/hive-exec-0.5.0-pentaho-1.0.0.jar
8b84b000-8b854000 r--s 00074000 08:01 5249268    /home/jug/Desktop/Kettle/data-integration/libext/hive/hive-metastore-0.5.0-pentaho-1.0.0.jar
8b854000-8b857000 r--s 00019000 08:01 5249270    /home/jug/Desktop/Kettle/data-integration/libext/hive/libfb303.jar
8b857000-8b85a000 r--s 00018000 08:01 5249269    /home/jug/Desktop/Kettle/data-integration/libext/hive/hive-service-0.5.0-pentaho-1.0.0.jar
8b85a000-8b85f000 r--s 00028000 08:01 5249252    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-net-1.4.1.jar
8b85f000-8b860000 r--s 0000c000 08:01 5249251    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-logging-1.1.jar
8b860000-8b862000 r--s 0000a000 08:01 5249243    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-codec-1.3.jar
8b862000-8b865000 r--s 00018000 08:01 5249249    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-io-1.4.jar
8b865000-8b867000 r--s 0000e000 08:01 5249253    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-pool-1.3.jar
8b867000-8b86c000 r--s 0002a000 08:01 5249242    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-beanutils-1.7.0.jar
8b86c000-8b86f000 r--s 0001f000 08:01 5249254    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-validator-1.3.1.jar
8b86f000-8b874000 r--s 00040000 08:01 5249248    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-httpclient-3.0.1.jar
8b874000-8b878000 r--s 0003c000 08:01 5249250    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-lang-2.4.jar
8b878000-8b87c000 r--s 00020000 08:01 5249246    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-digester-1.8.jar
8b87c000-8b87f000 r--s 00018000 08:01 5249245    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-dbcp-1.2.1.jar
8b87f000-8b88c000 r--s 0007c000 08:01 5249244    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-collections-3.1.jar
8b88c000-8b88e000 r--s 00004000 08:01 5249247    /home/jug/Desktop/Kettle/data-integration/libext/commons/commons-fileupload-1.0.jar
8b88e000-8b88f000 r--s 00008000 08:01 5249240    /home/jug/Desktop/Kettle/data-integration/libext/ascsapjco3wrp.jar
8b88f000-8b895000 r--s 00032000 08:01 5249278    /home/jug/Desktop/Kettle/data-integration/libext/jaxen-1.1.1.jar
8b895000-8b898000 r--s 00028000 08:01 5249256    /home/jug/Desktop/Kettle/data-integration/libext/edtftpj2.1.jar
8b898000-8b8a1000 r--s 000cc000 08:01 5249312    /home/jug/Desktop/Kettle/data-integration/libext/js.jar
8b8a1000-8b8f6000 r--s 00384000 08:01 5249333    /home/jug/Desktop/Kettle/data-integration/libext/odfdom.jar
8b8f6000-8b8fa000 r--s 0003a000 08:01 5249370    /home/jug/Desktop/Kettle/data-integration/libext/trilead-ssh2-build213.jar
8b8fa000-8b900000 r--s 0005f000 08:01 5249353    /home/jug/Desktop/Kettle/data-integration/libext/poi-ooxml-3.6-20091214.jar
8b900000-8b9fb000 rw-p 00000000 00:00 0 
8b9fb000-8ba00000 ---p 00000000 00:00 0 
8ba00000-8ba01000 r--p 00000000 08:01 1349329    /usr/lib/locale/en_IN/LC_NUMERIC
8ba01000-8ba1c000 r--s 0015d000 08:01 5249352    /home/jug/Desktop/Kettle/data-integration/libext/poi-3.6-20091214.jar
8ba1c000-8ba1f000 r--s 0002b000 08:01 5249313    /home/jug/Desktop/Kettle/data-integration/libext/jsch-0.1.42.jar
8ba1f000-8ba25000 r--s 00033000 08:01 5249317    /home/jug/Desktop/Kettle/data-integration/libext/junit-4.7.jar
8ba25000-8ba29000 r--s 00028000 08:01 5249364    /home/jug/Desktop/Kettle/data-integration/libext/secondstring.jar
8ba29000-8ba2e000 r--s 00048000 08:01 5249255    /home/jug/Desktop/Kettle/data-integration/libext/dom4j-1.6.1.jar
8ba2e000-8ba38000 r--s 0008d000 08:01 5249275    /home/jug/Desktop/Kettle/data-integration/libext/janino.jar
8ba38000-8ba3d000 r--s 0003c000 08:01 5249319    /home/jug/Desktop/Kettle/data-integration/libext/ldapjdk.jar
8ba3d000-8ba3e000 r--s 00004000 08:01 5249335    /home/jug/Desktop/Kettle/data-integration/libext/palo-core.jar
8ba3e000-8ba40000 r--s 00001000 08:01 5249314    /home/jug/Desktop/Kettle/data-integration/libext/jsonpath.jar
8ba40000-8babd000 r--s 0031d000 08:01 5249354    /home/jug/Desktop/Kettle/data-integration/libext/poi-ooxml-schemas-3.6-20091214.jar
8babd000-8bac3000 r--s 0005a000 08:01 5249279    /home/jug/Desktop/Kettle/data-integration/libext/jcifs-1.3.3.jar
8bac3000-8bac4000 r--s 00003000 08:01 5249276    /home/jug/Desktop/Kettle/data-integration/libext/javadbf.jar
8bac4000-8bb02000 r--s 0025b000 08:01 5249371    /home/jug/Desktop/Kettle/data-integration/libext/xbean.jar
8bb02000-8bb03000 r--s 00003000 08:01 5249315    /home/jug/Desktop/Kettle/data-integration/libext/json_simple-1.1.jar
8bb03000-8bb19000 r--s 00379000 08:01 5249362    /home/jug/Desktop/Kettle/data-integration/libext/saxon8.jar
8bb19000-8bb1a000 r--s 00001000 08:01 5249366    /home/jug/Desktop/Kettle/data-integration/libext/slf4j-jcl-1.5.8.jar
8bb1a000-8bb1f000 r--s 00061000 08:01 5249273    /home/jug/Desktop/Kettle/data-integration/libext/jackcess-1.2.1.jar
8bb1f000-8bb37000 r--s 00115000 08:01 5249372    /home/jug/Desktop/Kettle/data-integration/libext/xercesImpl-2.9.1.jar
8bb37000-8bb3b000 r--s 00026000 08:01 5249334    /home/jug/Desktop/Kettle/data-integration/libext/ognl-2.6.9.jar
8bb3b000-8bb40000 r--s 0002b000 08:01 5249369    /home/jug/Desktop/Kettle/data-integration/libext/syslog4j-0.9.34.jar
8bb40000-8bb41000 r--s 00003000 08:01 5249320    /home/jug/Desktop/Kettle/data-integration/libext/livetribe-jsr223-2.0.6.jar
8bb41000-8bb48000 r--s 00051000 08:01 5249322    /home/jug/Desktop/Kettle/data-integration/libext/mail.jar
8bb48000-8bb4e000 r--s 0006d000 08:01 5249277    /home/jug/Desktop/Kettle/data-integration/libext/javassist.jar
8bb4e000-8bb5a000 r--s 000a6000 08:01 5249318    /home/jug/Desktop/Kettle/data-integration/libext/jxl.jar
8bb5a000-8bb5c000 r--s 00008000 08:01 5249316    /home/jug/Desktop/Kettle/data-integration/libext/jug-lgpl-2.0.0.jar
8bb5c000-8bb62000 r--s 00055000 08:01 5249368    /home/jug/Desktop/Kettle/data-integration/libext/SNMP4J.jar
8bb62000-8bb64000 r--s 0000e000 08:01 5249274    /home/jug/Desktop/Kettle/data-integration/libext/jakarta-oro-2.0.8.jar
8bb64000-8bb66000 r--s 00016000 08:01 5249272    /home/jug/Desktop/Kettle/data-integration/libext/ini4j-0.5.1.jar
8bb66000-8bb67000 r--s 00005000 08:01 5249365    /home/jug/Desktop/Kettle/data-integration/libext/slf4j-api-1.5.8.jar
8bb67000-8bb69000 r--s 00003000 08:01 5249363    /home/jug/Desktop/Kettle/data-integration/libext/scannotation-1.0.2.jar
8bb69000-8bb70000 r--s 00059000 08:01 5249321    /home/jug/Desktop/Kettle/data-integration/libext/log4j-1.2.14.jar
8bb70000-8bb76000 r--s 00038000 08:01 5249367    /home/jug/Desktop/Kettle/data-integration/libext/snakeyaml-1.7.jar
8bb76000-8bb78000 r--s 00015000 08:01 5249264    /home/jug/Desktop/Kettle/data-integration/libext/ftp4che-0.7.1.jar
8bb78000-8bb7c000 r--s 0003b000 08:01 5249237    /home/jug/Desktop/Kettle/data-integration/lib/kettle-test.jar
8bb7c000-8bb7d000 r--p 00000000 08:01 1349330    /usr/lib/locale/en_IN/LC_TIME
8bb7d000-8bb7f000 r--s 0000c000 08:01 5381716    /home/jug/Desktop/Kettle/data-integration/libext/web/activation.jar
8bb7f000-8bb82000 r--s 0001e000 08:01 5381720    /home/jug/Desktop/Kettle/data-integration/libext/web/servlet-api-2.5-6.1.9.jar
8bb82000-8bb89000 r--s 0007c000 08:01 5381717    /home/jug/Desktop/Kettle/data-integration/libext/web/jetty-6.1.21.jar
8bb89000-8bb8b000 r--s 0000d000 08:01 5381718    /home/jug/Desktop/Kettle/data-integration/libext/web/jetty-plus-6.1.21.jar
8bb8b000-8bb8d000 r--s 00009000 08:01 5381721    /home/jug/Desktop/Kettle/data-integration/libext/web/simple-jndi-0.11.1.jar
8bb8d000-8bb99000 r--s 00069000 08:01 5381712    /home/jug/Desktop/Kettle/data-integration/libext/spring/spring-context-2.5.6.jar
8bb99000-8bb9f000 r--s 00040000 08:01 5381714    /home/jug/Desktop/Kettle/data-integration/libext/spring/spring-core-2.5.6.jar
8bb9f000-8bba9000 r--s 0006e000 08:01 5381711    /home/jug/Desktop/Kettle/data-integration/libext/spring/spring-beans-2.5.6.jar
8bba9000-8bbac000 r--s 00015000 08:01 5381713    /home/jug/Desktop/Kettle/data-integration/libext/spring/spring-context-support-2.5.6.jar
8bbac000-8bc35000 r--s 0069c000 08:01 5249238    /home/jug/Desktop/Kettle/data-integration/lib/kettle-ui-swt.jar
8bc35000-8bc3e000 r--s 00063000 08:01 5249234    /home/jug/Desktop/Kettle/data-integration/lib/kettle-core.jar
8bc3e000-8bc9c000 r--s 0059e000 08:01 5249236    /home/jug/Desktop/Kettle/data-integration/lib/kettle-engine.jar
8bc9c000-8bc9d000 ---p 00000000 00:00 0 
8bc9d000-8bd1d000 rw-p 00000000 00:00 0 
8bd1d000-8bd20000 ---p 00000000 00:00 0 
8bd20000-8bd6e000 rw-p 00000000 00:00 0 
8bd6e000-8bd71000 ---p 00000000 00:00 0 
8bd71000-8bdef000 rw-p 00000000 00:00 0 
8bdef000-8bdf2000 ---p 00000000 00:00 0 
8bdf2000-8be70000 rw-p 00000000 00:00 0 
8be70000-8be73000 ---p 00000000 00:00 0 
8be73000-8bec1000 rw-p 00000000 00:00 0 
8bec1000-8bf00000 r--p 00000000 08:01 918124     /usr/lib/locale/en_IN/LC_CTYPE
8bf00000-8bffa000 rw-p 00000000 00:00 0 
8bffa000-8c000000 ---p 00000000 00:00 0 
8c000000-8c001000 r--s 00004000 08:01 5381708    /home/jug/Desktop/Kettle/data-integration/libext/salesforce/saaj.jar
8c001000-8c002000 r--s 00000000 08:01 5381724    /home/jug/Desktop/Kettle/data-integration/libext/webservices/qname.jar
8c002000-8c005000 r--s 00041000 08:01 5249235    /home/jug/Desktop/Kettle/data-integration/lib/kettle-db.jar
8c005000-8c019000 r--s 00145000 08:01 5381741    /home/jug/Desktop/Kettle/data-integration/libswt/linux/x86/swt.jar
8c019000-8c01c000 r--s 0007d000 08:01 5249413    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
8c01c000-8c025000 r--s 00065000 08:01 262607     /usr/share/java/gnome-java-bridge.jar
8c025000-8c028000 ---p 00000000 00:00 0 
8c028000-8c076000 rw-p 00000000 00:00 0 
8c076000-8c079000 ---p 00000000 00:00 0 
8c079000-8c0c7000 rw-p 00000000 00:00 0 
8c0c7000-8c0c8000 ---p 00000000 00:00 0 
8c0c8000-8c148000 rw-p 00000000 00:00 0 
8c148000-8c14a000 r--s 0001d000 08:01 5249418    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
8c14a000-8c14f000 r--s 00045000 08:01 5249417    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
8c14f000-8c182000 rw-p 00000000 00:00 0 
8c182000-8c312000 r--s 038c5000 08:01 5249613    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
8c312000-8c313000 ---p 00000000 00:00 0 
8c313000-8c393000 rw-p 00000000 00:00 0 
8c393000-8c394000 ---p 00000000 00:00 0 
8c394000-8c41e000 rw-p 00000000 00:00 0 
8c41e000-8c454000 rw-p 00000000 00:00 0 
8c454000-8c464000 rw-p 00000000 00:00 0 
8c464000-8c4ff000 rw-p 00000000 00:00 0 
8c4ff000-8c509000 rw-p 00000000 00:00 0 
8c509000-8c53f000 rw-p 00000000 00:00 0 
8c53f000-8c54f000 rw-p 00000000 00:00 0 
8c54f000-8c5e9000 rw-p 00000000 00:00 0 
8c5e9000-8c63f000 rw-p 00000000 00:00 0 
8c63f000-8d960000 rw-p 00000000 00:00 0 
8d960000-94640000 rw-p 00000000 00:00 0 
94640000-96470000 rw-p 00000000 00:00 0 
96470000-a9ba0000 rw-p 00000000 00:00 0 
a9ba0000-b4640000 rw-p 00000000 00:00 0 
b4640000-b4649000 rw-p 00000000 00:00 0 
b4649000-b4700000 rw-p 00000000 00:00 0 
b4700000-b4940000 rwxp 00000000 00:00 0 
b4940000-b7700000 rw-p 00000000 00:00 0 
b7700000-b7703000 ---p 00000000 00:00 0 
b7703000-b7754000 rw-p 00000000 00:00 0 
b7754000-b7756000 r--s 00001000 08:01 5249231    /home/jug/Desktop/Kettle/data-integration/launcher/launcher.jar
b7756000-b7759000 r--s 0000f000 08:01 5249399    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b7759000-b775b000 r--s 00001000 08:01 5249231    /home/jug/Desktop/Kettle/data-integration/launcher/launcher.jar
b775b000-b7763000 rw-s 00000000 08:01 5243663    /tmp/hsperfdata_jug/2148
b7763000-b7764000 rw-p 00000000 00:00 0 
b7764000-b7765000 r--p 00000000 00:00 0 
b7765000-b7767000 rw-p 00000000 00:00 0 
bfdf0000-bfe25000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xmx512m -Djava.library.path=./../libswt/linux/x86/ -DKETTLE_HOME= -DKETTLE_REPOSITORY= -DKETTLE_USER= -DKETTLE_PASSWORD= -DKETTLE_PLUGIN_PACKAGES= -DKETTLE_LOG_SIZE_LIMIT= 
java_command: launcher/launcher.jar -lib ./../libswt/linux/x86/ 
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=jug
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/server:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:/usr/lib/jvm/java-6-openjdk/jre/../lib/i386:/usr/lib/xulrunner-1.9.2.18:
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x64a040], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x64a040], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x51c0d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x51c0d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x51c0d0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x51b780], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x51e2f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x51e2f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x51e2f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x51e2f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
```


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.98 1.55 0.72

/proc/meminfo:
MemTotal:        2964920 kB
MemFree:          446512 kB
Buffers:          271344 kB
Cached:          1497916 kB
SwapCached:            0 kB
Active:           816824 kB
Inactive:        1551024 kB
Active(anon):     631720 kB
Inactive(anon):    69528 kB
Active(file):     185104 kB
Inactive(file):  1481496 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2102856 kB
HighFree:          19220 kB
LowTotal:         862064 kB
LowFree:          427292 kB
SwapTotal:       8683092 kB
SwapFree:        8683092 kB
Dirty:               172 kB
Writeback:             0 kB
AnonPages:        598636 kB
Mapped:            88016 kB
Shmem:            102656 kB
Slab:             102168 kB
SReclaimable:      90732 kB
SUnreclaim:        11436 kB
KernelStack:        2272 kB
PageTables:         6368 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    10165552 kB
Committed_AS:    1716468 kB
VmallocTotal:     122880 kB
VmallocUsed:       36684 kB
VmallocChunk:      38596 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB


CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 23 stepping 10, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1

Memory: 4k page, physical 2964920k(446512k free), swap 8683092k(8683092k free)

vm_info: OpenJDK Server VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Feb 17 2012 07:22:18 by "buildd" with gcc 4.4.3

time: Thu May  3 20:10:26 2012
elapsed time: 7 seconds

Kindly help me to solve this issue.

---

