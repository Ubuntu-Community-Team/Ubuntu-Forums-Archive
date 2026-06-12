---
title: "Problems with gcc include path"
date: 2008-10-10
forum: Programming Talk
---

### Post by Cod on 2008-10-10
Hi folks,
I recently installed Ubuntu on a new laptop.  I'm compiling a package for R that includes C and C++ code.  It uses the adolc C/C++ libraries.  I installed adolc using apt-get and it has put the headers in /usr/include/adolc which is fine.  I need to include the header file adouble.h

However, when I use:

#include <adouble.h>

The compiler does not find the file.  If I specify the location, e.g. #include </usr/include/adolc/adouble.h> then of course everything is fine.  I could just do this but...

On my other, older laptop everything seems to be set up the same way but I only need to use #include <adouble.h> and it works.  The compiler knows to look in /usr/include/adolc.  The same is true for my friend's system.

It appears that the compiler is only looking at the first level of /usr/include and not inside any of the directories inside it.  But this doesn't happen on other machines.  Very weird.

Any clues?

---

### Post by Cod on 2008-10-10
Me again.  Please ignore my post.  I just solved the problem.  It was just me being stupid.  I can't be bothered to explain how I was being stupid, but everything is working as it should be.  I think I'll give up now and go for a beer instead. *sigh*

---

### Post by dwhitney67 on 2008-10-10
Beer is good!  It makes the brain compute things at light-speed.

Let me guess...
```
#include <adolc/adouble.h>
```
or did you compile with the -I/usr/include/adolc?

---

