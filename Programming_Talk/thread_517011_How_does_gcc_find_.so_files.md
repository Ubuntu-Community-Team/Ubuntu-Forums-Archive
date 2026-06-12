---
title: "How does gcc find .so files?"
date: 2007-08-03
forum: Programming Talk
---

### Post by WereWisher on 2007-08-03
I'm having a problem, and I think the cause is gcc not finding the .so file that corresponds to a .h file that is in the standard system include path.

How does gcc find .so files?  is there a standard system library path as well??

Any help would be appreciated,

-WW

---

### Post by rbprogrammer on 2007-08-04
probably i cant help you, but you might want to post what commands you are executing when compiling..

for example, are you making your own shared object? or are you using a pre-written one?

i'm not a pro, but i'm sure more information is needed to the pros to help :) ..

---

### Post by WereWisher on 2007-08-04
It seems that I have answered my own question, a file /etc/ld.so.conf and a utility called ldconfig, allow you to register your library directories with the linker.

And as for my problem, well, it turned out that it wasn't a linking issue after all, it was a simple lack of a dependancy I needed.  

Melancholy ensues,
-WW

---

### Post by slavik on 2007-08-04
.so files are linked to during runtime, not during compile time, so gcc doesn't know anything about .so files except that the code being compiled will be linked by the system when needed (when program is run). gcc (specifically the linker) knows about .a files which are static libraries (same as including the entire source code almost, except they are precompiled) ...

---

### Post by the_unforgiven on 2007-08-04
> **slavik said:**
> .so files are linked to during runtime, not during compile time, so gcc doesn't know anything about .so files except that the code being compiled will be linked by the system when needed (when program is run). gcc (specifically the linker) knows about .a files which are static libraries (same as including the entire source code almost, except they are precompiled) ...
No, gcc can link in .so files too - in which case, it works more like an import lib - the .so is definitely loaded only when the program is run, but the linker CAN resolve symbols using .so.

What you're talking about is explicit loading of DSOs - using the dlopen()/dlsym() API.

---

### Post by slavik on 2007-08-04
> **the_unforgiven said:**
> No, gcc can link in .so files too - in which case, it works more like an import lib - the .so is definitely loaded only when the program is run, but the linker CAN resolve symbols using .so.

What you're talking about is explicit loading of DSOs - using the dlopen()/dlsym() API.
learn something new, everyday. thanks. :)

---

