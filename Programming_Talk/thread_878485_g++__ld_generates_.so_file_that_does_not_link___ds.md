---
title: "g++ / ld generates .so file that does not link __dso_handle"
date: 2008-08-02
forum: Programming Talk
---

### Post by demareg on 2008-08-02
I use ld to generate the .so file successfully and -v outputs:
  GNU ld (GNU Binutils for Ubuntu) 2.18.0.20080103
  ld: mode elf_x86_64

When trying to load the .so file (using Java JNI), I get:
  java.lang.UnsatisfiedLinkError: libadrjava.so: undefined symbol: __dso_handle

Search of the web suggested that I add dso_handle.c containing:
  const void *const __dso_handle __attribute__ ((__visibility__ ("hidden")))
  = &__dso_handle;

This gives me the following compile warning:
  g++    -c -o dso_handle.o dso_handle.c
  dso_handle.c:22: warning: ‘__visibility__’ attribute ignored
but does not fix the problem.

What should I do to fix the problem?

---

### Post by dwhitney67 on 2008-08-03
WTFlock?  What are you trying to accomplish???

---

### Post by demareg on 2008-08-03
I have code that I have interfaced with Java on Windows as a DLL that I want to run under Java on Linux.

---

### Post by demareg on 2008-08-04
If I change the load to include a -static before the libaries (e.g. -lc) then I get a load error:
  ld: /usr/bin/../lib/libc.a(ctype.o): relocation R_X86_64_32 against 
  `a local symbol' can not be used when making a shared object;
   recompile with -fPIC
   /usr/bin/../lib/libc.a: could not read symbols: Bad value

Are there static and relocatable standard libraries?

---

### Post by hamid2c on 2011-02-07
> **demareg said:**
> I use ld to generate the .so file successfully and -v outputs:
  GNU ld (GNU Binutils for Ubuntu) 2.18.0.20080103
  ld: mode elf_x86_64

When trying to load the .so file (using Java JNI), I get:
  java.lang.UnsatisfiedLinkError: libadrjava.so: undefined symbol: __dso_handle

Search of the web suggested that I add dso_handle.c containing:
  const void *const __dso_handle __attribute__ ((__visibility__ ("hidden")))
  = &__dso_handle;

This gives me the following compile warning:
  g++    -c -o dso_handle.o dso_handle.c
  dso_handle.c:22: warning: ‘__visibility__’ attribute ignored
but does not fix the problem.

What should I do to fix the problem?

Since you generate object files by using g++, you should also use g++ to link them (i.e. g++ -shared your_object_files -o libexample.so). Do not use ld to link object files which are produced by g++

---

### Post by worksofcraft on 2011-02-07
> **hamid2c said:**
> Since you generate object files by using g++, you should also use g++ to link them (i.e. g++ -shared your_object_files -o libexample.so). Do not use ld to link object files which are produced by g++

NVM... Edit:

D'oh

this thread is from way back in antediluvian times :shock:

---

