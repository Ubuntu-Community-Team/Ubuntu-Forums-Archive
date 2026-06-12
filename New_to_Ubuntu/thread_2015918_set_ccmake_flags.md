---
title: "set ccmake flags"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2012-07-03
Yup, silly beginner question.  When running ccmake (not cmake, though I don't know what the difference is) I have to set some flags.  The tut says run ccmake  . and be sure to set 6 flags, for example BUILD_EXAMPLES ON and BUILD_FAKENECT ON

sooooo how do I do that?

Should it be, for example, 

ccmake  . -BUILD_EXAMPLES=ON -BUILD_FAKENECT=ON

or how exactly do I go abou tthat?

regards, Richard

---

### Post by MG&amp;TL on 2012-07-04
According to [http://linux.die.net/man/1/ccmake](http://linux.die.net/man/1/ccmake) , ccmake is a curses interface to cmake. Therefore just cd to the source directory and run:

```
ccmake
```

and presumably just set the flags graphically.

Hope that helped.

---

