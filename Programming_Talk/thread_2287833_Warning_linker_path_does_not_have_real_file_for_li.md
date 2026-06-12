---
title: "Warning: linker path does not have real file for library -lstdc++."
date: 2015-07-22
forum: Programming Talk
---

### Post by newcfd on 2015-07-22
I am installing a code and got the following warnings from libtool:

*** Warning: linker path does not have real file for library -lstdc++.
*** I have the capability to make that library automatically link in when
*** you link to this library.  But I can only do this if you have a
*** shared version of the library, which you do not appear to have
*** because I did check the linker path looking for a file starting
*** with libstdc++ and none of the candidates passed a file format test
*** using a file magic. Last file checked: /usr/lib/x86_64-linux-gnu//libstdc++.so.6.0.21

*** Warning: linker path does not have real file for library -lpthread.
*** I have the capability to make that library automatically link in when
*** you link to this library.  But I can only do this if you have a
*** shared version of the library, which you do not appear to have
*** because I did check the linker path looking for a file starting
*** with libpthread and none of the candidates passed a file format test
*** using a file magic. Last file checked: /lib/x86_64-linux-gnu//libpthread-2.19.so
*** The inter-library dependencies that have been dropped here will be
*** automatically added whenever a program is linked with this library
*** or is declared to -dlopen it.

Both libraries are available.
/usr/lib/gcc/x86_64-linux-gnu/4.8/libstdc++.a
/usr/lib/gcc/x86_64-linux-gnu/4.8/libstdc++.so
/usr/lib/gcc/x86_64-linux-gnu/5/libstdc++.a
/usr/lib/gcc/x86_64-linux-gnu/5/libstdc++.so
/usr/lib/x86_64-linux-gnu/libstdc++.so
/usr/lib/x86_64-linux-gnu/libstdc++.so.6
/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21

/lib/i386-linux-gnu/libpthread-2.19.so
/lib/i386-linux-gnu/libpthread.so.0
/lib/x86_64-linux-gnu/libpthread-2.19.so
/lib/x86_64-linux-gnu/libpthread.so
/lib/x86_64-linux-gnu/libpthread.so.0
/usr/lib/debug/lib/x86_64-linux-gnu/libpthread-2.19.so
/usr/lib/x86_64-linux-gnu/libpthread.a
/usr/lib/x86_64-linux-gnu/libpthread.so
/usr/lib/x86_64-linux-gnu/libpthread_nonshared.a

How can I solve the problem? Thanks for your help.

---

### Post by newcfd on 2015-07-22
Damn it. No problem to make a static build. The problem shows up when shared libraries are built.
This package is an open source one and I am not allowed to use it with a static build.
Anyone can help? Thanks in advance.

---

### Post by steeldriver on 2015-07-22
What is the software you are trying to build? do you have a link to the source so we can try it for ourselves?

---

### Post by newcfd on 2015-07-23
I am trying to install OpenCascade 6.3(sort of old) on ubuntu. It seems that the configure file does not like the latest libraries of stdc++ and pthread.
The new ones were installed when I upgraded g++ to 5.0. Unluckily, I can not remove them any more.

---

