---
title: "Distributing binaries with shared libraries"
date: 2006-10-04
forum: Programming Talk
---

### Post by tralalalala on 2006-10-04
I am trying to send a program to somebody who does not have some of the shared libraries that the program depends on. I tried putting the program and the shared libraries in the same directory, and then running the program, but I get the following error:

./program: error while loading shared libraries: libmylib.so.1: cannot open shared object file: No such file or directory

Is there anywhere that I can look to figure out how to do this without using static linking?

Thanks!

---

### Post by Houman on 2006-10-04
Hi there,

ld, the dynamic loader/linker, has to know where to find your shared libraries. I suggest you try adding the path to the shared libraries to " /etc/ld.so.conf" and then running ldconfig as root to update the cache.  

regards,
Houman

---

### Post by amo-ej1 on 2006-10-05
Or for quick check you could also use the environment variable LD_LIBRARY_PATH 

see [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)

---

