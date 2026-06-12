---
title: "How do I compile x86_64 from an x86 machine?"
date: 2007-11-26
forum: Packaging and Compiling Programs
---

### Post by TwoBit on 2007-11-26
How do I compile x86_64 from an x86 machine? I have some x86 code but I need it to compile on x86-64. I don't have to  worry about it running right now, I just need to periodically compile it. 

I figure this must be possible because my Mac and Windows computers both have built-in cross-compiling to 64 bit, and Linux/GCC is usually at least as flexible as the others. 

I couldn't find an answer searching the forums, and no such package is listed in any of the package managers I've tried (e.g. Synaptic).

Thanks.

---

### Post by meatpan on 2007-11-26
Try using gcc with the '-m64' flag.

Here are some further docs regarding cross-compiling 32/64 on gcc:
[http://gcc.gnu.org/onlinedocs/gcc-4.2.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc-4.2.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)

---

### Post by TwoBit on 2007-11-27
Thanks. Using "/usr/bin/c++ -m64 hello.cpp" resulted in an error:

    /usr/bin/ld: cannot find -lm.

So I did some searches and found that -lm means libm. I used the package manager to download the 64 bit libc and libc++ libraries and it now appears to be successfully compiling and linking my simple test file.

---

