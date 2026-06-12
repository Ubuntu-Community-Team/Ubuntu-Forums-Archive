---
title: "g++ - Utilizing SSE Instructions"
date: 2012-05-29
forum: Programming Talk
---

### Post by MechWarrior001 on 2012-05-29
I've learned alot more about C++, but I'm still relatively new when it comes to compiling code utilizing the -msse<version> and/or -mfpmath options.

If I use -msse2, do I need to declare -msse as well? I wasn't sure if -msse2, -msse3 or etc included the instructions from previous options, or just added their own respective options on top of the previous option.

Also, if I declare -msse, do I need to declare -mfpmath?

---

### Post by jabl on 2012-05-29
> **MechWarrior001 said:**
> I've learned alot more about C++, but I'm still relatively new when it comes to compiling code utilizing the -msse<version> and/or -mfpmath options.

If I use -msse2, do I need to declare -msse as well? I wasn't sure if -msse2, -msse3 or etc included the instructions from previous options, or just added their own respective options on top of the previous option.


Sorry, I don't remember. The easiest way would IMHO be -march=native, which enables all features on the target CPU.

> 
Also, if I declare -msse, do I need to declare -mfpmath?

-mfpmath changes the default. In i386 mode (32-bit), -mfpmath=387 is the default, in x86-64 mode the default is -mfpmath=sse. Note that due to ABI compatibility, in i386 mode function arguments will still use the x87 regs.

If you want your code to be vectorized, you additionally need -ftree-vectorize (enabled by default with -O3), and often also -ffast-math. -ftree-vectorizer-verbose= can give you information why a loop wasn't vectorized, potentially enabling you to fix your code.

---

### Post by MadCow108 on 2012-05-29
-msse2 implies -msse so you don't need to explicitly set it (note that -msse2 is default on x86_64) but it also does not harm
this is also true for sse2 and sse3 to but not for all variants, e.g. sse4.1 does not imply ssse3 (yes three 's').
as mentioned march=native is the easiest way

I recommend to set -mfpmath=sse if your target machines support it (also default on 64 bit). It allows the autovectorizer (which is quite decent in 4.7) to work much better on machines with i386 target (e.g. 32 bit installs on x64 cpus). If its not set it will bail out on such machines with "cannot autovectorize long double" in allmost all cases due to how fpu's work.
It also improves rounding behavior even if nothing is vectorized, see the gcc manpage.

---

### Post by MechWarrior001 on 2012-06-02
Thanks for the help; Is there a website or a article somewhere that explains all these extra optimization/compiler options like -ftree-vectorize in a (relatively) easy to understand manner?

---

### Post by MadCow108 on 2012-06-02
the gcc manual:
[http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/Optimize-Options.html#Optimize-Options](http://gcc.gnu.org/onlinedocs/gcc-4.7.0/gcc/Optimize-Options.html#Optimize-Options)

---

