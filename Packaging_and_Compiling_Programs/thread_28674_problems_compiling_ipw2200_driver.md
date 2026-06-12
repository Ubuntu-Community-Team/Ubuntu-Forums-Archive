---
title: "problems compiling ipw2200 driver"
date: 2005-04-21
forum: Packaging and Compiling Programs
---

### Post by juicewvu on 2005-04-21
I recently asked this question as a reply to the HOW TO: ipw2200+WPA
thread in the how to section.  I realize that its generally impolite
to cross post, however, the issue wasn't getting much attention there,
and the problem is with compiling the driver, so here goes:

The driver which is included with Horray for the ipw2200 wireless card
is quiet old, version 0.19 the current version is 1.03.  The included
driver does not support WPA authentication which I need to get on my
university's wireless network.  I am attempting to follow the
instructions in the thread I mentioned above.
[link](http://www.ubuntuforums.org/showthread.php?t=26623)
However after make has ran for sometime, the screen begins to fill
with error 2 errors.  I redirected the output of make to a file and found that before the error 2s begin the following errors occour:
```

make[1748]: execvp: /bin/sh: Argument list too long
make[1748]: Entering directory `/home/jcsmith/ipw2200-1.0.3'
make[1748]: execvp: make: Argument list too long
make[1748]: *** [modules] Error 127
make[1747]: *** [modules] Error 2

```
After which error 2's contiune to fill the screen until the numbers count down to 1.

This leads me to believe that there is a problem with the makefile itself, however in the thread liked to above there are many success stories so I kind of doubt thats the problem.

Hopefully someone out there with more expierence compiling stuff can point me in the right direction.

-Juice

---

