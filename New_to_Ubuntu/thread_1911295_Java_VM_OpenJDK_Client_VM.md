---
title: "Java VM: OpenJDK Client VM"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by zyrex on 2012-01-18
Hi,

I have this current problem when ever i use a program called aptana see the log file below:


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00000042, pid=1551, tid=3078665920
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK Client VM (19.0-b09 mixed mode, sharing linux-x86 )
# Derivative: IcedTea6 1.9.10
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.10-0ubuntu1~10.04.2
# Problematic frame:
# C  0x00000042
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x08946800):  JavaThread "main" [_thread_in_native, id=1551, stack(0xbf918000,0xbf968000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000042

Registers:
EAX=0xad79f660, EBX=0xace0ba5c, ECX=0xb47c1598, EDX=0xad7df140
ESP=0xbf962f1c, EBP=0xbf963068, ESI=0x00000005, EDI=0x00000001
EIP=0x00000042, CR2=0x00000042, EFLAGS=0x00210282

Register to memory mapping:

EAX=0xad79f660
0xad79f660 is pointing to unknown location

EBX=0xace0ba5c
0xace0ba5c: <offset 0x101aa5c> in /usr/lib/adobe-flashplugin/libflashplayer.so at 0xabdf1000

ECX=0xb47c1598
0xb47c1598 is pointing to unknown location

EDX=0xad7df140
0xad7df140 is pointing to unknown location

ESP=0xbf962f1c
0xbf962f1c is pointing into the stack for thread: 0x08946800
"main" prio=10 tid=0x08946800 nid=0x60f runnable [0xbf964000]
   java.lang.Thread.State: RUNNABLE

EBP=0xbf963068
0xbf963068 is pointing into the stack for thread: 0x08946800
"main" prio=10 tid=0x08946800 nid=0x60f runnable [0xbf964000]
   java.lang.Thread.State: RUNNABLE

ESI=0x00000005
0x00000005 is pointing to unknown location

EDI=0x00000001
0x00000001 is pointing to unknown location


Top of Stack: (sp=0xbf962f1c)
0xbf962f1c:   abe93111 ad7df140 b47c1598 00000000
0xbf962f2c:   77732f68 73616c66 61632e68 65762362
0xbf962f3c:   6f697372 2c373d6e 2c302c30 00b99f18
0xbf962f4c:   0001000b 00200000 abc0e000 bf962f88
0xbf962f5c:   abc0e000 abbf1000 bf96305b 00000003
0xbf962f6c:   00000032 ace0ba5c bf962f70 00000001
0xbf962f7c:   bf963068 c1e9f2ce 3fd6aee6 00000000
0xbf962f8c:   ac5d3ec0 ace48850 abbf1060 00000001 

Instructions: (pc=0x00000042)
0x00000032:   
[error occurred during error reporting (printing registers, top of stack, instructions near pc), id 0xb]

Stack: [0xbf918000,0xbf968000],  sp=0xbf962f1c,  free space=299k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  0x00000042
C  [libflashplayer.so+0xa8059]
C  [libcefjni.so+0xdd1c3f]
C  [libcefjni.so+0xdd1dd5]
C  [libcefjni.so+0xdb0c70]
C  [libcefjni.so+0xdb7d3d]
C  [libcefjni.so+0x345b13]
C  [libcefjni.so+0xaca4d5]
C  [libcefjni.so+0xacac8a]
C  [libcefjni.so+0x7a0349]
C  [libcefjni.so+0xaf8355]
C  [libcefjni.so+0xaf9674]
C  [libcefjni.so+0xafb294]
C  [libcefjni.so+0xafc5e9]
C  [libcefjni.so+0x99634c]
C  [libcefjni.so+0x9a70a7]
C  [libcefjni.so+0x9b0c17]
C  [libcefjni.so+0x111765d]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  cef.CEFJNI.CefDoMessageLoopWork()V
J  com.aptana.swt.webkitbrowser.CEFHelper$1.run()V
J  org.eclipse.swt.widgets.Display.timerProc(I)I
v  ~StubRoutines::call_stub
J  org.eclipse.swt.internal.gtk.OS._g_main_context_iteration(IZ)Z
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
J  org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display;)V
j  org.eclipse.ui.internal.Workbench.runUI()I+555
j  org.eclipse.ui.internal.Workbench.access$4(Lorg/eclipse/ui/internal/Workbench;)I+1
j  org.eclipse.ui.internal.Workbench$7.run()V+55
j  org.eclipse.core.databinding.observable.Realm.runWithDefault(Lorg/eclipse/core/databinding/observable/Realm;Ljava/lang/Runnable;)V+12
j  org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+18
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor;)I+2
j  com.aptana.rcp.IDEApplication.start(Lorg/eclipse/equinox/app/IApplicationContext;)Ljava/lang/Object;+137
j  org.eclipse.equinox.internal.app.EclipseAppHandle.run(Ljava/lang/Object;)Ljava/lang/Object;+135
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object;)Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object;)Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object;)Ljava/lang/Object;+149
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable;)Ljava/lang/Object;+183
v  ~StubRoutines::call_stub
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+161
j  org.eclipse.equinox.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL;)V+211
j  org.eclipse.equinox.launcher.Main.basicRun([Ljava/lang/String;)V+126
j  org.eclipse.equinox.launcher.Main.run([Ljava/lang/String;)I+4
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x089cd800 JavaThread "Worker-10" [_thread_blocked, id=1760, stack(0xb4b4b000,0xb4b9c000)]
  0xb4741400 JavaThread "com.aptana.editor.common.text.reconciler.CommonReconciler" daemon [_thread_blocked, id=1756, stack(0xb3778000,0xb37c9000)]
  0x08f64800 JavaThread "Provisioning Event Dispatcher" daemon [_thread_blocked, id=1751, stack(0xb331a000,0xb336b000)]
  0x08cf8800 JavaThread "Thread-14" daemon [_thread_blocked, id=1721, stack(0xb32c9000,0xb331a000)]
  0xb41cd400 JavaThread "com.aptana.editor.common.text.reconciler.CommonReconciler" daemon [_thread_blocked, id=1704, stack(0xb3e67000,0xb3eb8000)]
  0x08a70400 JavaThread "MultiThreadedHttpConnectionManager cleanup" daemon [_thread_blocked, id=1703, stack(0xb3634000,0xb3685000)]
  0x08c3a400 JavaThread "Input Stream Monitor" daemon [_thread_blocked, id=1664, stack(0xb336b000,0xb33bc000)]
  0x08c33800 JavaThread "Output Stream Monitor" daemon [_thread_in_native, id=1663, stack(0xb33bc000,0xb340d000)]
  0x08c35400 JavaThread "Output Stream Monitor" daemon [_thread_in_native, id=1662, stack(0xb340d000,0xb345e000)]
  0x08c31400 JavaThread "Process watcher" [_thread_blocked, id=1660, stack(0xb345e000,0xb34af000)]
  0x08c36400 JavaThread "process reaper" daemon [_thread_in_native, id=1658, stack(0xb34af000,0xb3500000)]
  0xb3a44c00 JavaThread "CommandLineArgsServer" [_thread_in_native, id=1650, stack(0xb3727000,0xb3778000)]
  0x08ab5000 JavaThread "Worker-6" [_thread_blocked, id=1646, stack(0xb386b000,0xb38bc000)]
  0x08a27800 JavaThread "Worker-2" [_thread_blocked, id=1642, stack(0xb45f4000,0xb4645000)]
  0x08b5f800 JavaThread "I/O dispatcher 2" daemon [_thread_in_native, id=1605, stack(0xb395e000,0xb39af000)]
  0x08a17000 JavaThread "I/O dispatcher 1" daemon [_thread_in_native, id=1604, stack(0xb39af000,0xb3a00000)]
  0xb3a16c00 JavaThread "Thread-8" daemon [_thread_in_native, id=1603, stack(0xb3b2a000,0xb3b7b000)]
  0x08ce2c00 JavaThread "[ThreadPool Manager] - Idle Thread" daemon [_thread_blocked, id=1602, stack(0xb3bdb000,0xb3c2c000)]
  0xb3d56400 JavaThread "Bundle File Closer" daemon [_thread_blocked, id=1601, stack(0xb3c5e000,0xb3caf000)]
  0x08c06000 JavaThread "Thread-4" daemon [_thread_blocked, id=1597, stack(0xb3caf000,0xb3d00000)]
  0x08c04000 JavaThread "Thread-3" daemon [_thread_blocked, id=1596, stack(0xb3e16000,0xb3e67000)]
  0x08acb400 JavaThread "INotify thread" daemon [_thread_in_native, id=1593, stack(0xb43af000,0xb4400000)]
  0x08ac3c00 JavaThread "Worker-1" [_thread_blocked, id=1592, stack(0xb4538000,0xb4589000)]
  0x08a9f800 JavaThread "Worker-JM" [_thread_blocked, id=1576, stack(0xb4aa9000,0xb4afa000)]
  0x08a19c00 JavaThread "[Timer] - Main Queue Handler" daemon [_thread_blocked, id=1575, stack(0xb4afa000,0xb4b4b000)]
  0x089cbc00 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=1573, stack(0xb4b9c000,0xb4bed000)]
  0xb4dcec00 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=1572, stack(0xb4bed000,0xb4c3e000)]
  0xb4d97c00 JavaThread "State Data Manager" daemon [_thread_blocked, id=1571, stack(0xb4c3e000,0xb4c8f000)]
  0x08981400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=1567, stack(0xb4f50000,0xb4fa1000)]
  0x0897f800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=1566, stack(0xb4fa1000,0xb5022000)]
  0x0897dc00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=1565, stack(0xb5022000,0xb5073000)]
  0x08977000 JavaThread "Finalizer" daemon [_thread_blocked, id=1564, stack(0xb5073000,0xb50c4000)]
  0x08975c00 JavaThread "Reference Handler" daemon [_thread_blocked, id=1563, stack(0xb50c4000,0xb5115000)]
=>0x08946800 JavaThread "main" [_thread_in_native, id=1551, stack(0xbf918000,0xbf968000)]

Other Threads:
  0x08973c00 VMThread [stack: 0xb5115000,0xb5196000] [id=1562]
  0x0898d400 WatcherThread [stack: 0xb4ecf000,0xb4f50000] [id=1568]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 18304K, used 4538K [0x63990000, 0x64d60000, 0x6e430000)
  eden space 16320K,  17% used [0x63990000, 0x63c6b078, 0x64980000)
  from space 1984K,  81% used [0x64b70000, 0x64d03930, 0x64d60000)
  to   space 1984K,   0% used [0x64980000, 0x64980000, 0x64b70000)
 tenured generation   total 40412K, used 24245K [0x6e430000, 0x70ba7000, 0x83990000)
   the space 40412K,  59% used [0x6e430000, 0x6fbdd428, 0x6fbdd600, 0x70ba7000)
 compacting perm gen  total 53760K, used 53538K [0x83990000, 0x86e10000, 0x93990000)
   the space 53760K,  99% used [0x83990000, 0x86dd89f0, 0x86dd8a00, 0x86e10000)
    ro space 10240K,  73% used [0x93990000, 0x940e8c20, 0x940e8e00, 0x94390000)
    rw space 12288K,  60% used [0x94390000, 0x94ad0fe8, 0x94ad1000, 0x94f90000)

