---
title: "LD_LIBRARY_PATH, ld.so.conf, and gcc"
date: 2010-02-14
forum: Programming Talk
---

### Post by d_brandt on 2010-02-14
I have a question about the "right way" to link with a library.

 My question is: [SIZE=4]why, after setting LD_LIBRARY_PATH or setting up the /etc/ld.so.conf file, do I still need to specify the location of a library at compilation time?[/SIZE]

The man page for ld states:

> The linker uses the following search paths to locate required shared libraries:
[...]
5. For a native linker, the [sic] search the contents of the environment variable "LD_LIBRARY_PATH"
[...]
7. The default directories, normally /lib and /usr/lib.
8. For a native linker on an ELF system, if the file /etc/ld.so.conf exists, the list of directories found in that file.

So, if I have a program that needs the atlas library, which I have located at /usr/local/atlas/lib/libatlas.so, I can compile it this way:

```
$ gcc foo.c -L/usr/local/atlas/lib -latlas -o bar
```

and compilation will work fine. But if I try:

```
$ gcc foo.c -latlas -o bar
```

The linker complains about not being able to find the atlas library. My reading of the ld man page tells me that setting LD_LIBRARY_PATH should be a possible fix for this, but I get:

```
$ export LD_LIBRARY_PATH=/usr/local/atlas/lib
$ gcc foo.c -latlas -o bar
/usr/bin/ld: cannot find -latlas
collect2: ld returned 1 exit status
```

Setting up ld.so.conf to a value I think should work has the same result:

```
$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf

$ cat /etc/ld.so.conf.d/atlas.conf
/usr/local/atlas/lib
$ sudo ldconfig
$ gcc foo.c -latlas -o bar
/usr/bin/ld: cannot find -latlas
collect2: ld returned 1 exit status
```

However, ignoring the above issues, if I compile the program in a way that works, then, using either LD_LIBRARY_PATH or ld.so.conf, the program runs just fine (the loader is able to find the library).

So, am I reading the man page for the linker wrong? Why do I need to tell the linker where to find libraries, but the loader works just fine?

In case it's of value:
```
$ gcc --version
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ ld --version
GNU ld (GNU Binutils for Ubuntu) 2.20
Copyright 2009 Free Software Foundation, Inc.
This program is free software; you may redistribute it under the terms of
the GNU General Public License version 3 or (at your option) a later version.
This program has absolutely no warranty.
```

---

### Post by dwhitney67 on 2010-02-14
The simple answer is that gcc does not know about where to find your library.  To find out what areas gcc does know about, run this command, and example the 'libraries' section of the output:
```

gcc -print-search-dirs

```
The LD_LIBRARY_PATH and/or modifications to the ldconfig cache file assist in locating a library during the runtime of an application; not when building it.

---

