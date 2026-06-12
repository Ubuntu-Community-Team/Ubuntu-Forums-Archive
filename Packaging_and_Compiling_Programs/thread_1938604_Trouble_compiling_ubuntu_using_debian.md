---
title: "Trouble compiling ubuntu using debian"
date: 2012-03-10
forum: Packaging and Compiling Programs
---

### Post by gsfanatic on 2012-03-10
[LEFT]So I'm trying to compile a custom Kernel that allows me to copy /dev/mem into a file so I can process it. I'm running into issues with making the packages using the following guide:
[http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/](http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/)

When I get to 
skipabi=true skipmodule=true fakeroot debian/rules binary-i7
It fails and tells me that it cannot find perf/perf, despite the fact that it compiles when I go to that file and use make. In addition, when I tried to unpackage without it, the /dev/mem setting I fixed in editconfig didn't take. Any advice?
[/LEFT]

---

### Post by Bachstelze on 2012-03-12
In general if it's just for myself I compile my kernels the old way (make bzImage; make modules; sudo make modules_install; sudo make install). No need to bother with the packaging stuff, and it takes much less time.

---

