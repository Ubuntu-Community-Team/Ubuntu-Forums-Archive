---
title: "Help in crosscompilation: the library libdl.a"
date: 2007-11-30
forum: Programming Talk
---

### Post by Nokao on 2007-11-30
Hello World.

I have a very big problem, and I hope that in a forum like that, full of developers, I will find a solution.

This is a preambole, so to go directly to the problem jump after the:
------------------------------------------------------------------------
Yesterday I nearly fuked up my server, due to my attempt to move a file called libdl.so from /usr/lib/ to another folder.
My objective was trying to resolve a cross-compilation problem with the software "Lazarus", infact I wanted to compile from my machine (and AMD64) to a i386 architecture but that library was at 64 bits.

Fortunately, with a liveCD of ubuntu, I was able to put the file in it's original place and the server started again to work.
That library was an essential for everything, also the "mv" command, so I lost completely the control of the machine and I had the error ""libdl.so.2: cannot open shared object file"" doing anything.

Fortunately I discovered that "cat" and the "pipe" were working so I managed to backup the library with a "cat /path/ofthe/library > /backup/" before rebooting the zombie server.
------------------------------------------------------------------------

Now my problem is that lazarus won't compile anymore, the error is:
```
/usr/lib/fpc/2.2.1/units/x86_64-linux/rtl/cthreads.o: In function
`CTHREADS_LOADPTHREADS$$BOOLEAN':cthreads.pp:(.text+0x11): warning: Using 'dlopen' in statically linked
applications requires at runtime the shared libraries from the glibc version used for linking
/usr/bin/../lib/libdl.a(dlopen.o): In function `dlopen': undefined reference to `__dlopen'
/usr/bin/../lib/libdl.a(dlclose.o): In function `dlclose': undefined reference to `__dlclose'
/usr/bin/../lib/libdl.a(dlsym.o): In function `dlsym': undefined reference to `__dlsym'
myproject.lpr(185,1) Error: Error while linking
myproject.lpr(185,1) Fatal: There were 1 errors compiling module, stopping
```

That would be "their stuff" if the problem wasn't a ubuntu library-related problem.

So I'm begging you to help me to find wich package is related to that files:
libdl.a
libdl.so
crti.o

That are the files I tryed to copy at 32 bits on the machine, and help me reinstall them without destroyng the server again.

Also, I'd like to install the 32 bit versions of that files (that is the thing I was trying to do manually when I ruined my previous installation)

---

### Post by Nokao on 2007-12-03
No-one knows a way to understand wich package is related to that libs and how to re-install it?

---

### Post by llonesmiz on 2007-12-03
Those files are in the package "libc6-dev". You can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for packages containing a particular file.

---

### Post by Nokao on 2007-12-03
Thank you.

I managed to reinstall libc6-dev.

But I also want to know if is possible to install the 32 bit package with a dpkg -i --force-architecture without compromising the server installation.

The question is: the 32 bit libs are copyed in /usr/lib32 or in /usr/lib/ ?

Cause I need them in /usr/lib32/ for freePascal to cross-compile my application for 32 bits, but I don't want to overwrite the 64 bit library with the 32 bit version.

---

### Post by llonesmiz on 2007-12-03
In that case you need to install libc6-dev-i386.

---

### Post by Nokao on 2007-12-03
Thank you.

That installed the libs I needed... I still have some errors due to wrong libraries version, but I think that now I have to ask support to the lazarus team.

Bye

---

