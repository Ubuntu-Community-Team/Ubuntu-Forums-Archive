---
title: "libselinux.so.1 Causes Segfault?"
date: 2008-04-21
forum: Programming Talk
---

### Post by GenuineXP on 2008-04-21
A project of mine refuses to quit cleanly on my Ubuntu Hardy box (x86). Every time the program ends, I get a segfault. After poking around with gdb, I got this output.

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7c476c0 (LWP 7211)]
0xb6883f74 in ?? () from /lib/libselinux.so.1
```

I'm not entirely sure what this means, but it seems to indicate that libselinux.so.1 is the source of the segfault. If this is right, what can I do to prevent it? What's going on here?

On another system running Ubuntu Gutsy, there are no errors when the program ends. I tried compiling cleanly on both machines with the same results: Hardy gets a sigsegv, and Gutsy closes cleanly.

Any ideas? Thanks!

---

### Post by Zugzwang on 2008-04-22
Although the segfault seems to occur in libselinux, this does not necessarily mean that it's libselinux's fault (but due to the purpose of selinux isn't unlikely either). You might for example be calling a function with an invalid pointer that is calling a function that is calling a function, ...., that is calling a function that is intercepted by libselinux.

I assume that you're using C or C++? If so, try using valgrind (using the tool cachegrind if I remember correctly) on your application. This is not unlikely to detect such cases.

---

### Post by GenuineXP on 2008-04-22
I've already given valgrind a try on both machines with no errors or warnings (as far as I can tell).

Debugging is difficult in general. I'm not all that experienced with gdb, but I've run into issues because my program links dynamically to a library I've written which in turn dynamically loads another shared object using the Unix ld functions. gdb complains about not being able to grab/find threads, and I think this has something to do with loading the shared object at runtime.

Any more suggestions? Thanks for the help! I appreciate it.

---

### Post by stroyan on 2008-04-22
You could get the source for libselinux1 to build and install a debug version.
That would give gdb a lot of help with examining the crash.
```

$ mkdir libselinux1_source
$ cd libselinux1_source
$ apt-get source libselinux1
$ sudo apt-get build-dep libselinux1
$ cd libselinux-2.0.15
$ DEB_BUILD_OPTIONS="debug noopt nostrip" debuild -i -us -uc -b
$ sudo dpkg -i ../libselinux1_2.0.15-2ubuntu1_i386.deb

```

---

### Post by uzadow on 2008-06-07
Hi,

what libraries does your program link to (use ldd)? I'm asking because libavg ([www.libavg.de](www.libavg.de)) exits with a segfault in libselinux.so.1 as well. Here's the relevant part of the valgrind report:

==4503== Process terminating with default action of signal 11 (SIGSEGV)
==4503==  Access not within mapped region at address 0x50
==4503==    at 0x68AEF74: (within /lib/libselinux.so.1)
==4503==    by 0x68A864D: (within /lib/libselinux.so.1)
==4503==    by 0x68A10FF: (within /lib/libselinux.so.1)
==4503==    by 0x68B07BB: (within /lib/libselinux.so.1)
==4503==    by 0x400DFDE: (within /lib/ld-2.7.so)
==4503==    by 0x40AC083: exit (in /lib/tls/i686/cmov/libc-2.7.so)
==4503==    by 0x4094457: (below main) (in /lib/tls/i686/cmov/libc-2.7.so)
==4503== 

Recompiling selinux as described here:

[https://www.libavg.de/wiki/index.php/Libavg_on_Ubuntu](https://www.libavg.de/wiki/index.php/Libavg_on_Ubuntu)

avoids the segfault - but that's only a workaround, not a fix.

Launchpad bugreport with a complete description:

[https://bugs.launchpad.net/ubuntu/+source/libselinux/+bug/237156](https://bugs.launchpad.net/ubuntu/+source/libselinux/+bug/237156)

---

