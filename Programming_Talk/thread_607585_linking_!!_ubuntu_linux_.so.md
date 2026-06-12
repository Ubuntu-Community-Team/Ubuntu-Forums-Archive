---
title: "linking !!?? ubuntu linux .so"
date: 2007-11-09
forum: Programming Talk
---

### Post by queency on 2007-11-09
in my examples i can see the <iostream> tag
how can i know where all header files , tags are located
in the .so files.

example:

I am using wx/wx.h, sqlite3.h, stdlib.h, stdio.h header files and
I cannot link after compiling because i don't know the .so files
that this headers belong to.
gcc -c <mySource> works fine but gcc <mySource> doesn't

where can i find a guide for compiling / linking and .so index
and connect the headers to .so's

---

### Post by bunker on 2007-11-09
You need to refer to the docs and manpages of the softwares you're using unfortunately.  For standard library headers, they're automatically linked, otherwise you need to specify the library when linking.  For example, if I was to use the pthread library (pthread.h and /usr/lib/libpthread.so), the command is:
```
gcc -lpthread -o myprog the_source.c
```
Most libraries are in some similar format, eg boost_thread is lboost_thread, presumably wx/wx.h would be something like -lwx.

If you want to see which libraries a program has loaded, run
```
ldd <command>
```
For example
```
[bunker@sword] $ ldd /bin/ls
        linux-gate.so.1 =>  (0xffffe000)
        librt.so.1 => /lib/i686/cmov/librt.so.1 (0xb7fcb000)
        libacl.so.1 => /lib/libacl.so.1 (0xb7fc4000)
        libselinux.so.1 => /lib/libselinux.so.1 (0xb7fae000)
        libc.so.6 => /lib/i686/cmov/libc.so.6 (0xb7e66000)
        libpthread.so.0 => /lib/i686/cmov/libpthread.so.0 (0xb7e4f000)
        /lib/ld-linux.so.2 (0xb7fe3000)
        libattr.so.1 => /lib/libattr.so.1 (0xb7e4b000)
        libdl.so.2 => /lib/i686/cmov/libdl.so.2 (0xb7e46000)
        libsepol.so.1 => /lib/libsepol.so.1 (0xb7e05000)

```

---

