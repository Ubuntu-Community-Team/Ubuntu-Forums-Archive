---
title: "Compiler can't find shared libraries"
date: 2008-02-26
forum: Packaging and Compiling Programs
---

### Post by Potto on 2008-02-26
Hi guys,

I'm new to programming and Ubuntu, so sorry if this is a stupid question:

I'm trying to compile the number theory libraries ntl-5.4.1.  When I run make I get the following error:

gcc -I../include -I.  -O2   -I/usr/local/include -o gen_lip_gmp_aux gen_lip_gmp_aux.c -L/usr/local/lib -lgmp -lm
./gen_lip_gmp_aux > lip_gmp_aux_impl.h
./gen_lip_gmp_aux: error while loading shared libraries: libgmp.so.3: cannot open shared object file: No such file or directory

But libgmp.so.3 is in /usr/local/lib.  Does anyone know why gcc can't find it?   I trued adding /usr/local/lib to LD_LIBRARY_PATH, but that had no effect.

---

### Post by cyberdork33 on 2008-02-26
try installing the dev package for your library:
```
sudo apt-get install libgmp3-dev
```

If you get similar errors in the future, you have to search for the appropriate -dev package for compiling.

---

### Post by Potto on 2008-02-26
It works!  Thanks!

---

