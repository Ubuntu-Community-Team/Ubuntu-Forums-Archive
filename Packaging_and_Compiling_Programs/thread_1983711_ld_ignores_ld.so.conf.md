---
title: "ld ignores ld.so.conf?"
date: 2012-05-20
forum: Packaging and Compiling Programs
---

### Post by PeterP24 on 2012-05-20
Hi,

I am having troubles with setting /etc/ld.so.conf in order to add a directory to the default library search path. 

More specifically, I have already compiled a very simple shared library (libhello.so) which I previously tested that it works by placing it in /usr/local/lib and running ldconfig, and compiling the program with gcc main.c -lhello -o myprogr.

Everything worked well. Now, I try to make it run from a custom directory which I previously added to /etc/ld.so.conf. I copy the library into that custom directory and than I run ldconfig. 

I know ldconfig works, because the real name of the lib is libhello.so.1 and after ldconfig, in that custom directory it appears a link file (libhello.so). Moreover, ldconfig -v | grep /pathtomycustomdir reports that the custom  directory was considered.
But when I run gcc main.c -lhello -o myprogr, the linker complains it cannot find libhello. I have to give the -Ldir option in order to compile my program. My guess is that ld ignores my entry in ld.so.conf.

What I tried so far:
*adding a path to the custom directory entry directly into /etc/ld.so.conf
*adding a file in /etc/ld.so.conf.d directory with the .conf and containing the path to that custom directory.

Can I set ld somehow in order to read the ld.so.conf?

---

### Post by MadCow108 on 2012-05-21
ld.so.conf has nothing to do with the compile time linker (ld)
it only controls the runtime dynamic linker (ld.so)

so you always need to set -Ldir or LD_RUN_PATH=dir when linking from non standard folders

---

