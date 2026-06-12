---
title: "ld-linx-x86-64 segfault Just After Compiling (but Only Once) What's Happening?"
date: 2008-12-09
forum: Packaging and Compiling Programs
---

### Post by mankyd on 2008-12-09
I've started work on my first Apache module and it's coming along nicely. Part of my module involves adding support for loading modules of its own (a simple plugin architecture of sorts, specific to my module.) I am accomplishing this with dlopen and dlsym, two commands which I am also new to.

For the most part, everything is working well. The only hitch I am running into is immediately compiling one of my plugins. I restart the Apache server, compile my plugin into a .so, move it to where it needs to be, and then send a test request to the server. The request dynamically loads in the plugin I just compiled.

On the very first request, it causes the Apache process to segfault. On each subsequent request, the page returns just fine, loading the plugin with no complaints.

I tried running Apache through gdb, and I get this output:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f1ed215d750 (LWP 16990)]
0x00007f1ed1f6eb1b in ?? () from /lib64/ld-linux-x86-64.so.2
```

When I print the backtrace, I get:

```
#0  0x00007f1ed1f6eb1b in ?? () from /lib64/ld-linux-x86-64.so.2
#1  0x00007f1ed1f6f056 in ?? () from /lib64/ld-linux-x86-64.so.2
#2  0x00007f1ed1f6f29e in ?? () from /lib64/ld-linux-x86-64.so.2
#3  0x00007f1ed147b516 in ?? () from /lib/libc.so.6
#4  0x00007f1ecf8b60d4 in ?? () from /lib/libdl.so.2
#5  0x00007f1ed1f73656 in ?? () from /lib64/ld-linux-x86-64.so.2
#6  0x00007f1ecf8b62cc in ?? () from /lib/libdl.so.2
#7  0x00007f1ecf8b607a in dlsym () from /lib/libdl.so.2
#8  0x00007f1ecbba00dc in load_library () from /usr/lib/apache2/modules/mod_mymod.so
...
#22 0x00007f1ed21d893d in ap_mpm_run () from /usr/sbin/apache2
#23 0x00007f1ed21ae40d in main () from /usr/sbin/apache2
```

Is there something I am doing wrong here? Let me be the first to admit that I'm a bit of a noob when it comes to C compiling and debugging - I spend most of my time as a script developer. Thanks for any insight you may be able to offer!

---

### Post by lensman3 on 2008-12-11
I'm fishing here.  Use the "file" command on the Apache binary and see if your Apache binary is 32bit.  You are compiling for a 64bit.  Maybe that's the problem.

Sorry I can't be more help, but it looks like everything you are doing is OK.

---

### Post by mankyd on 2008-12-11
Thanks for the feedback. It is a 64bit binary of Apache, unfortunately.

One interesting thing of note: If I don't actually change the code, and just recompile, the segfault does not occur. It only occurs when I move a line of code or two around (i.e. inserting/removing a few junk lines just ot mix things up.)

Also, this is actually happening within a nested dlopen() call. I.E. the plugin I am loading is actually a database abstraction library, which itself loads in a specific database driver. Changing the abstraction plugin doesn't seem to cause a segfault. Changing the driver does.

---

