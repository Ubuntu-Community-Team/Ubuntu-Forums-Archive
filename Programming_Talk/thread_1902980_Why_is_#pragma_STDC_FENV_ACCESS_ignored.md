---
title: "Why is #pragma STDC FENV_ACCESS ignored ?"
date: 2012-01-01
forum: Programming Talk
---

### Post by Clive McCarthy on 2012-01-01
I'm using gcc 4.4.5 and C code. I'm compiling with all the SSE floating point options for the x86, turned on. 

I find that gcc does not recognize the **STDC FENV_ACCESS** pragma defined in C99.

I find that the **feenableexcept()** function links in glibc but has no prototype in **fenv.h** -- even with **_GNU_SOURCE** defined. This function is not part of C99 but is commonly referenced on the web and has a Linux man page.

I want to trap floating point exceptions because with SSE turned on certain integer divide by zero exceptions (such as x = 1 % 0) appear as floating point exceptions (I think this doesn't happen if just the x87 is used).

Is there a "clean" way of dealing with this? I found this link which at least assures me I'm somewhat on the right track: 
[http://www.fortran-2000.com/ArnaudRecipes/CompilerTricks.html#x86_FP]("http://www.fortran-2000.com/ArnaudRecipes/CompilerTricks.html#x86_FP")

---

### Post by Bachstelze on 2012-01-01
What value of -std are you compiling with? From fenv.h:

```
#ifdef __USE_GNU

/* Enable individual exceptions.  Will not enable more exceptions than
   EXCEPTS specifies.  Returns the previous enabled exceptions if all
   exceptions are successfully set, otherwise returns -1.  */
extern int feenableexcept (int __excepts) __THROW;

```

So try -std=gnu99.

---

### Post by Clive McCarthy on 2012-01-01
Thanks. Defining the __USE_GNU allows the prototype for feenableexcept to become visible but defining the "documented" _GNU_SOURCE does not.

I'm using the default -std=gnu89 so I guess that is why the pragma is unrecognized.

Thanks again.

---

