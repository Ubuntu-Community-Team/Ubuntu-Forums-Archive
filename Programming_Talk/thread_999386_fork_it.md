---
title: "fork it"
date: 2008-12-01
forum: Programming Talk
---

### Post by overtime on 2008-12-01
How do i fork in Dev C++?

What do i have to #include in order for the fork to work?

---

### Post by snova on 2008-12-01
I have doubts that this will be possible at all. DevC++ knows nothing but Windows, which does not (to my knowledge) have the fork() system call, rather something different.

Either use a Linux-aware IDE, or just a simple text editor even.

The header, I think, is unistd.h.

---

### Post by SeanHodges on 2008-12-03
For instructions on how to fork, see this:

[http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html](http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html)

DevC++ should allow you to type code for forking, just like any IDE or text editor would... I assume you're using DevC++ for Linux ([http://freshmeat.net/projects/dev-cpp/)?](http://freshmeat.net/projects/dev-cpp/)?)

---

