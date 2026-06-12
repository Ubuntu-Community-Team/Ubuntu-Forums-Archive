---
title: "ldconfig question"
date: 2008-09-29
forum: Programming Talk
---

### Post by khughitt on 2008-09-29
Hi all,

I am not too familiar with compilation that involves linking, and was wondering if someone could help me understand if i'm doing it wrong.

Here is my dilemma:

I have compiled some binaries using a provided make file. At first, however, the binaries do not work because they cannot find the necessary libraries:

> 
./kdu_merge: error while loading shared libraries: libkdu_v60R.so: cannot open shared object file: No such file or directory


The offending file does indeed exist, but it simply cannot be found.

I can get around this by creating a conf file in the /etc/ld.so.conf.d/ directory, and running "ldconfig," but this only works if I have admin privileges. I would like to be able to install it on a remote system (a web host), for which I do not have sufficient privileges to call ldconfig.

Is there any way to compile it so that it knows where to find the library?


Any help would be greatly appreciated. :)

Thanks!

---

### Post by dwhitney67 on 2008-09-29
I presume that you are compiling/linking with GCC.  If so, then specify the -L option along with the path where the library exists.

For example,
```
gcc myprog.c -L/path/to/library -llibname -o app
```

If the library does not exist on your remote system, you will need to statically link (essentially include) the library within your application, as opposed to dynamically loading it during runtime of the application.

This is done by (and sorry, I may be wrong about this):
```
gcc myprog.c -L/path/to/library -static -llibname -o app
```

---

