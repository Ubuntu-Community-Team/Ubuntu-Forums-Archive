---
title: "[SOLVED] PCRE libraries appear to be missing after install"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by capnfabs on 2008-06-21
Hi (again) :)

I just downloaded and installed pcre-7.7 (with the standard ./configure, make, sudo make install), however, when I try to run any program that depends upon pcre, i receive the error message (in this case, for pcretest) ```
pcretest: error while loading shared libraries: libpcreposix.so.0: cannot open shared object file: No such file or directory
```.

Also, when I run "make check" from terminal, output indicates that pcregrep (a program that relies upon said libraries) worked perfectly. When I try the command "pcregrep --help" I get the same error message stated above.

If anyone could explain to me exactly what's going on and how I can avoid it, I would greatly appreciate it.

Thanks heaps!

P.S. Just found libpcreposix.so.0 in my usr/local/lib directory, if that means anything to anyone. Thanks again :)

Update: Just figured out how to fix the problem! :D If anyone is interested, there's further information at [http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html]("http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html")

---

### Post by bopjiang on 2012-03-07
I faced the same problem when installing pcre-8.21 on Ubuntu 11.04.
Don't know why /usr/local/lib/ not in default LD_LIBRARY_PATH.

---

