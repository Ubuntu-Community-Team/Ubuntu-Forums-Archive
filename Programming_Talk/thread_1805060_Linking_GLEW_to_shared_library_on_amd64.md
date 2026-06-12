---
title: "Linking GLEW to shared library on amd64"
date: 2011-07-15
forum: Programming Talk
---

### Post by MiKom on 2011-07-15
Hi,

im developing a shared library (game engine to be exact) that needs to link to GLEW. When the library is getting linked I get following error:

```
/usr/bin/ld: /usr/lib64/libGLEW.a(glew.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/lib64/libGLEW.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
```

I'm running 64bit Natty with package ibglew1.5-dev installed.

---

### Post by karlson on 2011-07-15
> **MiKom said:**
> Hi,

im developing a shared library (game engine to be exact) that needs to link to GLEW. When the library is getting linked I get following error:

```
/usr/bin/ld: /usr/lib64/libGLEW.a(glew.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/lib64/libGLEW.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
```

I'm running 64bit Natty with package ibglew1.5-dev installed.

Are you compiling with -fPIC set as the error suggests?

---

### Post by MiKom on 2011-07-15
I am indeed compiling with -fPIC. I think that error message suggests that libGLEW is not compiled with -fPIC, and it should be.

UPDATE: Also, it compiles well if I compile it as a static library.

---

