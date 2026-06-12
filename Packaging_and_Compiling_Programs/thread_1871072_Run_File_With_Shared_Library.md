---
title: "Run File With Shared Library"
date: 2011-10-28
forum: Packaging and Compiling Programs
---

### Post by remusmp on 2011-10-28
Hi All,

I am building a project that uses a shared library (more details about the way I build it are found in this thread [http://ubuntuforums.org/showthread.php?t=1870586](http://ubuntuforums.org/showthread.php?t=1870586)).

The project is built successfully but when I run the file the shared libraries are not found:
./simple: error while loading shared libraries: libmaplec.so: cannot open shared object file: No such file or directory

I partially solve it by adding these extra commands before running the file:
MAPLE=/usr/local/bin/maple15
export LD_LIBRARY_PATH=$MAPLE/bin.IBM_INTEL_LINUX

But then I get this error:
fatal error(-1) loading GMP library: ./libgmp.so
Aborted

I think there is a conflict between libgmp.so from /usr/lib/ and libgmp.so from $MAPLE/bin.IBM_INTEL_LINUX (my file should use libgmp.so from $MAPLE/bin.IBM_INTEL_LINUX and not the other one!).

I got it working only by copying the binary file (simple) to where the libraries are located. It runs well from that folder! But I would like to run it from a different folder.

How do I solve this issue?

Thanks a lot!

Remus.

---

### Post by MadCow108 on 2011-10-28
did you copy the maple executle to /usr/lib and it worked?
or to $MAPLE/bin.IBM_INTEL_LINUX/?
do you have libgmp-dev installed? if yes and it is the cause of the conflict, try removing it (will only remove the symlink in /usr/lib and a few headers)

perhaps this works
```
LD_PRELOAD=$MAPLE/bin.IBM_INTEL_LINUX/libgmp.so maple-executable
```

---

