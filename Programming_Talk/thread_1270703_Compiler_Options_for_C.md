---
title: "Compiler Options for C"
date: 2009-09-19
forum: Programming Talk
---

### Post by MechWarrior001 on 2009-09-19
Hey, long time no see.

I've recently been using Code::Blocks under ***Windows XP*** (for the meantime, so don't raid my house and override everything with Linux just yet :p), and I have some questions about the compiler options:

What does profiling the code do? [-pg]

Whats the difference between [-s] and [-Os]?

How do the expensive optimizations effect the generated exe? [-fexpensive-optimizations]

Will using [-s] and [-Os] simultaneously cause a crash/error/generally-bad-scenario-we-want-to-avoid?

---

### Post by Can+~ on 2009-09-19
```
       -pg Generate extra code to write profile information suitable for the analysis program gprof.
           You must use this option when compiling the source files you want data about, and you must
           also use it when linking.

```
```
       -fexpensive-optimizations
           Perform a number of minor optimizations that are relatively expensive.

           Enabled at levels -O2, -O3, -Os.
```

```
       -Os Optimize for size.  -Os enables all -O2 optimizations that do not typically increase code
           size.  It also performs further optimizations designed to reduce code size.

           -Os disables the following optimization flags: -falign-functions  -falign-jumps
           -falign-loops -falign-labels  -freorder-blocks  -freorder-blocks-and-partition
           -fprefetch-loop-arrays  -ftree-vect-loop-version

           If you use multiple -O options, with or without level numbers, the last such option is the
           one that is effective.
```

```
-s  Remove all symbol table and relocation information from the executable.
```

Manpages to the rescue. Try looking for online alternatives to man, because gcc has thousands of different arguments and flags.

---