Dynamic libraries:
00110000-00134000 r-xp 00000000 08:01 3539907    /lib/tls/i686/cmov/libm-2.11.1.so
00134000-00135000 r--p 00023000 08:01 3539907    /lib/tls/i686/cmov/libm-2.11.1.so
00135000-00136000 rw-p 00024000 08:01 3539907    /lib/tls/i686/cmov/libm-2.11.1.so
00136000-0013d000 r-xp 00000000 08:01 3539929    /lib/tls/i686/cmov/librt-2.11.1.so
0013d000-0013e000 r--p 00006000 08:01 3539929    /lib/tls/i686/cmov/librt-2.11.1.so
0013e000-0013f000 rw-p 00007000 08:01 3539929    /lib/tls/i686/cmov/librt-2.11.1.so
0013f000-00152000 r-xp 00000000 08:01 3408070    /lib/libz.so.1.2.3.3
00152000-00153000 r--p 00012000 08:01 3408070    /lib/libz.so.1.2.3.3
00153000-00154000 rw-p 00013000 08:01 3408070    /lib/libz.so.1.2.3.3
00154000-00191000 r-xp 00000000 08:01 1969345    /usr/lib/libgobject-2.0.so.0.2400.1
00191000-00192000 r--p 0003c000 08:01 1969345    /usr/lib/libgobject-2.0.so.0.2400.1
00192000-00193000 rw-p 0003d000 08:01 1969345    /usr/lib/libgobject-2.0.so.0.2400.1
00193000-00197000 r-xp 00000000 08:01 1969429    /usr/lib/libgthread-2.0.so.0.2400.1
00197000-00198000 r--p 00003000 08:01 1969429    /usr/lib/libgthread-2.0.so.0.2400.1
00198000-00199000 rw-p 00004000 08:01 1969429    /usr/lib/libgthread-2.0.so.0.2400.1
00199000-001c7000 r-xp 00000000 08:01 1969230    /usr/lib/libfontconfig.so.1.4.4
001c7000-001c8000 r--p 0002d000 08:01 1969230    /usr/lib/libfontconfig.so.1.4.4
001c8000-001c9000 rw-p 0002e000 08:01 1969230    /usr/lib/libfontconfig.so.1.4.4
001c9000-001cb000 r-xp 00000000 08:01 1968943    /usr/lib/libXcomposite.so.1.0.0
001cb000-001cc000 r--p 00001000 08:01 1968943    /usr/lib/libXcomposite.so.1.0.0
001cc000-001cd000 rw-p 00002000 08:01 1968943    /usr/lib/libXcomposite.so.1.0.0
001cd000-00244000 r-xp 00000000 08:01 1969071    /usr/lib/libcairo.so.2.10800.10
00244000-00246000 r--p 00076000 08:01 1969071    /usr/lib/libcairo.so.2.10800.10
00246000-00247000 rw-p 00078000 08:01 1969071    /usr/lib/libcairo.so.2.10800.10
00247000-0024a000 r-xp 00000000 08:01 1969941    /usr/lib/libxcb-render-util.so.0.0.0
0024a000-0024b000 r--p 00002000 08:01 1969941    /usr/lib/libxcb-render-util.so.0.0.0
0024b000-0024c000 rw-p 00003000 08:01 1969941    /usr/lib/libxcb-render-util.so.0.0.0
0024c000-0024e000 r-xp 00000000 08:01 1968938    /usr/lib/libXau.so.6.0.0
0024e000-0024f000 r--p 00001000 08:01 1968938    /usr/lib/libXau.so.6.0.0
0024f000-00250000 rw-p 00002000 08:01 1968938    /usr/lib/libXau.so.6.0.0
00250000-0025a000 r-xp 00000000 08:01 3539916    /lib/tls/i686/cmov/libnss_files-2.11.1.so
0025a000-0025b000 r--p 00009000 08:01 3539916    /lib/tls/i686/cmov/libnss_files-2.11.1.so
0025b000-0025c000 rw-p 0000a000 08:01 3539916    /lib/tls/i686/cmov/libnss_files-2.11.1.so
0025c000-00324000 r-xp 00000000 08:01 3407959    /lib/libglib-2.0.so.0.2400.1
00324000-00325000 r--p 000c7000 08:01 3407959    /lib/libglib-2.0.so.0.2400.1
00325000-00326000 rw-p 000c8000 08:01 3407959    /lib/libglib-2.0.so.0.2400.1
00326000-0033e000 r-xp 00000000 08:01 1979103    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0033e000-0033f000 r--p 00017000 08:01 1979103    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
0033f000-00340000 rw-p 00018000 08:01 1979103    /usr/lib/libgdk_pixbuf-2.0.so.0.2000.1
00340000-00364000 r-xp 00000000 08:01 3407948    /lib/libexpat.so.1.5.2
00364000-00366000 r--p 00024000 08:01 3407948    /lib/libexpat.so.1.5.2
00366000-00367000 rw-p 00026000 08:01 3407948    /lib/libexpat.so.1.5.2
00367000-0036f000 r-xp 00000000 08:01 1969242    /usr/lib/libfusion-1.2.so.0.8.0
0036f000-00370000 r--p 00007000 08:01 1969242    /usr/lib/libfusion-1.2.so.0.8.0
00370000-00371000 rw-p 00008000 08:01 1969242    /usr/lib/libfusion-1.2.so.0.8.0
00371000-00377000 r-xp 00000000 08:01 1969943    /usr/lib/libxcb-render.so.0.0.0
00377000-00378000 r--p 00005000 08:01 1969943    /usr/lib/libxcb-render.so.0.0.0
00378000-00379000 rw-p 00006000 08:01 1969943    /usr/lib/libxcb-render.so.0.0.0
00379000-00385000 r-xp 00000000 08:01 1968959    /usr/lib/libXi.so.6.1.0
00385000-00386000 r--p 0000c000 08:01 1968959    /usr/lib/libXi.so.6.1.0
00386000-00387000 rw-p 0000d000 08:01 1968959    /usr/lib/libXi.so.6.1.0
00387000-0038b000 r-xp 00000000 08:01 1968949    /usr/lib/libXdmcp.so.6.0.0
0038b000-0038c000 r--p 00003000 08:01 1968949    /usr/lib/libXdmcp.so.6.0.0
0038c000-0038d000 rw-p 00004000 08:01 1968949    /usr/lib/libXdmcp.so.6.0.0
0038d000-0038f000 r-xp 00000000 08:01 4079381    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/141/1/.cp/os/linux/x86/libunixfile_1_0_0.so
0038f000-00390000 rw-p 00001000 08:01 4079381    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/141/1/.cp/os/linux/x86/libunixfile_1_0_0.so
00390000-00397000 r-xp 00000000 08:01 2766659    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00397000-00398000 r--p 00006000 08:01 2766659    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00398000-00399000 rw-p 00007000 08:01 2766659    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libzip.so
00399000-003bc000 r-xp 00000000 08:01 3407932    /lib/libpng12.so.0.42.0
003bc000-003bd000 r--p 00022000 08:01 3407932    /lib/libpng12.so.0.42.0
003bd000-003be000 rw-p 00023000 08:01 3407932    /lib/libpng12.so.0.42.0
003be000-003ce000 r-xp 00000000 08:01 3539927    /lib/tls/i686/cmov/libresolv-2.11.1.so
003ce000-003cf000 r--p 00010000 08:01 3539927    /lib/tls/i686/cmov/libresolv-2.11.1.so
003cf000-003d0000 rw-p 00011000 08:01 3539927    /lib/tls/i686/cmov/libresolv-2.11.1.so
003d0000-003d2000 rw-p 00000000 00:00 0 
003d2000-003d3000 rwxp 00000000 00:00 0 
003d3000-003d9000 r-xp 00000000 08:01 3539912    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
003d9000-003da000 r--p 00006000 08:01 3539912    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
003da000-003db000 rw-p 00007000 08:01 3539912    /lib/tls/i686/cmov/libnss_compat-2.11.1.so
003db000-003f4000 r-xp 00000000 08:01 3408037    /lib/libselinux.so.1
003f4000-003f5000 r--p 00018000 08:01 3408037    /lib/libselinux.so.1
003f5000-003f6000 rw-p 00019000 08:01 3408037    /lib/libselinux.so.1
003f6000-0040f000 r-xp 00000000 08:01 1969024    /usr/lib/libatk-1.0.so.0.3009.1
0040f000-00410000 ---p 00019000 08:01 1969024    /usr/lib/libatk-1.0.so.0.3009.1
00410000-00411000 r--p 00019000 08:01 1969024    /usr/lib/libatk-1.0.so.0.3009.1
00411000-00412000 rw-p 0001a000 08:01 1969024    /usr/lib/libatk-1.0.so.0.3009.1
00412000-00416000 r-xp 00000000 08:01 1973283    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
00416000-00417000 ---p 00004000 08:01 1973283    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
00417000-00418000 r--p 00004000 08:01 1973283    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
00418000-00419000 rw-p 00005000 08:01 1973283    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
00419000-0041c000 r-xp 00000000 08:01 1969079    /usr/lib/libcanberra-gtk.so.0.1.5
0041c000-0041d000 r--p 00003000 08:01 1969079    /usr/lib/libcanberra-gtk.so.0.1.5
0041d000-0041e000 rw-p 00004000 08:01 1969079    /usr/lib/libcanberra-gtk.so.0.1.5
0041e000-00425000 r-xp 00000000 08:01 1969908    /usr/lib/libvorbisfile.so.3.3.2
00425000-00426000 r--p 00006000 08:01 1969908    /usr/lib/libvorbisfile.so.3.3.2
00426000-00427000 rw-p 00007000 08:01 1969908    /usr/lib/libvorbisfile.so.3.3.2
00427000-0042c000 r-xp 00000000 08:01 1969662    /usr/lib/libogg.so.0.6.0
0042c000-0042d000 r--p 00004000 08:01 1969662    /usr/lib/libogg.so.0.6.0
0042d000-0042e000 rw-p 00005000 08:01 1969662    /usr/lib/libogg.so.0.6.0
0042e000-0043b000 r-xp 00000000 08:01 1969853    /usr/lib/libtdb.so.1.2.0
0043b000-0043c000 r--p 0000c000 08:01 1969853    /usr/lib/libtdb.so.1.2.0
0043c000-0043d000 rw-p 0000d000 08:01 1969853    /usr/lib/libtdb.so.1.2.0
0043d000-00440000 r-xp 00000000 08:01 1979068    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
00440000-00441000 r--p 00002000 08:01 1979068    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
00441000-00442000 rw-p 00003000 08:01 1979068    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-bmp.so
00442000-00444000 r-xp 00000000 08:01 3539905    /lib/tls/i686/cmov/libdl-2.11.1.so
00444000-00445000 r--p 00001000 08:01 3539905    /lib/tls/i686/cmov/libdl-2.11.1.so
00445000-00446000 rw-p 00002000 08:01 3539905    /lib/tls/i686/cmov/libdl-2.11.1.so
00446000-004b7000 r-xp 00000000 08:01 1982871    /usr/lib/libfreetype.so.6.3.22
004b7000-004bb000 r--p 00070000 08:01 1982871    /usr/lib/libfreetype.so.6.3.22
004bb000-004bc000 rw-p 00074000 08:01 1982871    /usr/lib/libfreetype.so.6.3.22
004bc000-004c3000 r-xp 00000000 08:01 1969579    /usr/lib/libltdl.so.7.2.1
004c3000-004c4000 r--p 00006000 08:01 1969579    /usr/lib/libltdl.so.7.2.1
004c4000-004c5000 rw-p 00007000 08:01 1969579    /usr/lib/libltdl.so.7.2.1
004c5000-004c8000 r-xp 00000000 08:01 4079368    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-gtk-3659.so
004c8000-004c9000 rw-p 00002000 08:01 4079368    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-gtk-3659.so
004c9000-004ca000 rw-p 00000000 00:00 0 
004ca000-004ce000 r-xp 00000000 08:01 1968979    /usr/lib/libXtst.so.6.1.0
004ce000-004cf000 r--p 00003000 08:01 1968979    /usr/lib/libXtst.so.6.1.0
004cf000-004d0000 rw-p 00004000 08:01 1968979    /usr/lib/libXtst.so.6.1.0
004d0000-00510000 r-xp 00000000 08:01 1966210    /usr/lib/libpango-1.0.so.0.2800.0
00510000-00511000 ---p 00040000 08:01 1966210    /usr/lib/libpango-1.0.so.0.2800.0
00511000-00512000 r--p 00040000 08:01 1966210    /usr/lib/libpango-1.0.so.0.2800.0
00512000-00513000 rw-p 00041000 08:01 1966210    /usr/lib/libpango-1.0.so.0.2800.0
00513000-00528000 r-xp 00000000 08:01 3539925    /lib/tls/i686/cmov/libpthread-2.11.1.so
00528000-00529000 r--p 00014000 08:01 3539925    /lib/tls/i686/cmov/libpthread-2.11.1.so
00529000-0052a000 rw-p 00015000 08:01 3539925    /lib/tls/i686/cmov/libpthread-2.11.1.so
0052a000-0052c000 rw-p 00000000 00:00 0 
0052c000-00553000 r-xp 00000000 08:01 1969904    /usr/lib/libvorbis.so.0.4.3
00553000-00554000 r--p 00026000 08:01 1969904    /usr/lib/libvorbis.so.0.4.3
00554000-00555000 rw-p 00027000 08:01 1969904    /usr/lib/libvorbis.so.0.4.3
00555000-00569000 r-xp 00000000 08:01 2767486    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
00569000-0056a000 r--p 00013000 08:01 2767486    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
0056a000-0056b000 rw-p 00014000 08:01 2767486    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnet.so
0056c000-00576000 r-xp 00000000 08:01 1966580    /usr/lib/libpangocairo-1.0.so.0.2800.0
00576000-00577000 r--p 00009000 08:01 1966580    /usr/lib/libpangocairo-1.0.so.0.2800.0
00577000-00578000 rw-p 0000a000 08:01 1966580    /usr/lib/libpangocairo-1.0.so.0.2800.0
00578000-00612000 r-xp 00000000 08:01 1969291    /usr/lib/libgio-2.0.so.0.2400.1
00612000-00613000 ---p 0009a000 08:01 1969291    /usr/lib/libgio-2.0.so.0.2400.1
00613000-00614000 r--p 0009a000 08:01 1969291    /usr/lib/libgio-2.0.so.0.2400.1
00614000-00615000 rw-p 0009b000 08:01 1969291    /usr/lib/libgio-2.0.so.0.2400.1
00615000-00616000 rw-p 00000000 00:00 0 
00616000-00640000 r-xp 00000000 08:01 1973230    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00640000-00641000 r--p 00029000 08:01 1973230    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00641000-00642000 rw-p 0002a000 08:01 1973230    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
00642000-00644000 r-xp 00000000 08:01 1967088    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00644000-00645000 r--p 00001000 08:01 1967088    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00645000-00646000 rw-p 00002000 08:01 1967088    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
00646000-00647000 r-xp 00000000 08:01 4079601    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/56/1/.cp/os/linux/x86/libjnotify.so
00647000-00648000 rw-p 00001000 08:01 4079601    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/56/1/.cp/os/linux/x86/libjnotify.so
00648000-0064c000 r-xp 00000000 08:01 1968953    /usr/lib/libXfixes.so.3.1.0
0064c000-0064d000 r--p 00003000 08:01 1968953    /usr/lib/libXfixes.so.3.1.0
0064d000-0064e000 rw-p 00004000 08:01 1968953    /usr/lib/libXfixes.so.3.1.0
0064f000-00667000 r-xp 00000000 08:01 1969945    /usr/lib/libxcb.so.1.1.0
00667000-00668000 r--p 00017000 08:01 1969945    /usr/lib/libxcb.so.1.1.0
00668000-00669000 rw-p 00018000 08:01 1969945    /usr/lib/libxcb.so.1.1.0
00669000-0066d000 r-xp 00000000 08:01 1979075    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
0066d000-0066e000 r--p 00003000 08:01 1979075    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
0066e000-0066f000 rw-p 00004000 08:01 1979075    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
0066f000-00674000 r-xp 00000000 08:01 1973247    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
00674000-00675000 r--p 00004000 08:01 1973247    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
00675000-00676000 rw-p 00005000 08:01 1973247    /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so
00676000-0069a000 r-xp 00000000 08:01 1972802    /usr/lib/gio/modules/libgvfsdbus.so
0069a000-0069b000 r--p 00023000 08:01 1972802    /usr/lib/gio/modules/libgvfsdbus.so
0069b000-0069c000 rw-p 00024000 08:01 1972802    /usr/lib/gio/modules/libgvfsdbus.so
0069c000-006a6000 r-xp 00000000 08:01 4080800    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-cairo-gtk-3659.so
006a6000-006a7000 rw-p 00009000 08:01 4080800    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-cairo-gtk-3659.so
006a9000-006ac000 r-xp 00000000 08:01 1969309    /usr/lib/libgmodule-2.0.so.0.2400.1
006ac000-006ad000 r--p 00002000 08:01 1969309    /usr/lib/libgmodule-2.0.so.0.2400.1
006ad000-006ae000 rw-p 00003000 08:01 1969309    /usr/lib/libgmodule-2.0.so.0.2400.1
006ae000-006e7000 r-xp 00000000 08:01 1969494    /usr/lib/libibus.so.1.0.0
006e7000-006e8000 r--p 00039000 08:01 1969494    /usr/lib/libibus.so.1.0.0
006e8000-006e9000 rw-p 0003a000 08:01 1969494    /usr/lib/libibus.so.1.0.0
006e9000-006eb000 r-xp 00000000 08:01 3407993    /lib/libnss_mdns4_minimal.so.2
006eb000-006ec000 r--p 00001000 08:01 3407993    /lib/libnss_mdns4_minimal.so.2
006ec000-006ed000 rw-p 00002000 08:01 3407993    /lib/libnss_mdns4_minimal.so.2
006ed000-006f1000 r-xp 00000000 08:01 3539914    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006f1000-006f2000 r--p 00004000 08:01 3539914    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006f2000-006f3000 rw-p 00005000 08:01 3539914    /lib/tls/i686/cmov/libnss_dns-2.11.1.so
006f3000-00717000 r-xp 00000000 08:01 2764868    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00717000-00718000 r--p 00023000 08:01 2764868    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
00718000-0071a000 rw-p 00024000 08:01 2764868    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libjava.so
0071a000-0078d000 r-xp 00000000 08:01 1969167    /usr/lib/libdirectfb-1.2.so.0.8.0
0078d000-0078e000 ---p 00073000 08:01 1969167    /usr/lib/libdirectfb-1.2.so.0.8.0
0078e000-0078f000 r--p 00073000 08:01 1969167    /usr/lib/libdirectfb-1.2.so.0.8.0
0078f000-00790000 rw-p 00074000 08:01 1969167    /usr/lib/libdirectfb-1.2.so.0.8.0
00790000-00791000 rw-p 00000000 00:00 0 
00791000-007c8000 r-xp 00000000 08:01 3408009    /lib/libdbus-1.so.3.4.0
007c8000-007c9000 r--p 00036000 08:01 3408009    /lib/libdbus-1.so.3.4.0
007c9000-007ca000 rw-p 00037000 08:01 3408009    /lib/libdbus-1.so.3.4.0
007ca000-007cd000 r-xp 00000000 08:01 4080997    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-gnome-gtk-3659.so
007cd000-007ce000 rw-p 00002000 08:01 4080997    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-gnome-gtk-3659.so
007ce000-007e2000 r-xp 00000000 08:01 1969313    /usr/lib/libgnome-2.so.0.3000.0
007e2000-007e3000 r--p 00013000 08:01 1969313    /usr/lib/libgnome-2.so.0.3000.0
007e3000-007e4000 rw-p 00014000 08:01 1969313    /usr/lib/libgnome-2.so.0.3000.0
007e4000-007e5000 r-xp 00000000 08:01 1974289    /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
007e5000-007e6000 r--p 00000000 08:01 1974289    /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
007e6000-007e7000 rw-p 00001000 08:01 1974289    /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so
007e7000-007ed000 r-xp 00000000 08:01 1968971    /usr/lib/libXrandr.so.2.2.0
007ed000-007ee000 r--p 00005000 08:01 1968971    /usr/lib/libXrandr.so.2.2.0
007ee000-007ef000 rw-p 00006000 08:01 1968971    /usr/lib/libXrandr.so.2.2.0
007ef000-00848000 r-xp 00000000 08:01 4079369    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-pi-gtk-3659.so
00848000-0084a000 rw-p 00058000 08:01 4079369    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-pi-gtk-3659.so
0084a000-0084b000 rw-p 00000000 00:00 0 
0084b000-0087c000 r-xp 00000000 08:01 1969647    /usr/lib/libnspr4.so
0087c000-0087d000 r--p 00030000 08:01 1969647    /usr/lib/libnspr4.so
0087d000-0087e000 rw-p 00031000 08:01 1969647    /usr/lib/libnspr4.so
0087e000-00880000 rw-p 00000000 00:00 0 
00880000-00882000 r-xp 00000000 08:01 1966587    /usr/lib/libavahi-glib.so.1.0.1
00882000-00883000 r--p 00001000 08:01 1966587    /usr/lib/libavahi-glib.so.1.0.1
00883000-00884000 rw-p 00002000 08:01 1966587    /usr/lib/libavahi-glib.so.1.0.1
00884000-00886000 r-xp 00000000 08:01 3539933    /lib/tls/i686/cmov/libutil-2.11.1.so
00886000-00887000 r--p 00001000 08:01 3539933    /lib/tls/i686/cmov/libutil-2.11.1.so
00887000-00888000 rw-p 00002000 08:01 3539933    /lib/tls/i686/cmov/libutil-2.11.1.so
00888000-0088c000 rwxp 00000000 00:00 0 
0088c000-00891000 r-xp 00000000 08:01 1979069    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
00891000-00892000 r--p 00004000 08:01 1979069    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
00892000-00893000 rw-p 00005000 08:01 1979069    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
00893000-0089d000 r-xp 00000000 08:01 1966987    /usr/lib/libavahi-common.so.3.5.1
0089d000-0089e000 r--p 00009000 08:01 1966987    /usr/lib/libavahi-common.so.3.5.1
0089e000-0089f000 rw-p 0000a000 08:01 1966987    /usr/lib/libavahi-common.so.3.5.1
0089f000-008a8000 r-xp 00000000 08:01 1969208    /usr/lib/libesd.so.0.2.39
008a8000-008a9000 r--p 00008000 08:01 1969208    /usr/lib/libesd.so.0.2.39
008a9000-008aa000 rw-p 00009000 08:01 1969208    /usr/lib/libesd.so.0.2.39
008aa000-008b2000 rwxp 00000000 00:00 0 
008b2000-008c0000 r-xp 00000000 08:01 1966990    /usr/lib/libavahi-client.so.3.2.5
008c0000-008c1000 ---p 0000e000 08:01 1966990    /usr/lib/libavahi-client.so.3.2.5
008c1000-008c2000 r--p 0000e000 08:01 1966990    /usr/lib/libavahi-client.so.3.2.5
008c2000-008c3000 rw-p 0000f000 08:01 1966990    /usr/lib/libavahi-client.so.3.2.5
008c3000-008ca000 r-xp 00000000 08:01 1968932    /usr/lib/libSM.so.6.0.1
008ca000-008cb000 r--p 00006000 08:01 1968932    /usr/lib/libSM.so.6.0.1
008cb000-008cc000 rw-p 00007000 08:01 1968932    /usr/lib/libSM.so.6.0.1
008cc000-008dd000 r-xp 00000000 08:01 1972801    /usr/lib/gio/modules/libgioremote-volume-monitor.so
008dd000-008de000 r--p 00011000 08:01 1972801    /usr/lib/gio/modules/libgioremote-volume-monitor.so
008de000-008df000 rw-p 00012000 08:01 1972801    /usr/lib/gio/modules/libgioremote-volume-monitor.so
008df000-008e8000 r-xp 00000000 08:01 4079376    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-atk-gtk-3659.so
008e8000-008e9000 rw-p 00008000 08:01 4079376    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/226/1/.cp/libswt-atk-gtk-3659.so
008e9000-008f2000 r-xp 00000000 08:01 3408027    /lib/libpopt.so.0.0.0
008f2000-008f3000 r--p 00008000 08:01 3408027    /lib/libpopt.so.0.0.0
008f3000-008f4000 rw-p 00009000 08:01 3408027    /lib/libpopt.so.0.0.0
008f7000-008fe000 r-xp 00000000 08:01 2883710    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
008fe000-008ff000 r--p 00006000 08:01 2883710    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
008ff000-00900000 rw-p 00007000 08:01 2883710    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/native_threads/libhpi.so
00900000-00904000 r-xp 00000000 08:01 1968928    /usr/lib/libORBitCosNaming-2.so.0.1.0
00904000-00905000 r--p 00003000 08:01 1968928    /usr/lib/libORBitCosNaming-2.so.0.1.0
00905000-00906000 rw-p 00004000 08:01 1968928    /usr/lib/libORBitCosNaming-2.so.0.1.0
00906000-0090c000 r-xp 00000000 08:01 1973284    /usr/lib/libgailutil.so.18.0.1
0090c000-0090d000 r--p 00005000 08:01 1973284    /usr/lib/libgailutil.so.18.0.1
0090d000-0090e000 rw-p 00006000 08:01 1973284    /usr/lib/libgailutil.so.18.0.1
0090e000-0091c000 r-xp 00000000 08:01 2764869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0091c000-0091d000 r--p 0000d000 08:01 2764869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0091d000-0091e000 rw-p 0000e000 08:01 2764869    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libj2pkcs11.so
0091e000-00955000 r-xp 00000000 08:01 1970753    /usr/lib/nss/libsoftokn3.so
00955000-00956000 r--p 00037000 08:01 1970753    /usr/lib/nss/libsoftokn3.so
00956000-00957000 rw-p 00038000 08:01 1970753    /usr/lib/nss/libsoftokn3.so
00957000-0095a000 r-xp 00000000 08:01 3408063    /lib/libuuid.so.1.3.0
0095a000-0095b000 r--p 00002000 08:01 3408063    /lib/libuuid.so.1.3.0
0095b000-0095c000 rw-p 00003000 08:01 3408063    /lib/libuuid.so.1.3.0
0095c000-0095f000 r-xp 00000000 08:01 3407961    /lib/libgpg-error.so.0.4.0
0095f000-00960000 r--p 00002000 08:01 3407961    /lib/libgpg-error.so.0.4.0
00960000-00961000 rw-p 00003000 08:01 3407961    /lib/libgpg-error.so.0.4.0
00964000-009f7000 r-xp 00000000 08:01 1979102    /usr/lib/libgdk-x11-2.0.so.0.2000.1
009f7000-009f9000 r--p 00093000 08:01 1979102    /usr/lib/libgdk-x11-2.0.so.0.2000.1
009f9000-009fa000 rw-p 00095000 08:01 1979102    /usr/lib/libgdk-x11-2.0.so.0.2000.1
009fd000-00a11000 r-xp 00000000 08:01 1969165    /usr/lib/libdirect-1.2.so.0.8.0
00a11000-00a12000 r--p 00013000 08:01 1969165    /usr/lib/libdirect-1.2.so.0.8.0
00a12000-00a13000 rw-p 00014000 08:01 1969165    /usr/lib/libdirect-1.2.so.0.8.0
00a13000-00a42000 r-xp 00000000 08:01 1969255    /usr/lib/libgconf-2.so.4.1.5
00a42000-00a43000 r--p 0002e000 08:01 1969255    /usr/lib/libgconf-2.so.4.1.5
00a43000-00a45000 rw-p 0002f000 08:01 1969255    /usr/lib/libgconf-2.so.4.1.5
00a45000-00a48000 r-xp 00000000 08:01 1969871    /usr/lib/libtotem-plparser-mini.so.17.0.0
00a48000-00a49000 ---p 00003000 08:01 1969871    /usr/lib/libtotem-plparser-mini.so.17.0.0
00a49000-00a4a000 r--p 00003000 08:01 1969871    /usr/lib/libtotem-plparser-mini.so.17.0.0
00a4a000-00a4b000 rw-p 00004000 08:01 1969871    /usr/lib/libtotem-plparser-mini.so.17.0.0
00a4b000-00a4c000 r-xp 00000000 00:00 0          [vdso]
00a4c000-00a5b000 r-xp 00000000 08:01 1969850    /usr/lib/libtasn1.so.3.1.7
00a5b000-00a5c000 r--p 0000e000 08:01 1969850    /usr/lib/libtasn1.so.3.1.7
00a5c000-00a5d000 rw-p 0000f000 08:01 1969850    /usr/lib/libtasn1.so.3.1.7
00a5e000-00a6c000 r-xp 00000000 08:01 1969081    /usr/lib/libcanberra.so.0.2.1
00a6c000-00a6d000 r--p 0000d000 08:01 1969081    /usr/lib/libcanberra.so.0.2.1
00a6d000-00a6e000 rw-p 0000e000 08:01 1969081    /usr/lib/libcanberra.so.0.2.1
00a6e000-00a73000 r-xp 00000000 08:01 2883707    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so
00a73000-00a74000 r--p 00004000 08:01 2883707    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so
00a74000-00a75000 rw-p 00005000 08:01 2883707    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/headless/libmawt.so
00a75000-00a7c000 rwxp 00000000 00:00 0 
00a7c000-00a8f000 r-xp 00000000 08:01 3539910    /lib/tls/i686/cmov/libnsl-2.11.1.so
00a8f000-00a90000 r--p 00012000 08:01 3539910    /lib/tls/i686/cmov/libnsl-2.11.1.so
00a90000-00a91000 rw-p 00013000 08:01 3539910    /lib/tls/i686/cmov/libnsl-2.11.1.so
00a91000-00a93000 rw-p 00000000 00:00 0 
00a93000-00ab0000 r-xp 00000000 08:01 1966106    /usr/lib/libdbus-glib-1.so.2.1.0
00ab0000-00ab1000 r--p 0001c000 08:01 1966106    /usr/lib/libdbus-glib-1.so.2.1.0
00ab1000-00ab2000 rw-p 0001d000 08:01 1966106    /usr/lib/libdbus-glib-1.so.2.1.0
00ab2000-00ac0000 r-xp 00000000 08:01 1968951    /usr/lib/libXext.so.6.4.0
00ac0000-00ac1000 r--p 0000d000 08:01 1968951    /usr/lib/libXext.so.6.4.0
00ac1000-00ac2000 rw-p 0000e000 08:01 1968951    /usr/lib/libXext.so.6.4.0
00ac2000-00acd000 r-xp 00000000 08:01 1982839    /usr/lib/liblber-2.4.so.2.5.4
00acd000-00ace000 r--p 0000a000 08:01 1982839    /usr/lib/liblber-2.4.so.2.5.4
00ace000-00acf000 rw-p 0000b000 08:01 1982839    /usr/lib/liblber-2.4.so.2.5.4
00ad0000-00c23000 r-xp 00000000 08:01 3539899    /lib/tls/i686/cmov/libc-2.11.1.so
00c23000-00c24000 ---p 00153000 08:01 3539899    /lib/tls/i686/cmov/libc-2.11.1.so
00c24000-00c26000 r--p 00153000 08:01 3539899    /lib/tls/i686/cmov/libc-2.11.1.so
00c26000-00c27000 rw-p 00155000 08:01 3539899    /lib/tls/i686/cmov/libc-2.11.1.so
00c27000-00c2a000 rw-p 00000000 00:00 0 
00c2a000-00c3d000 r-xp 00000000 08:01 1969053    /usr/lib/libbonobo-activation.so.4.0.0
00c3d000-00c3e000 r--p 00012000 08:01 1969053    /usr/lib/libbonobo-activation.so.4.0.0
00c3e000-00c3f000 rw-p 00013000 08:01 1969053    /usr/lib/libbonobo-activation.so.4.0.0
00c3f000-00c40000 rw-p 00000000 00:00 0 
00c40000-00c55000 r-xp 00000000 08:01 1969016    /usr/lib/libart_lgpl_2.so.2.3.20
00c55000-00c56000 r--p 00014000 08:01 1969016    /usr/lib/libart_lgpl_2.so.2.3.20
00c56000-00c57000 rw-p 00015000 08:01 1969016    /usr/lib/libart_lgpl_2.so.2.3.20
00c57000-00c59000 r-xp 00000000 08:01 3407928    /lib/libcom_err.so.2.1
00c59000-00c5a000 r--p 00001000 08:01 3407928    /lib/libcom_err.so.2.1
00c5a000-00c5b000 rw-p 00002000 08:01 3407928    /lib/libcom_err.so.2.1
00c5d000-00c72000 r-xp 00000000 08:01 1970822    /usr/lib/libnssutil3.so
00c72000-00c75000 r--p 00014000 08:01 1970822    /usr/lib/libnssutil3.so
00c75000-00c76000 rw-p 00017000 08:01 1970822    /usr/lib/libnssutil3.so
00c76000-00c7c000 r-xp 00000000 08:01 1967021    /usr/lib/libkrb5support.so.0.1
00c7c000-00c7d000 r--p 00005000 08:01 1967021    /usr/lib/libkrb5support.so.0.1
00c7d000-00c7e000 rw-p 00006000 08:01 1967021    /usr/lib/libkrb5support.so.0.1
00c7e000-00c80000 r-xp 00000000 08:01 3407968    /lib/libkeyutils-1.2.so
00c80000-00c81000 r--p 00001000 08:01 3407968    /lib/libkeyutils-1.2.so
00c81000-00c82000 rw-p 00002000 08:01 3407968    /lib/libkeyutils-1.2.so
00c86000-00c92000 r-xp 00000000 08:01 2766673    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00c92000-00c93000 r--p 0000b000 08:01 2766673    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00c93000-00c94000 rw-p 0000c000 08:01 2766673    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libverify.so
00c9d000-00cc2000 r-xp 00000000 08:01 1966752    /usr/lib/libpangoft2-1.0.so.0.2800.0
00cc2000-00cc3000 r--p 00024000 08:01 1966752    /usr/lib/libpangoft2-1.0.so.0.2800.0
00cc3000-00cc4000 rw-p 00025000 08:01 1966752    /usr/lib/libpangoft2-1.0.so.0.2800.0
00cc4000-00cdf000 r-xp 00000000 08:01 1969319    /usr/lib/libgnome-keyring.so.0.1.1
00cdf000-00ce0000 r--p 0001a000 08:01 1969319    /usr/lib/libgnome-keyring.so.0.1.1
00ce0000-00ce1000 rw-p 0001b000 08:01 1969319    /usr/lib/libgnome-keyring.so.0.1.1
00ce8000-00cf0000 r-xp 00000000 08:01 3539920    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cf0000-00cf1000 r--p 00007000 08:01 3539920    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cf1000-00cf2000 rw-p 00008000 08:01 3539920    /lib/tls/i686/cmov/libnss_nis-2.11.1.so
00cf2000-00d03000 r-xp 00000000 08:01 1974292    /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
00d03000-00d04000 ---p 00011000 08:01 1974292    /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
00d04000-00d05000 r--p 00011000 08:01 1974292    /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
00d05000-00d06000 rw-p 00012000 08:01 1974292    /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
00d08000-00d0f000 r-xp 00000000 08:01 2766658    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00d0f000-00d10000 r--p 00006000 08:01 2766658    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00d10000-00d11000 rw-p 00007000 08:01 2766658    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libnio.so
00d11000-00d26000 r-xp 00000000 08:01 1968903    /usr/lib/libICE.so.6.3.0
00d26000-00d27000 r--p 00014000 08:01 1968903    /usr/lib/libICE.so.6.3.0
00d27000-00d28000 rw-p 00015000 08:01 1968903    /usr/lib/libICE.so.6.3.0
00d28000-00d2a000 rw-p 00000000 00:00 0 
00d31000-00d60000 r-xp 00000000 08:01 3408013    /lib/libpcre.so.3.12.1
00d60000-00d61000 r--p 0002e000 08:01 3408013    /lib/libpcre.so.3.12.1
00d61000-00d62000 rw-p 0002f000 08:01 3408013    /lib/libpcre.so.3.12.1
00d62000-00dad000 r-xp 00000000 08:01 1970746    /usr/lib/nss/libfreebl3.so
00dad000-00dae000 r--p 0004a000 08:01 1970746    /usr/lib/nss/libfreebl3.so
00dae000-00daf000 rw-p 0004b000 08:01 1970746    /usr/lib/nss/libfreebl3.so
00daf000-00db3000 rw-p 00000000 00:00 0 
00dc0000-00e17000 r-xp 00000000 08:01 1969709    /usr/lib/libpixman-1.so.0.16.4
00e17000-00e19000 r--p 00057000 08:01 1969709    /usr/lib/libpixman-1.so.0.16.4
00e19000-00e1a000 rw-p 00059000 08:01 1969709    /usr/lib/libpixman-1.so.0.16.4
00e1a000-00e3c000 r-xp 00000000 08:01 1969028    /usr/lib/libaudiofile.so.0.0.2
00e3c000-00e3d000 r--p 00021000 08:01 1969028    /usr/lib/libaudiofile.so.0.0.2
00e3d000-00e3f000 rw-p 00022000 08:01 1969028    /usr/lib/libaudiofile.so.0.0.2
00e4d000-00e4f000 r-xp 00000000 08:01 1968947    /usr/lib/libXdamage.so.1.1.0
00e4f000-00e50000 r--p 00001000 08:01 1968947    /usr/lib/libXdamage.so.1.1.0
00e50000-00e51000 rw-p 00002000 08:01 1968947    /usr/lib/libXdamage.so.1.1.0
00e51000-00e69000 r-xp 00000000 08:01 1974290    /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
00e69000-00e6a000 r--p 00017000 08:01 1974290    /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
00e6a000-00e6b000 rw-p 00018000 08:01 1974290    /usr/lib/mozilla/plugins/libtotem-cone-plugin.so
00e6b000-00e75000 r-xp 00000000 08:01 3408053    /lib/libudev.so.0.6.1
00e75000-00e76000 r--p 00009000 08:01 3408053    /lib/libudev.so.0.6.1
00e76000-00e77000 rw-p 0000a000 08:01 3408053    /lib/libudev.so.0.6.1
00e77000-00e94000 r-xp 00000000 08:01 3407955    /lib/libgcc_s.so.1
00e94000-00e95000 r--p 0001c000 08:01 3407955    /lib/libgcc_s.so.1
00e95000-00e96000 rw-p 0001d000 08:01 3407955    /lib/libgcc_s.so.1
00e97000-00e99000 r-xp 00000000 08:01 1968961    /usr/lib/libXinerama.so.1.0.0
00e99000-00e9a000 r--p 00001000 08:01 1968961    /usr/lib/libXinerama.so.1.0.0
00e9a000-00e9b000 rw-p 00002000 08:01 1968961    /usr/lib/libXinerama.so.1.0.0
00e9b000-00ebb000 rwxp 00000000 00:00 0 
00ebb000-00ed6000 r-xp 00000000 08:01 3407897    /lib/ld-2.11.1.so
00ed6000-00ed7000 r--p 0001a000 08:01 3407897    /lib/ld-2.11.1.so
00ed7000-00ed8000 rw-p 0001b000 08:01 3407897    /lib/ld-2.11.1.so
00ed8000-00edb000 r-xp 00000000 08:01 1969710    /usr/lib/libplc4.so
00edb000-00edc000 r--p 00002000 08:01 1969710    /usr/lib/libplc4.so
00edc000-00edd000 rw-p 00003000 08:01 1969710    /usr/lib/libplc4.so
00edd000-00ef0000 r-xp 00000000 08:01 1974293    /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
00ef0000-00ef1000 ---p 00013000 08:01 1974293    /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
00ef1000-00ef2000 r--p 00013000 08:01 1974293    /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
00ef2000-00ef3000 rw-p 00014000 08:01 1974293    /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
00ef6000-00f0a000 r-xp 00000000 08:01 1969478    /usr/lib/libgvfscommon.so.0.0.0
00f0a000-00f0b000 r--p 00013000 08:01 1969478    /usr/lib/libgvfscommon.so.0.0.0
00f0b000-00f0c000 rw-p 00014000 08:01 1969478    /usr/lib/libgvfscommon.so.0.0.0
00f22000-00f2a000 r-xp 00000000 08:01 1968945    /usr/lib/libXcursor.so.1.0.2
00f2a000-00f2b000 r--p 00007000 08:01 1968945    /usr/lib/libXcursor.so.1.0.2
00f2b000-00f2c000 rw-p 00008000 08:01 1968945    /usr/lib/libXcursor.so.1.0.2
00f2c000-00f2e000 r-xp 00000000 08:01 1969712    /usr/lib/libplds4.so
00f2e000-00f2f000 r--p 00001000 08:01 1969712    /usr/lib/libplds4.so
00f2f000-00f30000 rw-p 00002000 08:01 1969712    /usr/lib/libplds4.so
00f30000-00f49000 r-xp 00000000 08:01 1974291    /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
00f49000-00f4a000 r--p 00019000 08:01 1974291    /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
00f4a000-00f4b000 rw-p 0001a000 08:01 1974291    /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
00f4d000-00f55000 r-xp 00000000 08:01 1968973    /usr/lib/libXrender.so.1.3.0
00f55000-00f56000 r--p 00007000 08:01 1968973    /usr/lib/libXrender.so.1.3.0
00f56000-00f57000 rw-p 00008000 08:01 1968973    /usr/lib/libXrender.so.1.3.0
00f57000-00f86000 r-xp 00000000 08:01 1969329    /usr/lib/libgnomecanvas-2.so.0.3000.1
00f86000-00f87000 r--p 0002e000 08:01 1969329    /usr/lib/libgnomecanvas-2.so.0.3000.1
00f87000-00f88000 rw-p 0002f000 08:01 1969329    /usr/lib/libgnomecanvas-2.so.0.3000.1
00f88000-00faa000 r-xp 00000000 08:01 1970818    /usr/lib/libsmime3.so
00faa000-00fab000 ---p 00022000 08:01 1970818    /usr/lib/libsmime3.so
00fab000-00fad000 r--p 00022000 08:01 1970818    /usr/lib/libsmime3.so
00fad000-00fae000 rw-p 00024000 08:01 1970818    /usr/lib/libsmime3.so
00faf000-00fbb000 r-xp 00000000 08:01 4077596    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.2.R36x_v20101019_1345/eclipse_1310.so
00fbb000-00fbc000 rw-p 0000c000 08:01 4077596    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.2.R36x_v20101019_1345/eclipse_1310.so
00fbc000-0140f000 r-xp 00000000 08:01 2766665    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
0140f000-01410000 ---p 00453000 08:01 2766665    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01410000-01427000 r--p 00453000 08:01 2766665    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01427000-01434000 rw-p 0046a000 08:01 2766665    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/libjvm.so
01434000-01850000 rw-p 00000000 00:00 0 
01850000-018e6000 r-xp 00000000 08:01 1969343    /usr/lib/libgnutls.so.26.14.12
018e6000-018ea000 r--p 00095000 08:01 1969343    /usr/lib/libgnutls.so.26.14.12
018ea000-018eb000 rw-p 00099000 08:01 1969343    /usr/lib/libgnutls.so.26.14.12
018eb000-01945000 r-xp 00000000 08:01 1969055    /usr/lib/libbonoboui-2.so.0.0.0
01945000-01946000 r--p 00059000 08:01 1969055    /usr/lib/libbonoboui-2.so.0.0.0
01946000-01948000 rw-p 0005a000 08:01 1969055    /usr/lib/libbonoboui-2.so.0.0.0
01948000-01968000 rwxp 00000000 00:00 0 
01968000-019ab000 r-xp 00000000 08:01 1966594    /usr/lib/libcurl.so.4.1.1
019ab000-019ac000 r--p 00042000 08:01 1966594    /usr/lib/libcurl.so.4.1.1
019ac000-019ad000 rw-p 00043000 08:01 1966594    /usr/lib/libcurl.so.4.1.1
019ad000-019cf000 r-xp 00000000 08:01 1981460    /usr/lib/libk5crypto.so.3.1
019cf000-019d0000 r--p 00021000 08:01 1981460    /usr/lib/libk5crypto.so.3.1
019d0000-019d1000 rw-p 00022000 08:01 1981460    /usr/lib/libk5crypto.so.3.1
01ab3000-01ae2000 r-xp 00000000 08:01 2752763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
01ae2000-01ae3000 r--p 0002e000 08:01 2752763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
01ae3000-01ae4000 rw-p 0002f000 08:01 2752763    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so
01ae4000-01c1c000 r-xp 00000000 08:01 3414674    /lib/i686/cmov/libcrypto.so.0.9.8
01c1c000-01c24000 r--p 00137000 08:01 3414674    /lib/i686/cmov/libcrypto.so.0.9.8
01c24000-01c32000 rw-p 0013f000 08:01 3414674    /lib/i686/cmov/libcrypto.so.0.9.8
01c32000-01c36000 rw-p 00000000 00:00 0 
01c57000-01cc7000 r-xp 00000000 08:01 3407957    /lib/libgcrypt.so.11.5.2
01cc7000-01cc8000 r--p 00070000 08:01 3407957    /lib/libgcrypt.so.11.5.2
01cc8000-01cca000 rw-p 00071000 08:01 3407957    /lib/libgcrypt.so.11.5.2
02007000-0204b000 r-xp 00000000 08:01 1982840    /usr/lib/libldap_r-2.4.so.2.5.4
0204b000-0204c000 r--p 00043000 08:01 1982840    /usr/lib/libldap_r-2.4.so.2.5.4
0204c000-0204d000 rw-p 00044000 08:01 1982840    /usr/lib/libldap_r-2.4.so.2.5.4
0204d000-0204e000 rw-p 00000000 00:00 0 
02220000-02344000 r-xp 00000000 08:01 1969031    /usr/lib/libxml2.so.2.7.6
02344000-02345000 ---p 00124000 08:01 1969031    /usr/lib/libxml2.so.2.7.6
02345000-02349000 r--p 00124000 08:01 1969031    /usr/lib/libxml2.so.2.7.6
02349000-0234a000 rw-p 00128000 08:01 1969031    /usr/lib/libxml2.so.2.7.6
0234a000-0234b000 rw-p 00000000 00:00 0 
02369000-0242c000 r-xp 00000000 08:01 1969018    /usr/lib/libasound.so.2.0.0
0242c000-02430000 r--p 000c2000 08:01 1969018    /usr/lib/libasound.so.2.0.0
02430000-02431000 rw-p 000c6000 08:01 1969018    /usr/lib/libasound.so.2.0.0
0261b000-0264b000 r-xp 00000000 08:01 1969517    /usr/lib/libidn.so.11.5.44
0264b000-0264c000 r--p 0002f000 08:01 1969517    /usr/lib/libidn.so.11.5.44
0264c000-0264d000 rw-p 00030000 08:01 1969517    /usr/lib/libidn.so.11.5.44
02877000-02c44000 r-xp 00000000 08:01 1979101    /usr/lib/libgtk-x11-2.0.so.0.2000.1
02c44000-02c48000 r--p 003cd000 08:01 1979101    /usr/lib/libgtk-x11-2.0.so.0.2000.1
02c48000-02c4a000 rw-p 003d1000 08:01 1979101    /usr/lib/libgtk-x11-2.0.so.0.2000.1
02c4a000-02c4c000 rw-p 00000000 00:00 0 
02e4f000-02e6f000 rwxp 00000000 00:00 0 
0338e000-033dd000 r-xp 00000000 08:01 1968977    /usr/lib/libXt.so.6.0.0
033dd000-033de000 r--p 0004e000 08:01 1968977    /usr/lib/libXt.so.6.0.0
033de000-033e1000 rw-p 0004f000 08:01 1968977    /usr/lib/libXt.so.6.0.0
03566000-035af000 r-xp 00000000 08:01 1968924    /usr/lib/libORBit-2.so.0.1.0
035af000-035b7000 r--p 00049000 08:01 1968924    /usr/lib/libORBit-2.so.0.1.0
035b7000-035b9000 rw-p 00051000 08:01 1968924    /usr/lib/libORBit-2.so.0.1.0
036cc000-03867000 r-xp 00000000 08:01 4072374    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libffmpegsumo.so
03867000-03868000 r--p 0019a000 08:01 4072374    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libffmpegsumo.so
03868000-0386b000 rw-p 0019b000 08:01 4072374    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libffmpegsumo.so
0386b000-038c6000 rw-p 00000000 00:00 0 
03e19000-03e39000 rwxp 00000000 00:00 0 
043e3000-043f9000 r-xp 00000000 08:01 1969795    /usr/lib/libsasl2.so.2.0.23
043f9000-043fa000 r--p 00015000 08:01 1969795    /usr/lib/libsasl2.so.2.0.23
043fa000-043fb000 rw-p 00016000 08:01 1969795    /usr/lib/libsasl2.so.2.0.23
0448c000-0469b000 r-xp 00000000 08:01 4072373    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libosmesa.so
0469b000-046a2000 r--p 0020e000 08:01 4072373    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libosmesa.so
046a2000-046a4000 rw-p 00215000 08:01 4072373    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libosmesa.so
046a4000-046b3000 rw-p 00000000 00:00 0 
04dce000-04e12000 r-xp 00000000 08:01 3414675    /lib/i686/cmov/libssl.so.0.9.8
04e12000-04e13000 r--p 00044000 08:01 3414675    /lib/i686/cmov/libssl.so.0.9.8
04e13000-04e16000 rw-p 00045000 08:01 3414675    /lib/i686/cmov/libssl.so.0.9.8
04fc9000-04ff6000 r-xp 00000000 08:01 1967013    /usr/lib/libgssapi_krb5.so.2.2
04ff6000-04ff7000 r--p 0002d000 08:01 1967013    /usr/lib/libgssapi_krb5.so.2.2
04ff7000-04ff8000 rw-p 0002e000 08:01 1967013    /usr/lib/libgssapi_krb5.so.2.2
05042000-050ec000 r-xp 00000000 08:01 1981463    /usr/lib/libkrb5.so.3.3
050ec000-050ed000 ---p 000aa000 08:01 1981463    /usr/lib/libkrb5.so.3.3
050ed000-050f2000 r--p 000aa000 08:01 1981463    /usr/lib/libkrb5.so.3.3
050f2000-050f3000 rw-p 000af000 08:01 1981463    /usr/lib/libkrb5.so.3.3
0516f000-05288000 r-xp 00000000 08:01 1968934    /usr/lib/libX11.so.6.3.0
05288000-05289000 r--p 00118000 08:01 1968934    /usr/lib/libX11.so.6.3.0
05289000-0528b000 rw-p 00119000 08:01 1968934    /usr/lib/libX11.so.6.3.0
0528b000-0528c000 rw-p 00000000 00:00 0 
056d8000-056f7000 r-xp 00000000 08:01 1969547    /usr/lib/libjpeg.so.62.0.0
056f7000-056f8000 r--p 0001e000 08:01 1969547    /usr/lib/libjpeg.so.62.0.0
056f8000-056f9000 rw-p 0001f000 08:01 1969547    /usr/lib/libjpeg.so.62.0.0
05cd7000-05d07000 r-xp 00000000 08:01 1970814    /usr/lib/libssl3.so
05d07000-05d09000 r--p 0002f000 08:01 1970814    /usr/lib/libssl3.so
05d09000-05d0a000 rw-p 00031000 08:01 1970814    /usr/lib/libssl3.so
05d8a000-05e0f000 r-xp 00000000 08:01 2766657    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
05e0f000-05e10000 r--p 00085000 08:01 2766657    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
05e10000-05e16000 rw-p 00086000 08:01 2766657    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libawt.so
05e16000-05e3b000 rw-p 00000000 00:00 0 
0602f000-0604f000 rwxp 00000000 00:00 0 
06210000-06296000 r-xp 00000000 08:01 1969335    /usr/lib/libgnomeui-2.so.0.2400.3
06296000-06298000 r--p 00085000 08:01 1969335    /usr/lib/libgnomeui-2.so.0.2400.3
06298000-0629a000 rw-p 00087000 08:01 1969335    /usr/lib/libgnomeui-2.so.0.2400.3
0644a000-064a3000 r-xp 00000000 08:01 1969337    /usr/lib/libgnomevfs-2.so.0.2400.2
064a3000-064a5000 r--p 00058000 08:01 1969337    /usr/lib/libgnomevfs-2.so.0.2400.2
064a5000-064a7000 rw-p 0005a000 08:01 1969337    /usr/lib/libgnomevfs-2.so.0.2400.2
06d15000-06d95000 r-xp 00000000 08:01 1969836    /usr/lib/libsqlite3.so.0.8.6
06d95000-06d96000 r--p 0007f000 08:01 1969836    /usr/lib/libsqlite3.so.0.8.6
06d96000-06d97000 rw-p 00080000 08:01 1969836    /usr/lib/libsqlite3.so.0.8.6
06d97000-06d98000 rw-p 00000000 00:00 0 
0729a000-073a9000 r-xp 00000000 08:01 1971038    /usr/lib/libnss3.so
073a9000-073ac000 r--p 0010e000 08:01 1971038    /usr/lib/libnss3.so
073ac000-073ae000 rw-p 00111000 08:01 1971038    /usr/lib/libnss3.so
07a27000-07b10000 r-xp 00000000 08:01 1969843    /usr/lib/libstdc++.so.6.0.13
07b10000-07b11000 ---p 000e9000 08:01 1969843    /usr/lib/libstdc++.so.6.0.13
07b11000-07b15000 r--p 000e9000 08:01 1969843    /usr/lib/libstdc++.so.6.0.13
07b15000-07b16000 rw-p 000ed000 08:01 1969843    /usr/lib/libstdc++.so.6.0.13
07b16000-07b1d000 rw-p 00000000 00:00 0 
07f93000-07fb3000 rwxp 00000000 00:00 0 
08048000-0804c000 r-xp 00000000 08:01 4069806    /home/####/temp/Aptana Studio 3/AptanaStudio3
0804c000-0804d000 rw-p 00003000 08:01 4069806    /home/####/temp/Aptana Studio 3/AptanaStudio3
082ee000-0833f000 r-xp 00000000 08:01 1969051    /usr/lib/libbonobo-2.so.0.0.0
0833f000-08340000 ---p 00051000 08:01 1969051    /usr/lib/libbonobo-2.so.0.0.0
08340000-08343000 r--p 00051000 08:01 1969051    /usr/lib/libbonobo-2.so.0.0.0
08343000-0834a000 rw-p 00054000 08:01 1969051    /usr/lib/libbonobo-2.so.0.0.0
08938000-08fa3000 rw-p 00000000 00:00 0          [heap]
63990000-64d60000 rw-p 00000000 00:00 0 
64d60000-6e430000 rw-p 00000000 00:00 0 
6e430000-70ba7000 rw-p 00000000 00:00 0 
70ba7000-83990000 rw-p 00000000 00:00 0 
83990000-86e10000 rw-p 00000000 00:00 0 
86e10000-93990000 rw-p 00000000 00:00 0 
93990000-940e9000 r--s 00001000 08:01 2752764    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
940e9000-94390000 rw-p 00000000 00:00 0 
94390000-94ad1000 rw-p 0075a000 08:01 2752764    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
94ad1000-94f90000 rw-p 00000000 00:00 0 
94f90000-9508b000 rw-p 00e9b000 08:01 2752764    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
9508b000-95390000 rw-p 00000000 00:00 0 
95390000-95398000 r-xs 00f96000 08:01 2752764    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa
95398000-95790000 rw-p 00000000 00:00 0 
aa100000-aa200000 rw-p 00000000 00:00 0 
aae00000-aae63000 rw-p 00000000 00:00 0 
aae63000-aaf00000 ---p 00000000 00:00 0 
aafff000-ab000000 ---p 00000000 00:00 0 
ab000000-ab800000 rw-p 00000000 00:00 0 
aba00000-abaf9000 rw-p 00000000 00:00 0 
abaf9000-abb00000 ---p 00000000 00:00 0 
abbaf000-abbcb000 r--s 00141000 08:01 4076681    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.team.ui_3.5.102.R36x_v20110203-1036.jar
abbcb000-abbf1000 r--s 0020a000 08:01 4079196    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ui.ide_3.6.2.M20101201-0800.jar
abbf1000-abdf1000 rw-p 00000000 00:00 0 
abdf1000-acdb9000 r-xp 00000000 08:01 1969280    /usr/lib/adobe-flashplugin/libflashplayer.so
acdb9000-ace2e000 rw-p 00fc7000 08:01 1969280    /usr/lib/adobe-flashplugin/libflashplayer.so
ace2e000-ad546000 rw-p 00000000 00:00 0 
ad55e000-ad57a000 r--s 00261000 08:01 4072408    /home/####/temp/Aptana Studio 3/plugins/com.aptana.scripting_3.0.0.1323292937.jar
ad5c6000-ad646000 rw-p 00000000 00:00 0 
ad646000-ad668000 r--s 00000000 08:01 3285161    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
ad668000-ad700000 r--s 00000000 08:01 2757045    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ad700000-ad7fe000 rw-p 00000000 00:00 0 
ad7fe000-ad800000 ---p 00000000 00:00 0 
ad81a000-ad851000 rw-p 00000000 00:00 0 
ad851000-ad874000 r--s 00000000 08:01 3285192    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
ad874000-ad8f4000 rw-p 00000000 00:00 0 
ad8f4000-ad917000 r--s 00000000 08:01 3285183    /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf
ad917000-ad95d000 r--s 00000000 08:01 3285174    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
ad95d000-ad9ae000 r--s 00000000 08:01 3285157    /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf
ad9ae000-ada00000 r--s 00000000 08:01 3285184    /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf
ada00000-adaf9000 rw-p 00000000 00:00 0 
adaf9000-adb00000 ---p 00000000 00:00 0 
adb0c000-adb30000 rw-p 00000000 00:00 0 
adb30000-adb74000 r--s 00000000 08:01 3285176    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
adb74000-ae000000 ---p 00000000 00:00 0 
ae000000-ae100000 rw-p 00000000 00:00 0 
ae100000-ae800000 ---p 00000000 00:00 0 
ae800000-ae900000 rw-p 00000000 00:00 0 
ae900000-afb74000 ---p 00000000 00:00 0 
afb74000-afb75000 ---p 00000000 00:00 0 
afb75000-b0375000 rw-p 00000000 00:00 0 
b0375000-b0378000 ---p 00000000 00:00 0 
b0378000-b0b76000 rw-p 00000000 00:00 0 
b0b76000-b0b77000 ---p 00000000 00:00 0 
b0b77000-b1377000 rw-p 00000000 00:00 0 
b1377000-b3247000 r-xp 00000000 08:01 4072376    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libcefjni.so
b3247000-b3248000 r--p 01ecf000 08:01 4072376    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libcefjni.so
b3248000-b3259000 rw-p 01ed0000 08:01 4072376    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/libcefjni.so
b3259000-b3278000 rw-p 00000000 00:00 0 
b3278000-b327b000 ---p 00000000 00:00 0 
b327b000-b32c9000 rw-p 00000000 00:00 0 
b32c9000-b32cc000 ---p 00000000 00:00 0 
b32cc000-b331a000 rw-p 00000000 00:00 0 
b331a000-b331d000 ---p 00000000 00:00 0 
b331d000-b336b000 rw-p 00000000 00:00 0 
b336b000-b336e000 ---p 00000000 00:00 0 
b336e000-b33bc000 rw-p 00000000 00:00 0 
b33bc000-b33bf000 ---p 00000000 00:00 0 
b33bf000-b340d000 rw-p 00000000 00:00 0 
b340d000-b3410000 ---p 00000000 00:00 0 
b3410000-b345e000 rw-p 00000000 00:00 0 
b345e000-b3461000 ---p 00000000 00:00 0 
b3461000-b34af000 rw-p 00000000 00:00 0 
b34af000-b34b2000 ---p 00000000 00:00 0 
b34b2000-b3500000 rw-p 00000000 00:00 0 
b3500000-b3502000 rw-s 00000000 08:01 3281061    /tmp/.webkitbrowser.cache/data_0
b3502000-b3543000 rw-s 00000000 08:01 3281060    /tmp/.webkitbrowser.cache/index
b3543000-b3605000 rw-p 00000000 00:00 0 
b3612000-b362e000 r--s 00000000 08:01 2369549    /usr/share/mime/mime.cache
b3634000-b3637000 ---p 00000000 00:00 0 
b3637000-b3685000 rw-p 00000000 00:00 0 
b3685000-b3688000 ---p 00000000 00:00 0 
b3688000-b36d6000 rw-p 00000000 00:00 0 
b36d6000-b36d9000 ---p 00000000 00:00 0 
b36d9000-b3727000 rw-p 00000000 00:00 0 
b3727000-b372a000 ---p 00000000 00:00 0 
b372a000-b3778000 rw-p 00000000 00:00 0 
b3778000-b377b000 ---p 00000000 00:00 0 
b377b000-b37c9000 rw-p 00000000 00:00 0 
b37c9000-b37cc000 ---p 00000000 00:00 0 
b37cc000-b381a000 rw-p 00000000 00:00 0 
b381a000-b381d000 ---p 00000000 00:00 0 
b381d000-b386b000 rw-p 00000000 00:00 0 
b386b000-b386e000 ---p 00000000 00:00 0 
b386e000-b38bc000 rw-p 00000000 00:00 0 
b38bc000-b38bf000 ---p 00000000 00:00 0 
b38bf000-b390d000 rw-p 00000000 00:00 0 
b390d000-b3910000 ---p 00000000 00:00 0 
b3910000-b395e000 rw-p 00000000 00:00 0 
b395e000-b3961000 ---p 00000000 00:00 0 
b3961000-b39af000 rw-p 00000000 00:00 0 
b39af000-b39b2000 ---p 00000000 00:00 0 
b39b2000-b3a00000 rw-p 00000000 00:00 0 
b3a00000-b3b00000 rw-p 00000000 00:00 0 
b3b03000-b3b2a000 r--s 00000000 08:01 4072375    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser.linux.x86_1.0.0.1295409059/os/linux/x86/cefjniresources.pak
b3b2a000-b3b2d000 ---p 00000000 00:00 0 
b3b2d000-b3b7b000 rw-p 00000000 00:00 0 
b3b7b000-b3bdb000 rw-s 00000000 00:04 1703988    /SYSV00000000 (deleted)
b3bdb000-b3bde000 ---p 00000000 00:00 0 
b3bde000-b3c2c000 rw-p 00000000 00:00 0 
b3c2c000-b3c46000 r--s 00171000 08:01 4077463    /home/####/temp/Aptana Studio 3/plugins/org.python.pydev_2.2.4.2011121401/pydev.jar
b3c46000-b3c5e000 r--s 001b6000 08:01 4070151    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/276/1/.cp/css-validator.jar
b3c5e000-b3c61000 ---p 00000000 00:00 0 
b3c61000-b3caf000 rw-p 00000000 00:00 0 
b3caf000-b3cb2000 ---p 00000000 00:00 0 
b3cb2000-b3d00000 rw-p 00000000 00:00 0 
b3d00000-b3e00000 rw-p 00000000 00:00 0 
b3e03000-b3e06000 r--s 00018000 08:01 4077630    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ruby.debug.ui_3.0.2.1322066031.jar
b3e08000-b3e10000 r--s 0004c000 08:01 4077607    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.debug.core_3.6.0.v20100519.jar
b3e16000-b3e19000 ---p 00000000 00:00 0 
b3e19000-b3e67000 rw-p 00000000 00:00 0 
b3e67000-b3e6a000 ---p 00000000 00:00 0 
b3e6a000-b3eb8000 rw-p 00000000 00:00 0 
b3eb8000-b3ebf000 r--s 0003b000 08:01 4076823    /home/####/temp/Aptana Studio 3/plugins/com.aptana.js.debug.ui_3.0.0.1313451701.jar
b3ebf000-b3ef6000 r--p 00000000 08:01 2764824    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-BoldOblique.ttf
b3ef6000-b3f2e000 r--p 00000000 08:01 2764825    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Oblique.ttf
b3f2e000-b3f78000 r--p 00000000 08:01 2757046    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
b3f78000-b3fc7000 r--p 00000000 08:01 2757047    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b3fd2000-b3fe0000 r--s 000a6000 08:01 4076833    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.compare_3.5.101.R36x_v20100929-0800.jar
b3fe0000-b4080000 rw-p 00000000 00:00 0 
b4080000-b4100000 r--p 00000000 08:01 2764822    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-BoldOblique.ttf
b4100000-b4200000 rw-p 00000000 00:00 0 
b4201000-b4209000 r--s 00049000 08:01 4077573    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.metadata_2.0.1.R36x_v20101202.jar
b4209000-b420d000 r--s 00028000 08:01 4076835    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.engine_2.0.1.R36x_v20110201.jar
b420d000-b4212000 rw-p 00000000 00:00 0 
b4212000-b421c000 r--s 0005a000 08:01 4080894    /home/####/temp/Aptana Studio 3/configuration/org.eclipse.osgi/bundles/123/1/.cp/org_apache_httpcomponents_httpcore_4.1.3.jar
b421c000-b4222000 r--s 00036000 08:01 4072686    /home/####/temp/Aptana Studio 3/plugins/com.aptana.parsing_3.0.0.1319578629/libs/jaxen-1.1.2.jar
b422c000-b422f000 r--s 0001c000 08:01 4077645    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.artifact.repository_1.1.1.R36x_v20100901.jar
b4230000-b423b000 r--s 0007d000 08:01 4072524    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ui.editors_3.6.1.r361_v20100825-0800.jar
b423b000-b42bb000 r--p 00000000 08:01 2764823    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
b42bb000-b42be000 r--s 0001c000 08:01 4077257    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ecf.provider.filetransfer_3.1.0.v20100906-1425.jar
b42c3000-b42c8000 rw-p 00000000 00:00 0 
b42c8000-b42d0000 r--s 0009a000 08:01 4077473    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.js_3.0.3.1321635969.jar
b42d1000-b42d3000 rw-s 00000000 08:01 3281064    /tmp/.webkitbrowser.cache/data_3
b42d3000-b42d5000 rw-s 00000000 08:01 3281063    /tmp/.webkitbrowser.cache/data_2
b42d5000-b42d7000 rw-s 00000000 08:01 3281062    /tmp/.webkitbrowser.cache/data_1
b42d7000-b42dc000 r--s 00029000 08:01 4072535    /home/####/temp/Aptana Studio 3/plugins/com.aptana.formatter.ui.epl_3.0.0.1312932604.jar
b42de000-b42e4000 r--s 00044000 08:01 4072380    /home/####/temp/Aptana Studio 3/plugins/com.python.pydev.analysis_2.2.4.2011121401/analysis.jar
b42e4000-b42e7000 r--s 0001a000 08:01 4077480    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.touchpoint.eclipse_2.0.3.R36x_v20101202.jar
b42e8000-b4319000 r--s 00240000 08:01 4077475    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.debug.ui_3.6.3.v20101201_r362.jar
b4319000-b4321000 r--s 00000000 08:01 4198088    /home/####/.local/share/gvfs-metadata/root-e5f6fe0d.log
b4321000-b4325000 r--s 00038000 08:01 4077268    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.html_3.0.3.1322511901.jar
b4329000-b4332000 r--s 00056000 08:01 4077486    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.team.core_3.5.101.R36x_v20110203-1036.jar
b4345000-b434b000 rw-s 00000000 00:10 12524      /dev/shm/com.google.chrome.shmem.libcef_7335378409365025387
b434b000-b435e000 r--s 000dc000 08:01 4079345    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.jface.text_3.6.1.r361_v20100825-0800.jar
b435e000-b4361000 ---p 00000000 00:00 0 
b4361000-b43af000 rw-p 00000000 00:00 0 
b43af000-b43b2000 ---p 00000000 00:00 0 
b43b2000-b4400000 rw-p 00000000 00:00 0 
b4400000-b44f9000 rw-p 00000000 00:00 0 
b44f9000-b4500000 ---p 00000000 00:00 0 
b4501000-b4505000 r--s 00017000 08:01 4072613    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.commands_3.6.0.I20100512-1500.jar
b4505000-b450a000 r--s 00038000 08:01 4077488    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.text_3.5.0.v20100601-1300.jar
b450a000-b450d000 r--s 00173000 08:01 4077628    /home/####/temp/Aptana Studio 3/plugins/com.aptana.browser_3.0.0.1319670764.jar
b4516000-b4522000 r--s 00082000 08:01 4072542    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ui.workbench.texteditor_3.6.1.r361_v20100714-0800.jar
b4522000-b4525000 r--s 00012000 08:01 4069907    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ui.ftp_3.0.0.1315851584.jar
b452a000-b452d000 r--s 00010000 08:01 4079321    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.ruby.formatter.epl_3.0.2.1318551485.jar
b452d000-b4530000 rw-s 00000000 00:04 1671219    /SYSV00000000 (deleted)
b4534000-b4538000 r--s 00021000 08:01 4072409    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.repository_2.0.2.R36x_v20110111-1500.jar
b4538000-b453b000 ---p 00000000 00:00 0 
b453b000-b4589000 rw-p 00000000 00:00 0 
b458a000-b458c000 r--s 0000e000 08:01 4079322    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ui.s3_3.0.0.1312932604.jar
b458c000-b458e000 r--s 00011000 08:01 4076843    /home/####/temp/Aptana Studio 3/plugins/com.aptana.index.core_3.0.0.1319825135.jar
b458e000-b4597000 r--s 000e0000 08:01 4077279    /home/####/temp/Aptana Studio 3/plugins/org.mozilla.rhino_1.7.2.1320796166.jar
b4597000-b459b000 r--s 00037000 08:01 4077609    /home/####/temp/Aptana Studio 3/plugins/com.aptana.core_3.0.4.1323890190.jar
b459b000-b459d000 r--s 0001b000 08:01 4077625    /home/####/temp/Aptana Studio 3/plugins/com.aptana.swt.webkitbrowser_1.0.0.1308865296.jar
b459d000-b459f000 r--s 00006000 08:01 4072650    /home/####/temp/Aptana Studio 3/plugins/com.aptana.index.core.ui_3.0.0.1315934874.jar
b459f000-b45a1000 r--s 00005000 08:01 4077275    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.markdown_3.0.0.1312318673.jar
b45a1000-b45a4000 r--s 00038000 08:01 2239884    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunpkcs11.jar
b45a8000-b45ab000 r--s 00031000 08:01 2239886    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/sunjce_provider.jar
b45ab000-b45b0000 rw-p 00000000 00:00 0 
b45b0000-b45b2000 r--s 00009000 08:01 4077272    /home/####/temp/Aptana Studio 3/plugins/com.aptana.webserver.core_3.0.0.1318522247.jar
b45b2000-b45b5000 r--s 0001e000 08:01 4076784    /home/####/temp/Aptana Studio 3/plugins/beaver_3.0.0.1309394487.jar
b45b5000-b45b7000 r--s 00009000 08:01 4079342    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.haml_3.0.2.1319153036.jar
b45b7000-b45bd000 r--s 00041000 08:01 4072632    /home/####/temp/Aptana Studio 3/plugins/org.python.pydev.core_2.2.4.2011121401/core.jar
b45bd000-b45d0000 r--s 001f4000 08:01 4077612    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.php.epl_3.0.0.1322528867.jar
b45d5000-b45dd000 r--s 0006e000 08:01 4077491    /home/####/temp/Aptana Studio 3/plugins/com.aptana.syncing.ui_3.0.3.1320185576.jar
b45e0000-b45e2000 r--s 00010000 08:01 4077589    /home/####/temp/Aptana Studio 3/plugins/com.aptana.preview_3.0.0.1315523439.jar
b45e5000-b45ea000 r--s 00041000 08:01 4079328    /home/####/temp/Aptana Studio 3/plugins/com.aptana.portal.ui_3.0.0.1322703189.jar
b45ed000-b45f4000 r--s 00048000 08:01 4076803    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ui.io_3.0.0.1323820142.jar
b45f4000-b45f7000 ---p 00000000 00:00 0 
b45f7000-b4645000 rw-p 00000000 00:00 0 
b4645000-b4666000 r--s 00607000 08:01 4077483    /home/####/temp/Aptana Studio 3/plugins/com.ibm.icu_4.2.1.v20100412.jar
b4666000-b4668000 r--s 00013000 08:01 2239841    /usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
b4668000-b4674000 r--s 000b2000 08:01 4072528    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.resources_3.6.1.R36x_v20110131-1630.jar
b4674000-b4700000 r--p 00000000 08:01 2757044    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4700000-b4800000 rw-p 00000000 00:00 0 
b4801000-b4803000 r--s 00006000 08:01 4076816    /home/####/temp/Aptana Studio 3/plugins/com.aptana.portal.ui.eclipse35_3.0.0.1317250778.jar
b4803000-b4805000 r--s 00007000 08:01 4076812    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy.ftp_3.0.3.1321500599.jar
b4805000-b4811000 r--s 000a3000 08:01 4072539    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.common_3.0.3.1323901670.jar
b4812000-b4816000 r--s 0002a000 08:01 4072403    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ui.epl_3.0.0.1322514554.jar
b4816000-b481a000 r--s 00023000 08:01 4076838    /home/####/temp/Aptana Studio 3/plugins/com.aptana.explorer_3.0.0.1316716614.jar
b481d000-b481f000 r--s 00005000 08:01 4077484    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.text_3.0.0.1312318673.jar
b4820000-b4823000 r--s 00014000 08:01 4072527    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.contenttype_3.4.100.v20100505-1235.jar
b4823000-b4825000 r--s 0000e000 08:01 4079341    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy.engineyard_3.0.3.1321500599.jar
b4825000-b4827000 r--s 0000b000 08:01 4076841    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.erb_3.0.3.1319153036.jar
b4828000-b482a000 r--s 00005000 08:01 4077559    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy.epl_3.0.0.1321554449.jar
b482a000-b482c000 r--s 0000a000 08:01 4079306    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy_3.0.3.1317162654.jar
b482c000-b4841000 r--s 000f1000 08:01 4072540    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.jface_3.6.2.M20110210-1200.jar
b4841000-b4843000 r--s 0000b000 08:01 4072387    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.operations_2.0.0.v20100510.jar
b4843000-b4846000 r--s 0000c000 08:01 4079192    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.ui.sdk.scheduler_1.0.0.v20100507-1815.jar
b4846000-b4848000 r--s 00003000 08:01 4072541    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.updatechecker_1.1.101.R36x_v20100823.jar
b4848000-b484b000 r--s 0000e000 08:01 4079320    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.core_2.0.3.R36x_v20110111.jar
b484b000-b484d000 r--s 00016000 08:01 4076810    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.director_2.0.3.R36x_v20101117-1018.jar
b484d000-b48e5000 r--p 00000000 08:01 2757045    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b48e5000-b48e6000 r--s 00000000 08:01 3677555    /var/cache/fontconfig/26de28bc8622bbc1fb67fd234c21975f-le32d4.cache-3
b48e6000-b48e7000 r--s 00000000 08:01 3674541    /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le32d4.cache-3
b48e7000-b48ed000 r--s 00000000 08:01 3674538    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le32d4.cache-3
b48ed000-b48ef000 r--s 00000000 08:01 3674539    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le32d4.cache-3
b48ef000-b48f2000 r--s 00000000 08:01 3674548    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-le32d4.cache-3
b48f2000-b48f8000 r--s 00000000 08:01 3670144    /var/cache/fontconfig/401a5dd6b567794a1d18dd9342dfa604-le32d4.cache-3
b48f8000-b48f9000 r--s 00000000 08:01 3674549    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le32d4.cache-3
b48f9000-b48fc000 r--s 00000000 08:01 3674535    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-le32d4.cache-3
b48fc000-b4900000 r--s 00000000 08:01 3674540    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le32d4.cache-3
b4900000-b4a00000 rw-p 00000000 00:00 0 
b4a01000-b4a02000 r--s 00000000 08:01 3674531    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-le32d4.cache-3
b4a02000-b4a06000 r--s 00000000 08:01 3671922    /var/cache/fontconfig/515ca1ebc4b18308bea979be5704f9db-le32d4.cache-3
b4a06000-b4a0d000 r--s 00000000 08:01 3677219    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
b4a0d000-b4a18000 r--s 00000000 08:01 3674526    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
b4a18000-b4a1b000 r--s 00000000 08:01 3674545    /var/cache/fontconfig/d60319d88cac85ba9e1a07bd06cfbb8c-le32d4.cache-3
b4a1b000-b4a3d000 r--s 00000000 08:01 3677428    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le32d4.cache-3
b4a3d000-b4a45000 r--s 00000000 08:01 3674544    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
b4a45000-b4a46000 r--p 00000000 00:00 0 
b4a46000-b4a47000 r--s 00000000 08:01 4197915    /home/####/.local/share/gvfs-metadata/root
b4a47000-b4a49000 r--s 0000a000 08:01 4076819    /home/####/temp/Aptana Studio 3/plugins/org.radrails.rails.ui_3.0.2.1320689232.jar
b4a49000-b4a4e000 r--s 00040000 08:01 4077606    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.publisher_1.1.2.v20100824-2220.jar
b4a4e000-b4a62000 r--s 00213000 08:01 4077648    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.swt.gtk.linux.x86_3.6.2.v3659b.jar
b4a62000-b4aa9000 r--s 003ab000 08:01 4077477    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ui.workbench_3.6.2.M20110210-1200.jar
b4aa9000-b4aac000 ---p 00000000 00:00 0 
b4aac000-b4afa000 rw-p 00000000 00:00 0 
b4afa000-b4afd000 ---p 00000000 00:00 0 
b4afd000-b4b4b000 rw-p 00000000 00:00 0 
b4b4b000-b4b4e000 ---p 00000000 00:00 0 
b4b4e000-b4b9c000 rw-p 00000000 00:00 0 
b4b9c000-b4b9f000 ---p 00000000 00:00 0 
b4b9f000-b4bed000 rw-p 00000000 00:00 0 
b4bed000-b4bf0000 ---p 00000000 00:00 0 
b4bf0000-b4c3e000 rw-p 00000000 00:00 0 
b4c3e000-b4c41000 ---p 00000000 00:00 0 
b4c41000-b4c8f000 rw-p 00000000 00:00 0 
b4c8f000-b4ca0000 r--s 00108000 08:01 4077642    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.osgi_3.6.2.R36x_v20110210.jar
b4ca0000-b4d00000 rw-s 00000000 00:04 1474605    /SYSV00000000 (deleted)
b4d00000-b4e00000 rw-p 00000000 00:00 0 
b4e00000-b4e01000 r--s 00000000 08:01 3674525    /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le32d4.cache-3
b4e01000-b4e02000 r--s 00000000 08:01 3674533    /var/cache/fontconfig/6a53c69dea097a2d716e069445527da8-le32d4.cache-3
b4e02000-b4e03000 r--s 00000000 08:01 3674529    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le32d4.cache-3
b4e03000-b4e05000 r--s 00000000 08:01 3670079    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le32d4.cache-3
b4e05000-b4e08000 r--s 00000000 08:01 3677621    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le32d4.cache-3
b4e08000-b4e09000 r--s 00004000 08:01 4076813    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.swt_3.6.2.v3659c.jar
b4e0a000-b4e0b000 r--s 00006000 08:01 4072641    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ruby.rake_3.0.0.1318602500.jar
b4e0b000-b4e0e000 r--s 00019000 08:01 4079184    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.filebuffers_3.5.100.v20100520-0800.jar
b4e0e000-b4e12000 r--s 0002b000 08:01 4072523    /home/####/temp/Aptana Studio 3/plugins/com.aptana.theme_3.0.0.1320258654.jar
b4e12000-b4e14000 r--s 0000a000 08:01 4077633    /home/####/temp/Aptana Studio 3/plugins/com.aptana.core.epl_3.0.0.1317316579.jar
b4e14000-b4e16000 r--s 00010000 08:01 4072652    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.runtime_3.6.0.v20100505.jar
b4e16000-b4e19000 r--s 0001b000 08:01 4076815    /home/####/temp/Aptana Studio 3/plugins/org.sat4j.pb_2.2.0.v20100429.jar
b4e19000-b4e1e000 r--s 0002b000 08:01 4079347    /home/####/temp/Aptana Studio 3/plugins/org.sat4j.core_2.2.0.v20100429.jar
b4e1e000-b4e20000 r--s 00001000 08:01 4077634    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.ui.workbench.compatibility_3.2.100.I20100511-0800/compatibility.jar
b4e20000-b4e21000 r--s 00006000 08:01 4076811    /home/####/temp/Aptana Studio 3/plugins/com.aptana.portal.ui.eclipse36_3.0.0.1313011284.jar
b4e21000-b4e22000 r--s 00009000 08:01 4077283    /home/####/temp/Aptana Studio 3/plugins/com.aptana.samples.ui_3.0.0.1322862427.jar
b4e22000-b4e24000 r--s 00014000 08:01 4077560    /home/####/temp/Aptana Studio 3/plugins/com.aptana.projects_3.0.0.1323462907.jar
b4e24000-b4e26000 r--s 0000f000 08:01 4077551    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ui.secureftp_3.0.0.1313195111.jar
b4e27000-b4e29000 r--s 0000b000 08:01 4077571    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.filesystem_1.3.1.R36x_v20100727-0745.jar
b4e29000-b4e2b000 r--s 0000f000 08:01 4079348    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy.heroku_3.0.3.1321500599.jar
b4e2b000-b4e2c000 r--s 00009000 08:01 4077273    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.sass_3.0.2.1322070237.jar
b4e2c000-b4e2d000 r--s 00006000 08:01 4072388    /home/####/temp/Aptana Studio 3/plugins/com.aptana.editor.diff_3.0.0.1317303845.jar
b4e2d000-b4e30000 r--s 00014000 08:01 4079195    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.jobs_3.5.1.R36x_v20100824.jar
b4e30000-b4e33000 r--s 00018000 08:01 4076818    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.metadata.repository_1.1.0.v20100513.jar
b4e33000-b4e34000 r--s 00005000 08:01 4076807    /home/####/temp/Aptana Studio 3/plugins/com.aptana.deploy.capistrano_3.0.3.1321500599.jar
b4e34000-b4e35000 r--s 00002000 08:01 4076826    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.runtime.compatibility.registry_3.3.0.v20100520/runtime_registry_compatibility.jar
b4e35000-b4e39000 r--s 00029000 08:01 4077553    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.registry_3.5.0.v20100503.jar
b4e39000-b4e3b000 r--s 0000f000 08:01 4072520    /home/####/temp/Aptana Studio 3/plugins/com.aptana.ruby.ui_3.0.2.1322528885.jar
b4e3b000-b4e3d000 r--s 00006000 08:01 4069916    /home/####/temp/Aptana Studio 3/plugins/com.aptana.workbench_3.0.0.1312932604.jar
b4e3d000-b4e3e000 r--s 00006000 08:01 4077471    /home/####/temp/Aptana Studio 3/plugins/org.python.pydev.red_core_2.2.4.2011121401/red-core.jar
b4e3e000-b4e3f000 r--s 00002000 08:01 4077474    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.core.filesystem.linux.x86_1.4.0.v20100505-1235.jar
b4e3f000-b4e40000 r--s 00000000 08:01 4200062    /home/####/.local/share/mime/mime.cache
b4e40000-b4e42000 r--s 00007000 08:01 4072537    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.extensionlocation_1.2.0.v20100518.jar
b4e42000-b4eb9000 rw-p 00000000 00:00 0 
b4eb9000-b4ebb000 r--s 00017000 08:01 4076834    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.common_3.6.0.v20100503.jar
b4ebb000-b4ebc000 r--s 00005000 08:01 4072530    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.garbagecollector_1.0.100.v20100503.jar
b4ebc000-b4ebd000 r--s 00007000 08:01 4079186    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.p2.directorywatcher_1.0.203.R36x_v20101220.jar
b4ebd000-b4ec3000 r--s 000fc000 08:01 2239897    /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
b4ec3000-b4ec6000 r--s 0007d000 08:01 2239837    /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
b4ec6000-b4ecf000 r--s 00065000 08:01 2377733    /usr/share/java/gnome-java-bridge.jar
b4ecf000-b4ed0000 ---p 00000000 00:00 0 
b4ed0000-b4f50000 rw-p 00000000 00:00 0 
b4f50000-b4f53000 ---p 00000000 00:00 0 
b4f53000-b4fa1000 rw-p 00000000 00:00 0 
b4fa1000-b4fa4000 ---p 00000000 00:00 0 
b4fa4000-b5022000 rw-p 00000000 00:00 0 
b5022000-b5025000 ---p 00000000 00:00 0 
b5025000-b5073000 rw-p 00000000 00:00 0 
b5073000-b5076000 ---p 00000000 00:00 0 
b5076000-b50c4000 rw-p 00000000 00:00 0 
b50c4000-b50c7000 ---p 00000000 00:00 0 
b50c7000-b5115000 rw-p 00000000 00:00 0 
b5115000-b5116000 ---p 00000000 00:00 0 
b5116000-b5196000 rw-p 00000000 00:00 0 
b5196000-b5198000 r--s 0001d000 08:01 2239846    /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
b5198000-b519d000 r--s 00045000 08:01 2239857    /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
b519d000-b51d0000 rw-p 00000000 00:00 0 
b51d0000-b535f000 r--s 038c4000 08:01 2239832    /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
b535f000-b5387000 rw-p 00000000 00:00 0 
b5387000-b53ed000 rw-p 00000000 00:00 0 
b53ed000-b5401000 rw-p 00000000 00:00 0 
b5401000-b5498000 rw-p 00000000 00:00 0 
b5498000-b54a2000 rw-p 00000000 00:00 0 
b54a2000-b54ed000 rw-p 00000000 00:00 0 
b54ed000-b5502000 rw-p 00000000 00:00 0 
b5502000-b5598000 rw-p 00000000 00:00 0 
b5598000-b55b3000 rw-p 00000000 00:00 0 
b55b3000-b5618000 rw-p 00000000 00:00 0 
b5618000-b5640000 rw-p 00000000 00:00 0 
b5640000-b56a4000 rw-p 00000000 00:00 0 
b56a4000-b5d7c000 rwxp 00000000 00:00 0 
b5d7c000-b76a4000 rw-p 00000000 00:00 0 
b76a4000-b76ac000 rw-s 00000000 08:01 3281053    /tmp/hsperfdata_####/1551
b76ac000-b76ad000 rw-p 00000000 00:00 0 
b76ad000-b76ae000 r--p 00000000 00:00 0 
b76ae000-b76ed000 r--p 00000000 08:01 1973924    /usr/lib/locale/en_ZA.utf8/LC_CTYPE
b76ed000-b780b000 r--p 00000000 08:01 1973923    /usr/lib/locale/en_ZA.utf8/LC_COLLATE
b780b000-b780d000 rw-p 00000000 00:00 0 
b780d000-b780f000 r--s 0000a000 08:01 4077588    /home/####/temp/Aptana Studio 3/plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar
b780f000-b7812000 r--s 0000f000 08:01 2239889    /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
b7812000-b7813000 r--p 00000000 08:01 1974171    /usr/lib/locale/en_ZA.utf8/LC_NUMERIC
b7813000-b7814000 r--p 00000000 08:01 1973831    /usr/lib/locale/en_ZA.utf8/LC_TIME
b7814000-b7815000 r--p 00000000 08:01 1974224    /usr/lib/locale/en_ZA.utf8/LC_MONETARY
b7815000-b7816000 r--p 00000000 08:01 2097328    /usr/lib/locale/en_ZA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7816000-b7817000 r--p 00000000 08:01 1973851    /usr/lib/locale/en_ZA.utf8/LC_PAPER
b7817000-b7818000 r--p 00000000 08:01 1978145    /usr/lib/locale/en_ZA.utf8/LC_NAME
b7818000-b7819000 r--p 00000000 08:01 1978146    /usr/lib/locale/en_ZA.utf8/LC_ADDRESS
b7819000-b781a000 r--p 00000000 08:01 1974228    /usr/lib/locale/en_ZA.utf8/LC_TELEPHONE
b781a000-b781b000 r--p 00000000 08:01 1973926    /usr/lib/locale/en_ZA.utf8/LC_MEASUREMENT
b781b000-b7822000 r--s 00000000 08:01 1972692    /usr/lib/gconv/gconv-modules.cache
b7822000-b7823000 r--p 00000000 08:01 1978147    /usr/lib/locale/en_ZA.utf8/LC_IDENTIFICATION
b7823000-b7825000 rw-p 00000000 00:00 0 
bf918000-bf91b000 ---p 00000000 00:00 0 
bf91c000-bf968000 rw-p 00000000 00:00 0          [stack]

