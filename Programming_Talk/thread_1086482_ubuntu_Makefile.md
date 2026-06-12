---
title: "ubuntu Makefile"
date: 2009-03-04
forum: Programming Talk
---

### Post by bundy75 on 2009-03-04
Hi
I recent install ubuntu and previously have been using debian etch. In a make file from my debian system I have the command

 @cp -a /home/tst/zlib-1.2.3/libz.so{.1,.1.2.3} build/

does ubuntu not support the use of the curly brackets in this way as I get the error

cp: cannot stat `/home/tst/zlib-1.2.3/libz.so{.1,.1.2.3}': No such file or directory

instead of doing a copy of the two directories

"/home/tst/zlib-1.2.3/libz.so.1" 
"/home/tst/zlib-1.2.3/libz.so.1.2.3"

as on debian 


Thanks

---

### Post by dwhitney67 on 2009-03-04
It does, but you need to install bash.  Ubuntu is delivered with a variant of bash called "dash".  It does not support the {}, nor pushd/popd.

Once you install bash, ensure that /bin/sh points to it, and not to dash.

---

