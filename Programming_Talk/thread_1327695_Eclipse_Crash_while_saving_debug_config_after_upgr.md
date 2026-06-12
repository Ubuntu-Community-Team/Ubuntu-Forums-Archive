---
title: "Eclipse Crash while saving debug config after upgrade"
date: 2009-11-15
forum: Programming Talk
---

### Post by TennTux on 2009-11-15
While using eclipse under Jaunty I had no problems.

However, after upgrading to Ubuntu Karmic Koala (9.10), Eclipse Galileo (3.5.1) and sun-java6 I found that when I tried to enter a new debug configuration for my existing project, I would crash. I have tried a number of things to see if I could fix or narrow down the problem. At this point I will not take you through each step. If need be, I will fill that in later. For now I will summerize where I am.

I have uninstalled (Clean) and reinstalled the following packages.
> eclipse-jdt
eclipse-platform
eclipse-platform-data
eclipse-plugin-cvs
eclipse-rcp
sun-java6-bin (see note below)
sun-java6-doc
sun-java6-fonts
sun-java6-jdk
sun-java6-jre
sun-java6-source


NOTE1: The uninstall of sun-java6-* required the uninstall of a number of other packages that I uninstalled and reinstalled, though, I believe they have no relevance to eclipse. ie. openoffic.org.

