---
title: "Choosing between Compilers"
date: 2006-02-07
forum: Packaging and Compiling Programs
---

### Post by glee on 2006-02-07
Hello, 

I notice that build-essential defaults to the gcc 4.0 suite. I am somewhat wary of this, given that under Gentoo, for instance, gcc 3.4 is the current stable offering. Further, I need to have g77, and I notice that under Ubuntu g77 4.0 requires gcc 3.4 (!)

Anyone care to express an opinion re: stability and compatibility? Should I install build-essential plus g77 and allow Ubuntu to take care of dependencies, or simply choose gcc 3.4 components manually?

Cheers, 
glee.

---

### Post by gord on 2006-02-07
you can have them both installed, gcc4 is fine and i use it all the time, but it is diffirent than 3.4 and so many applications won't compile using gcc4.

if its a ./configure based program you can just set "CC=gcc-3.4"

id recomend 4.0 though, just because of the fact that one day you'll have to use it, maybe not today, maybe not tommorow, but someday :)

---

