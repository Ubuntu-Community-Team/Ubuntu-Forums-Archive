---
title: "Problems with Period04"
date: 2018-09-14
forum: New to Ubuntu
---

### Post by quei on 2018-09-14
Hi everyone,

I am quite new to everything about coding, but unfortunately I chosed to do my bachelor thesis working on a data analysis where I should use this program, Period04, or at least it would be very useful, unless from the fact that I couldn't manage to make it work.
At first I downloaded the original version from the official page of the program, but even if I managed to install it and open it without problems, it could not exactly read the data, and was therefore useless
I contacted the creator of the program, who sent me a new version of it and, when I had problems open this new version of it, kindly helped me and suggested me to update my java JRE; unfortunately , I still get an error while trying to open it, which is:
jackquei@jackquei-thinkpad:~/Period04$ sh period04
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/jackquei/Period04/libperiod04.so: libboost_regex.so.1.61.0: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(java.base@9-internal/Native Method)
    at java.lang.ClassLoader.loadLibrary0(java.base@9-internal/ClassLoader.java:2347)
    at java.lang.ClassLoader.loadLibrary(java.base@9-internal/ClassLoader.java:2264)
    at java.lang.Runtime.loadLibrary0(java.base@9-internal/Runtime.java:874)
    at java.lang.System.loadLibrary(java.base@9-internal/System.java:1807)
    at Period04.<clinit>(Period04.java:33)

I even tried to reinstall and run the old version of the program with the new version of java, but I now have a problem while trying to open the program:
jackquei@jackquei-thinkpad:~/Period04$ sh period04
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007feb0331c009, pid=15503, tid=15504
#
# JRE version: OpenJDK Runtime Environment (9.0) (build 9-internal+0-2016-04-14-195246.buildd.src)
# Java VM: OpenJDK 64-Bit Server VM (9-internal+0-2016-04-14-195246.buildd.src, mixed mode, tiered, compressed oops, g1 gc, linux-amd64)
# Problematic frame:
# C  [libjava.so+0x1d009]  JNU_GetEnv+0x19
#
# Core dump will be written. Default location: Core dumps may be processed with "/usr/share/apport/apport %p %s %c %d %P" (or dumping to /home/jackquei/Period04/core.15503)
#
# An error report file with more information is saved as:
# /home/jackquei/Period04/hs_err_pid15503.log
#
# If you would like to submit a bug report, please visit:
#   [http://bugreport.java.com/bugreport/crash.jsp](http://bugreport.java.com/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)

I anyone has any kind of hints, I would gladly listen to it!

Thanks in advance,
Jack

---

