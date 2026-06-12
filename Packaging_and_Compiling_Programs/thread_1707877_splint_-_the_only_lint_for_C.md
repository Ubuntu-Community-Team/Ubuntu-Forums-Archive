---
title: "splint - the only lint for C?"
date: 2011-03-15
forum: Packaging and Compiling Programs
---

### Post by osjak on 2011-03-15
I am about to take a course where we will be using C for programming, so I am trying to read up on it before hand. The book I am using, "C Programming: A Modern Approach", advises to use a 'lint' code checker to clean my code. The only code checker I have found for Ubuntu is *splint*. The problem with it is that although the documentation says it's using C99 standard, its parser chokes on declaring a loop variable inside the *for* loop. For example:

```
for (int i = 0; i < 10; i++) {
   /* some code here */
}
```

The parser will stop with an error after seeing *'for (int'*. However, the C89 standard works fine:

```
int i;

/* some code here */

for (i = 0; i < 10; i++) {
   /* some code here */
}
```

I tried the patch proposed here:
[http://www.cs.virginia.edu/pipermail/splint-discuss/2008-July/001190.html](http://www.cs.virginia.edu/pipermail/splint-discuss/2008-July/001190.html)
but it addresses a slightly different problem, and does not help me.

I would like to use the C99 standard and still be able to check my code. Does anyone know how to fix the parser? Or is there another 'lint' program that works well?

---

### Post by MadCow108 on 2011-03-16
in my experience lint just gives you billions of false positives which make it rather useless for non-trivial size program.

I quite like the static analyzer of clang:
[http://clang-analyzer.llvm.org/](http://clang-analyzer.llvm.org/)

you can also use cppcheck on C code
[http://cppcheck.sourceforge.net/](http://cppcheck.sourceforge.net/)
the big advantage of this one is that is has almost zero false positives (but in return might not find as many bugs).

then there are still a bunch of very good commercial ones like coverity.

---

### Post by gmargo on 2011-03-16
This doesn't answer your lint question, but.... Assuming you're using the GCC compilers, make sure you always add the "-Wall" option, and fix all the warnings.  This will catch a lot of the same things lint might.

---

