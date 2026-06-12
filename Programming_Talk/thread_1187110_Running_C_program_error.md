---
title: "Running C program error"
date: 2009-06-14
forum: Programming Talk
---

### Post by magawake on 2009-06-14
I have some C code, and I compiled the C library in /home/user/


```
gcc create_file.c -I/home/user/include -L/home/user/lib -lhdf5 -o create_file

```

The code compiles and builds fine...
But, when I run it I keep getting


```

./create_file: error while loading shared libraries: libhdf5.so.6: cannot open shared object file: No such file or directory

```

Any ideas? 

TIA

---

### Post by dwhitney67 on 2009-06-14
Try
```

LD_LIBRARY_FLAGS=/home/user/lib create_file

```
Your /home/user/lib is not a library directory known to the system, much less gcc.  Hence the reason you must specify it.

---

### Post by stroyan on 2009-06-14
The LD_LIBRARY_FLAGS environment variable will get the job done.
But it is very awkward to use.

You can also tell the ld.so dynamic linker/loader to search for shared libraries
in additional directories by including an rpath setting at build time.
Add
-Wl,-rpath,/home/user/lib
to your gcc options.
That is passed on to ld as "-rpath /home/user/lib".
It then shows up in the executable file.
It can be examined with
readelf --dynamic ./create_file

There is a bit of an issue with the use of rpath in debian packages.
It is less flexible than other approaches.
See [http://wiki.debian.org/RpathIssue](http://wiki.debian.org/RpathIssue) for a discussion.
Another option for a package is to update /etc/ld.so.conf or
create a config file in the /etc/ld.so.conf.d then run ldconfig.
There are many rules about handling shared libraries in debian packages at
[http://www.debian.org/doc/debian-policy/ch-files.html#s-libraries](http://www.debian.org/doc/debian-policy/ch-files.html#s-libraries)

---

