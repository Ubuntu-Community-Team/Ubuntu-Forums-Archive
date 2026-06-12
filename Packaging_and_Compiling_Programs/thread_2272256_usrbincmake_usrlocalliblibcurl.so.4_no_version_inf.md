---
title: "/usr/bin/cmake: /usr/local/lib/libcurl.so.4: no version information available (requir"
date: 2015-04-05
forum: Packaging and Compiling Programs
---

### Post by GregPayne on 2015-04-05
I am trying to compile a number of viewers for second life / open sim.

In all cases i am coming across the same issue.

/usr/bin/cmake: /usr/local/lib/libcurl.so.4: no version information available (required by /usr/bin/cmake)
make: *** [all] Error 2
Makefile:75: recipe for target 'all' failed
Finished



how do i fix this?

---

### Post by GregPayne on 2015-05-07
This was fixed by using a different version of Autobuild

---

