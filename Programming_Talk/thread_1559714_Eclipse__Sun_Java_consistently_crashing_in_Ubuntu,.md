---
title: "Eclipse / Sun Java consistently crashing in Ubuntu, fine in Windows"
date: 2010-08-23
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-23
I am developing a program in Eclipse and it runs fine on my windows laptop running Sun Java Environment.  On Ubuntu, it recently started crashing frequently.  By recently, I mean within the past week.  Below is the bottom part of the error log.  I am running Ubuntu 64-bit on Java JDK 64-bit and Eclipse 64-bit.  I think my Java JDK became corrupt, what's the best way to reinstall?

Here's the error log:

VM Arguments:
jvm_args: -Xmx6048m -Djava.library.path=/home/boxer/workspace/Puller -Dfile.encoding=UTF-8 
java_command: com.rapidminer.gui.RapidMinerGUI
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=boxer
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/server:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/../lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64:/usr/lib64/xulrunner-addons
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x70ffd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x70ffd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5d8cf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x5d8cf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5d8cf0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5db510], sa_mask[0]=0x00000004, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5db260], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:squeeze/sid

uname:Linux 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:4.46 4.71 4.71

CPU:total 4 (4 cores per cpu, 1 threads per core) family 6 model 23 stepping 6, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1

Memory: 4k page, physical 8159768k(1630940k free), swap 2441840k(2441840k free)

vm_info: Java HotSpot(TM) 64-Bit Server VM (16.3-b01) for linux-amd64 JRE (1.6.0_20-b02), built on Apr 12 2010 13:57:11 by "java_re" with gcc 3.2.2 (SuSE Linux)

time: Mon Aug 23 19:17:05 2010
elapsed time: 224 seconds

---

### Post by kahumba on 2010-08-23
If I were you I wouldn't even bother figuring out I'd just dump eclipse unless I am forced to use it. And btw sorry for offtopic but I really think it would be a better solution, especially since you're doing Java development (not C++).

---

### Post by SNYP40A1 on 2010-08-24
> **kahumba said:**
> If I were you I wouldn't even bother figuring out I'd just dump eclipse unless I am forced to use it. And btw sorry for offtopic but I really think it would be a better solution, especially since you're doing Java development (not C++).

Dump Eclipse?  I love Eclipse, it's the best IDE I have found so far.  What would you use?  I don't think it's Eclipse, it's not runtime error or an Exception, Java itself literally crashes.  That's not supposed to ever happen.

Update: I have the same problem with OpenJDK, so it's probably not Sun JDK exclusively.  Note, I updated my system's memory last weekend.  Is it possible that the memory could be causing this type of error without causing any other noticeable problem w/ rest of my system?  I ran memcheck twice and all tests passed.

> 
VM Arguments:
jvm_args: -Xmx6048m -Djava.library.path=/home/boxer/workspace/Puller -Dfile.encoding=UTF-8 
java_command: com.rapidminer.gui.RapidMinerGUI
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=boxer
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/server:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64:/usr/lib/jvm/java-6-sun-1.6.0.20/jre/../lib/amd64:/usr/lib64/xulrunner-addons
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x6c1f70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x6c1f70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x58ca00], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGXFSZ: [libjvm.so+0x58ca00], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x58ca00], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x58c150], sa_mask[0]=0x00000004, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x58e840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x58e840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x58e840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x58e840], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:4.57 4.71 4.39

CPU:total 4 (4 cores per cpu, 1 threads per core) family 6 model 23 stepping 6, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1

Memory: 4k page, physical 8159768k(1274372k free), swap 2441840k(2441840k free)

vm_info: OpenJDK 64-Bit Server VM (16.0-b13) for linux-amd64 JRE (1.6.0_18-b18), built on Jul 26 2010 23:34:55 by "buildd" with gcc 4.4.3

time: Mon Aug 23 21:23:31 2010
elapsed time: 149 seconds


---

### Post by Some Penguin on 2010-08-24
It's almost certainly not the only problem (Eclipse has problems... I've seen it segfault before it even brings up a single window!), but it bothers me vaguely when I see that your LD_LIBRARY_PATH has both OpenJDK and Sun JDK directories.  That would seem to be asking for trouble.

---

### Post by Queue29 on 2010-08-24
Why did your OS change between those two error logs?

---

### Post by kahumba on 2010-08-24
Open your project with NetBeans and if it doesn't crash then eclipse/swt is to blame.

---

### Post by SNYP40A1 on 2010-08-24
> **Some Penguin said:**
> It's almost certainly not the only problem (Eclipse has problems... I've seen it segfault before it even brings up a single window!), but it bothers me vaguely when I see that your LD_LIBRARY_PATH has both OpenJDK and Sun JDK directories.  That would seem to be asking for trouble.

It has not caused a problem in the past.  LD_LIBRARY_PATH specifies the path to both JVMs (Sun Java and OpenJDK), but I assume that Eclipse would only load the project JVM.

> Why did your OS change between those two error logs?

First log was taken with Sun Java JDK.  Second was with OpenJDK.  I don't know why the OS changed.  That's an interesting observation.

I ran memcheck86 over night.  It ran for 8 hours with no issues.  Is there a better way to stress-test my system for errors?  I also run a distributed computing project so the CPU is pegged at 100% all the time and my system has been stable, not sure if Linux would blue-screen-of-death.  If I have memory issues, how would Ubuntu behave?  Would it crash?  Would things freeze up?  I assume that these issues would not go mostly silently unnoticed.

---

### Post by SNYP40A1 on 2010-08-26
Update, I don't think it's actually the memory or Java.  I think my CPU was getting a bit too hot.  I turned up the fan and have not see the error since.

---

### Post by GregBrannon on 2010-08-26
Ahhhh . . . a hardware problem turned into a "my IDE is better than yours" debate.  Some can't resist the opportunity.

Glad you got it figured out.

Mark it solved?

---

