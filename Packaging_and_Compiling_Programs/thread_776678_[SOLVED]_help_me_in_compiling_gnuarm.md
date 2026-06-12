---
title: "[SOLVED] help me in compiling gnuarm"
date: 2008-04-30
forum: Packaging and Compiling Programs
---

### Post by montamer on 2008-04-30
hi 
im trying to compile gnuarm ... following these instructions here
[http://mcuprogramming.com/blog/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/#more-155](http://mcuprogramming.com/blog/2007/04/22/build-your-own-arm-cross-compiler-toolchain-2/#more-155)
im facing problem when compiling newlib
im getting this error

```

make[3]: Entering directory `/home/vijay/Desktop/newlib-1.14.0/etc'
/home/vijay/Desktop/newlib-1.14.0/missing makeinfo --split-size=5000000 --split-size=5000000 --no-split -I.././etc -o standards.info .././etc/standards.texi
WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [standards.info] Error 1
make[3]: Leaving directory `/home/vijay/Desktop/newlib-1.14.0/etc'
make[2]: *** [info] Error 1
make[2]: Leaving directory `/home/vijay/Desktop/newlib-1.14.0/etc'
make[1]: *** [all-etc] Error 2
make[1]: Leaving directory `/home/vijay/Desktop/newlib-1.14.0'
make: *** [all] Error 2
root@vijay-desktop:~/Desktop/newlib-1.14.0#
``` 

i have texinfo install , still the problem exist. i have no clue what to do.

---

### Post by montamer on 2008-05-04
sorry to bump the thread , but i really need to get this toolchain on my ubuntu ...... 
any idea? what the error is about???

---

### Post by montamer on 2008-05-12
got a precompiled toolchain. :KS
solved

---

### Post by Freddy436 on 2008-05-17
I had the same problem, probably an problem with configure.

You can set MAKEINFO...
./configure ... MAKEINFO=$(which makeinfo)

or edit the generated Makefile:
Look for a line like this:
MAKEINFO = .../missing makeinfo
Relace it with:
MAKEINFO = makeinfo

---

### Post by waipotn on 2008-11-03
We already have discussions for fixing on this thread

[http://ubuntuforums.org/showthread.php?p=4408067]("http://ubuntuforums.org/showthread.php?p=4408067")

---

