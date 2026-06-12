---
title: "change gcc optimisation flag"
date: 2008-04-09
forum: Programming Talk
---

### Post by leg on 2008-04-09
How do I change the -02 when I compile something. Is there a system wide default for the compilation flags or can I change for each program I compile.

---

### Post by Zugzwang on 2008-04-09
So how do you compile? 

The preferred way my many people here is to call gcc/g++ on the command line directly. Then you just add "-O3" or "-O0" (whatever you want). If you're using a standard Makefile, then you just add it to the line for "converting" .c or .cpp files into .o files.

Or are you using an IDE?

---

### Post by leg on 2008-04-09
Compiling a library with a makefile for now but also in an ide occasionally

---

### Post by Zugzwang on 2008-04-09
Would you mind posting the Makefile here so we can tell you where to add the flag.

As for IDEs, it depends on the IDE.

---

### Post by leg on 2008-04-09
Well I have found where to edit in the makefile and I can change them in the ide I use I just thought there might have been a system default set of flags to use. What I am actually struggling with is, maybe, a problem with visualisation in gcc. I have been reading that this problem exists for versions under 4.2. I am using 4.1 at the moment. How do I safely update the version of gcc?

---

### Post by Zugzwang on 2008-04-09
Regarding updating gcc: I don't know. 

As far as defaults are concerned: According to the [GCC documentation]("http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html") "-O0" is default (in every distribution) provided that you don't mean the setting of the flag when compiling the system tools/lib/programs itself.

---

### Post by Ramses de Norre on 2008-04-09
In your bashrc, try exporting CFLAGS and CXXFLAGS, for compiling c and c++ respectively. I'm not sure about how ubuntu handles these env var's though, if it doesn't work you can try adding this to your bashrc instead: ```
alias gcc='gcc -O2'
alias g++='g++ -O2'
```

---

### Post by leg on 2008-04-09
I think that the makefile will override that anyway. What I want to try now is upgrade my gcc to 4.2 to see if it is this visibility issue I have read about. I have installed gcc 4.2 but there must be a way to make it the system default. I tried update-alternatives but was told that there is only one gcc. Can anyone tell me how to get this to upgrade so that when gcc is called I am using the 4.2 version. I would also appreciate knowing any pitfalls, if any, to upgrading gcc.

Thanks.

---