VM Arguments:
jvm_args: -Xms40m -Xmx512m -Declipse.p2.unsignedPolicy=allow -Declipse.log.size.max=10000 -Declipse.log.backup.max=5 -Djava.awt.headless=true -XX:MaxPermSize=256m 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=####
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/i386/client:/usr/lib/jvm/java-6-openjdk/jre/lib/i386:
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3ea370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3ea370], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30d390], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x30ca40], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x30f5b0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.24 1.29 0.82

/proc/meminfo:
MemTotal:        1544040 kB
MemFree:          497636 kB
Buffers:           87364 kB
Cached:           411716 kB
SwapCached:            0 kB
Active:           593120 kB
Inactive:         393316 kB
Active(anon):     487812 kB
Inactive(anon):    15196 kB
Active(file):     105308 kB
Inactive(file):   378120 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        663496 kB
HighFree:           1116 kB
LowTotal:         880544 kB
LowFree:          496520 kB
SwapTotal:       3227640 kB
SwapFree:        3227640 kB
Dirty:               184 kB
Writeback:             0 kB
AnonPages:        487352 kB
Mapped:           123148 kB
Shmem:             15656 kB
Slab:              28064 kB
SReclaimable:      19232 kB
SUnreclaim:         8832 kB
KernelStack:        2512 kB
PageTables:         7720 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3999660 kB
Committed_AS:    1782564 kB
VmallocTotal:     122880 kB
VmallocUsed:       31716 kB
VmallocChunk:      79356 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       24568 kB
DirectMap4M:      884736 kB


