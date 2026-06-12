---
title: "[C++] io.h, process.h, eh.h ... but for Linux"
date: 2009-08-03
forum: Programming Talk
---

### Post by wbest on 2009-08-03
Hey,
are there any equivalents (or anything even remotely close) of the windows header files io.h, process.h, and eh.h that are for Linux?

Even if it takes 20 header files to do the job of any one of those, its fine.
So whatever you can give me would help.

PS.  Yes I know it may be best to go through and create fake io.h, process.h, and eh.h files so that it can find them, but can't find the method calls that they would contain, but there are already so many other errors in the file, mostly ambiguous function calls, that figuring out what functions I specifically should find linux equivalents to is not looking very appealing at this time.  Maybe I'll have the energy a bit later, but right now I'm casting to see if I can get anything.

---

### Post by crazyfuturamanoob on 2009-08-03
stdio.h? stdlib.h?

---

### Post by Mirge on 2009-08-03
What functions are you trying to use?

[http://en.wikipedia.org/wiki/Process.h](http://en.wikipedia.org/wiki/Process.h)

---