NOTE2: Installing sun-java6-* packages places them in in /usr/lib/jvm/java-6-sun/* and /usr/lib/jvm/java-6-sun-1.6.0.15 directories. The command > /usr/lib/jvm/java-6-sun/bin/java -version give the following result:
> java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

NOTE3: After receiving warnings and reviewing eclipse documentation I changed the menu command to the following:
> eclipse -vm /usr/lib/jvm/java-6-sun/bin/java

NOTE4: After noticing that "java -version" was not giving me the correct version I performed a > sudo update-java-alternatives -s java-6-sun . (If NOTE4 had been found first NOTE3 may not have been necessary but I did so I'm tellin ya).

I removed the entire ~/workspace and ~/.eclipse directories (just to be sure).

Then I performed the following:

Start Eclipse with a brand new workspace directory
Select Workbench
Create a new "Test" project.
Added a simple java.swing.JFrame derived class.
Built it successfully without warnings or errors.
Selected the debug dropdown icon and chose "Debug Configurations"
Added a new Application configuration and chose "Close" (not Debug).
Eclipse disappeared without a trace.

The following is extracted from the crash file hs_err_pid2810.log
```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb43fd856, pid=2810, tid=3068435312
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Client VM (14.1-b02 mixed mode, sharing linux-x86 )
# Problematic frame:
# C  [libpango-1.0.so.0+0x23856]  pango_layout_new+0x36
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x08450c00):  JavaThread "main" [_thread_in_native, id=2811, stack(0xb6df9000,0xb6e4a000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x0000000c

Registers:
EAX=0x00000000, EBX=0xb4420ff4, ECX=0x085aa678, EDX=0x00000000
ESP=0xb6e45520, EBP=0xb6e45548, ESI=0x09550e00, EDI=0x09366fb8
EIP=0xb43fd856, CR2=0x0000000c, EFLAGS=0x00010282

Top of Stack: (sp=0xb6e45520)
0xb6e45520:   0881d0c0 00000000 b6e45598 00000000
0xb6e45530:   08be2fb8 b7856ff4 b78583a0 b3ea8ff4
0xb6e45540:   094e7168 09366fb8 b6e45598 b3cd9047
0xb6e45550:   09550e00 094a1588 b45aa788 00000001
0xb6e45560:   b6e45704 094a1588 09399168 b3ea8ff4
0xb6e45570:   00000000 09054c80 00000000 08be4b80
0xb6e45580:   00000008 b45a9ff4 b3cbea3b b3ea8ff4
0xb6e45590:   094e7168 095a1178 b6e45728 b3cda77b 

Instructions: (pc=0xb43fd856)
0xb43fd846:   c7 44 24 04 00 00 00 00 89 04 24 e8 16 6d fe ff
0xb43fd856:   89 70 0c 89 c7 89 34 24 e8 49 6d fe ff 89 f8 8b 

Stack: [0xb6df9000,0xb6e4a000],  sp=0xb6e45520,  free space=305k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libpango-1.0.so.0+0x23856]  pango_layout_new+0x36

...

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x08621800 JavaThread "org.eclipse.jdt.internal.ui.text.JavaReconciler" daemon [_thread_blocked, id=2905, stack(0xb22fc000,0xb234d000)]
  0x08ded800 JavaThread "Bundle File Closer" daemon [_thread_blocked, id=2901, stack(0xb229f000,0xb22f0000)]
  0x089dd000 JavaThread "[ThreadPool Manager] - Idle Thread" daemon [_thread_blocked, id=2870, stack(0xb2a32000,0xb2a83000)]
  0x08c2bc00 JavaThread "Worker-4" [_thread_blocked, id=2867, stack(0xb2a9c000,0xb2aed000)]
  0x08ba7400 JavaThread "Worker-2" [_thread_blocked, id=2865, stack(0xb2f6f000,0xb2fc0000)]
  0x085a8400 JavaThread "Worker-1" [_thread_blocked, id=2864, stack(0xb2fc0000,0xb3011000)]
  0x08a29400 JavaThread "Java indexing" daemon [_thread_blocked, id=2827, stack(0xb2d20000,0xb2d71000)]
  0x086d3400 JavaThread "Worker-0" [_thread_blocked, id=2824, stack(0xb3572000,0xb35c3000)]
  0x087e3400 JavaThread "[Timer] - Main Queue Handler" daemon [_thread_blocked, id=2823, stack(0xb3521000,0xb3572000)]
  0x08629800 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=2821, stack(0xb35fd000,0xb364e000)]
  0x085f1c00 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=2820, stack(0xb364e000,0xb369f000)]
  0x085e0800 JavaThread "State Data Manager" daemon [_thread_blocked, id=2819, stack(0xb369f000,0xb36f0000)]
  0x0848e800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=2817, stack(0xb4689000,0xb46da000)]
  0x0848b400 JavaThread "CompilerThread0" daemon [_thread_blocked, id=2816, stack(0xb46da000,0xb475b000)]
  0x08489c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=2815, stack(0xb475b000,0xb47ac000)]
  0x08478000 JavaThread "Finalizer" daemon [_thread_blocked, id=2814, stack(0xb49bb000,0xb4a0c000)]
  0x08476800 JavaThread "Reference Handler" daemon [_thread_blocked, id=2813, stack(0xb4a0c000,0xb4a5d000)]
=>0x08450c00 JavaThread "main" [_thread_in_native, id=2811, stack(0xb6df9000,0xb6e4a000)]

Other Threads:
  0x08474c00 VMThread [stack: 0xb4a5d000,0xb4ade000] [id=2812]
  0x08490000 WatcherThread [stack: 0xb4608000,0xb4689000] [id=2818]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 5760K, used 4968K [0x730c0000, 0x73700000, 0x74470000)
  eden space 5120K,  97% used [0x730c0000, 0x7359a0f0, 0x735c0000)
  from space 640K,   0% used [0x73660000, 0x73660000, 0x73700000)
  to   space 640K,   0% used [0x735c0000, 0x735c0000, 0x73660000)
 tenured generation   total 76248K, used 29293K [0x74470000, 0x78ee6000, 0x830c0000)
   the space 76248K,  38% used [0x74470000, 0x7610b588, 0x7610b600, 0x78ee6000)
 compacting perm gen  total 47360K, used 47160K [0x830c0000, 0x85f00000, 0x930c0000)
   the space 47360K,  99% used [0x830c0000, 0x85ece270, 0x85ece400, 0x85f00000)
    ro space 8192K,  74% used [0x930c0000, 0x936ba2a8, 0x936ba400, 0x938c0000)
    rw space 12288K,  59% used [0x938c0000, 0x93fd7878, 0x93fd7a00, 0x944c0000)

Dynamic libraries:
08048000-08052000 r-xp 00000000 08:21 16024370   /usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin/java
08052000-08053000 rwxp 00009000 08:21 16024370   /usr/lib/jvm/java-6-sun-1.6.0.15/jre/bin/java
0844a000-09689000 rwxp 00000000 00:00 0          [heap]

...

VM Arguments:
jvm_args: -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=//usr/share/eclipse/dropins -Xms40m -Xmx256m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=//usr/share/eclipse/dropins -XX:MaxPermSize=256m 
java_command: /usr/lib/eclipse/plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar -os linux -ws gtk -arch x86 -showsplash -launcher /usr/lib/eclipse/eclipse -name Eclipse --launcher.library /usr/lib/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.200.v20090520/eclipse_1207.so -startup /usr/lib/eclipse/plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar -exitdata 158012 -Xms64m -Xmx320m -XX:MaxPermSize=320m -vm /usr/lib/jvm/java-6-sun/bin/java -vmargs -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=//usr/share/eclipse/dropins -Xms40m -Xmx256m -Dorg.eclipse.equinox.p2.reconciler.dropins.directory=//usr/share/eclipse/dropins -XX:MaxPermSize=256m -jar /usr/lib/eclipse/plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/home/sadwrn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=sadwrn
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.15/jre/../lib/i386:/usr/lib/xulrunner-1.9.1.5:/usr/lib/xulrunner-addons
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3fc2e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3fc2e0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x325ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGXFSZ: [libjvm.so+0x325ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x325ea0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x328a90], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x3287c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x3287c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x3287c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x3287c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
libc:glibc 2.10.1 NPTL 2.10.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.02 0.12 0.09

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 2 stepping 9, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1025912k(43412k free), swap 9767512k(9767512k free)

vm_info: Java HotSpot(TM) Client VM (14.1-b02) for linux-x86 JRE (1.6.0_15-b03), built on Jul  2 2009 16:04:51 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sun Nov 15 16:38:24 2009
elapsed time: 622 seconds


```

I have reviewed the recent treads with Eclipse and Java which I believe I have incorporated into what I have done.

So....         Any suggestions on where do I go from here?

---

### Post by TennTux on 2009-11-19
bump

Given the over whelming response I'm getting, ;-), I'm starting to wonder if this was the correct / best forum to post this to.

If people don't have the answer, could I get some suggestions on which forum would be best? And are there changes to the post I should make to better explain my issue?

Thanks in advance.

---

### Post by TennTux on 2009-12-04
I have tried to work through this issue as time permits, but, have not made progress.

I was able to not only remove the installed package and clean the config files but remove the install packages from the cache. Something that was not happening before. This did not help.

I currently have sun-java6-jdk and sun-java6-jre installed but not gnu java. Does anybody know if eclipse requires gnu jre for the environment to run eventhough it's not listed as a dependancy? I'm not sure why I'm crashing in native code while running eclipse. (Since I have done this with a new project even before entering a source file, I believe it's not my code but eclipse's or something it depends on.)

---

### Post by the_king_men on 2009-12-04
I had a lot of trouble with it too

Quote from another forum : 

Finally the solution required to disable the Assistive Technologies (System -> Preferences -> Assistive Technologies). After that everything works ok.

..... What are they doing with the accessibility...

Ref : 
[http://www.len.ro/2009/11/eclipse-in-ubuntu-karmic/](http://www.len.ro/2009/11/eclipse-in-ubuntu-karmic/)
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/460104](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/460104)
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/469375](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/469375)

---

### Post by TennTux on 2009-12-06
> **the_king_men said:**
> I had a lot of trouble with it too

Quote from another forum : 

Finally the solution required to disable the Assistive Technologies (System -> Preferences -> Assistive Technologies). After that everything works ok.



I thank you sooo much. I bow to your superior/prior torment. I tried it and it worked first time.

---