CPU:total 1 (1 cores per cpu, 2 threads per core) family 15 model 2 stepping 9, cmov, cx8, fxsr, mmx, sse, sse2, ht

Memory: 4k page, physical 1544040k(497636k free), swap 3227640k(3227640k free)

vm_info: OpenJDK Client VM (19.0-b09) for linux-x86 JRE (1.6.0_20-b20), built on Nov  8 2011 17:28:56 by "buildd" with gcc 4.4.3

time: Wed Jan 18 21:20:39 2012
elapsed time: 632 seconds

---

### Post by BC59 on 2012-01-18
Why don't you try installing Oracle Java 7?

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-jdk7-installer
```

---

### Post by zyrex on 2012-01-18
I gave that a try, here is the result:


#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=6742, tid=3078768320
#
# JRE version: 7.0_02-b13
# Java VM: Java HotSpot(TM) Client VM (22.0-b10 mixed mode linux-x86 )
# Problematic frame:
# C  0x00000000
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.sun.com/bugreport/crash.jsp](http://bugreport.sun.com/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x09774000):  JavaThread "main" [_thread_in_native, id=6742, stack(0xbf975000,0xbf9c5000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x0ac8b928, EBX=0x7c675a5c, ECX=0x0ab53618, EDX=0x0ac74088
ESP=0xbf9bfbcc, EBP=0xbf9bfd18, ESI=0x00000005, EDI=0x00000001
EIP=0x00000000, EFLAGS=0x00210206, CR2=0x00000000

Top of Stack: (sp=0xbf9bfbcc)
0xbf9bfbcc:   7b6fd111 0ac74088 0ab53618 00000000
0xbf9bfbdc:   77732f68 73616c66 61632e68 65762362
0xbf9bfbec:   6f697372 2c373d6e 2c302c30 0039bf18
0xbf9bfbfc:   0001000b 00200000 7b478000 bf9bfc38
0xbf9bfc0c:   7b478000 7b45b000 bf9bfd0b 00000003
0xbf9bfc1c:   00000032 7c675a5c bf9bfc20 00000001
0xbf9bfc2c:   bf9bfd18 37e637fd dfb08a74 00000000
0xbf9bfc3c:   7be3dec0 7c6b2850 7b45b060 00000001 

Instructions: (pc=0x00000000)
0xffffffe0:   

Register to memory mapping:

EAX=0x0ac8b928 is an unknown value
EBX=0x7c675a5c: <offset 0x101aa5c> in /usr/lib/adobe-flashplugin/libflashplayer.so at 0x7b65b000
ECX=0x0ab53618 is an unknown value
EDX=0x0ac74088 is an unknown value
ESP=0xbf9bfbcc is pointing into the stack for thread: 0x09774000
EBP=0xbf9bfd18 is pointing into the stack for thread: 0x09774000
ESI=0x00000005 is an unknown value
EDI=0x00000001 is an unknown value

---

### Post by BC59 on 2012-01-18
> To enable core dumping, try "ulimit -c unlimited" before starting Java again
I'm not sure how you can do it, look here:
[http://splunk-base.splunk.com/answers/13313/how-to-tune-ulimit-on-my-server](http://splunk-base.splunk.com/answers/13313/how-to-tune-ulimit-on-my-server)

---

