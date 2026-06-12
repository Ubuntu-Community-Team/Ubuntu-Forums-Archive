---
title: "what's up with mkstemp?"
date: 2007-11-16
forum: Packaging and Compiling Programs
---

### Post by webdreamer on 2007-11-16
We are having trouble including the function mkstemp. In the manual it refers to stduni.h and stdlib.h but none of this libraries have mkstemp in it. I know the manual says to us not to use this function, but this is the one we need to use, so where to find mkstemp?

I've noticed similar posts on the net but they had no answer...

---

### Post by meatpan on 2007-11-17
Which version of ubuntu are you using?    

I'm running 7.10, with libc6  2.6.1-1ubuntu10, and  mkstemp(..) is available.

Check out your packages with 'dpkg -l | grep <package>'

---

