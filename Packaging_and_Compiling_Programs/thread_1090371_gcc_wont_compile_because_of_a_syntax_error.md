---
title: "gcc wont compile because of a syntax error?"
date: 2009-03-08
forum: Packaging and Compiling Programs
---

### Post by jimi_hendrix on 2009-03-08
i am interested in compiling LFS, and the build of binutils went fine

but now i am at gcc and i get:

```
In file included from ../../gcc-4.3.2/gcc/rtl.h:28,
                 from ../../gcc-4.3.2/gcc/attribs.c:29:
../../gcc-4.3.2/gcc/real.h:444: error: expected declaration specifiers or '...' before 'mpfr_srcptr'
../../gcc-4.3.2/gcc/real.h:444: error: expected declaration specifiers or '...' before 'mp_rnd_t'
../../gcc-4.3.2/gcc/real.h:445: error: expected ')' before 'const'
make[3]: *** [attribs.o] Error 1
make[3]: Leaving directory `/mnt/lfs/sources/gcc-build/gcc'
make[2]: *** [all-stage1-gcc] Error 2
make[2]: Leaving directory `/mnt/lfs/sources/gcc-build'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/mnt/lfs/sources/gcc-build'
make: *** [all] Error 2

```

i copied and pasted commands from the LFS book to make sure i got them right...any insight?

---

### Post by Coder543 on 2009-03-08
try the livecd

---

### Post by Neo_The_User on 2009-03-09
syntax errors are a result of broken C code. You'll need to re-program the file. Need help? I'll do it for you. Might be a few days depending on the complexity of the source code. Yeah the LiveCD would have gcc-4.3 pre-built on there besides the newer source code for the new versions of gcc have that syntax error fixed so if I re-programmed it, it would already be obsolete. ;)

---

### Post by geraldm on 2009-03-09
if you did not read and comply with the build instructions in LFS-6.4, chapter 05, you may also install the mfpr and gmp packages as an alternative.  

regards, 
Gerald

---

