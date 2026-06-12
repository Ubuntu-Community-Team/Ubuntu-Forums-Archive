---
title: "linker fails to compile C++ code"
date: 2006-10-11
forum: Programming Talk
---

### Post by Houman on 2006-10-11
Hi All,

I am trying to compile a simple code that I found on a book. However everytime it fails witht his message:

```

/usr/bin/ld: cannot find -ltcl
collect2: ld returned 1 exit status
make: *** [pg] Error 1

```

Obviosuly the linker can not find the tcl dev library (tcl8.x-dev) but that is very odd because I have installed the library. Actually at teh beginning it wasnt even able to find tcl.h until i installed several versions of the tcl dev library (i installed 8.0, 8.1, then 8.2 then it worked). The proper compile flags are passed to g++ so thats not a problem (I use -ltcl when linking).

Also here is a list of all libtcl files on my computer:
```

-rw-r--r-- 1 root root  704026 2006-01-19 00:21 /usr/lib/libtcl8.0.a
lrwxrwxrwx 1 root root      14 2006-10-09 21:01 /usr/lib/libtcl8.0.so -> libtcl8.0.so.1
-rw-r--r-- 1 root root  437012 2006-01-19 00:21 /usr/lib/libtcl8.0.so.1
-rw-r--r-- 1 root root  909882 2006-01-08 12:20 /usr/lib/libtcl8.3.a
lrwxrwxrwx 1 root root      14 2006-10-09 21:01 /usr/lib/libtcl8.3.so -> libtcl8.3.so.1
-rw-r--r-- 1 root root  563476 2006-01-08 12:20 /usr/lib/libtcl8.3.so.1
-rw-r--r-- 1 root root 1100392 2006-01-05 12:53 /usr/lib/libtcl8.4.a
lrwxrwxrwx 1 root root      14 2006-10-09 20:56 /usr/lib/libtcl8.4.so -> libtcl8.4.so.0
-rw-r--r-- 1 root root  705072 2006-01-05 12:53 /usr/lib/libtcl8.4.so.0
-rw-r--r-- 1 root root    1916 2006-01-08 12:20 /usr/lib/libtclstub8.3.a
-rw-r--r-- 1 root root    1908 2006-01-05 12:53 /usr/lib/libtclstub8.4.a


```

There are two things that seem strange to me about the above listing, one is that the sonames seem to be incorrect (shoudlnt a soname only contain the major revision number, for instance libtcl8.0.so should be libtcl8.so, it just looks odd).

Also I believe there is a symlink missing here and thats the cause of the linker not beign able to find the library, there is no symlink libtcl.so which has to be pointing to the latest so. 

I have tried to run ldconfig as root and that hasnt helped, is it possible this is a problem with the deb packages for the tcl dev files? (or am I doing somethign stupid here?)

thank you,

Houman

---

### Post by MWAAAHAAA on 2006-10-11
You could always try linking against an explicit version of tcl, e.g. -ltcl8.4. Alternatively you create a simlink to your desired version of tcl yourself.

I do not know if this is problem with the packages. Years ago I remember having the same sort of problem with tcl/tk when 'make xconfig' for the linux kernel. Otherwise, I have never used tcl.

BTW your linker does not fail to compile, it fails to link.

---

### Post by skymt on 2006-10-11
EDIT: What ^^he^^ said.

---

### Post by Houman on 2006-10-11
Hi there, 
I linked against 8.4 explicitly and now it works, thank you for your help.

Houman

---

