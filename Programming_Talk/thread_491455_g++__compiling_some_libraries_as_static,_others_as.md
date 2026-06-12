---
title: "g++ : compiling *some* libraries as static, others as dynamic"
date: 2007-07-03
forum: Programming Talk
---

### Post by aks44 on 2007-07-03
I'm planning on migrating a PHP web application to a C++ CGI.

As you may guess, my web host only provides a few shared libraries (libc, libstdc++, ...) so I need to be able to specify which libraries are linked statically, and which ones are linked dynamically.

I really can't afford a ~900k binary (compiled with -static, then stripped) for a simple "Hello world" CGI...

Being kinda new to Linux and g++, I'm having trouble configuring the compiler to my needs. :(

Any pointers (no pun intended) would be appreciated.

---

### Post by PuckStopper31 on 2007-07-03
The linker commands allow you to specify libraries to be included and how they are to be included.

PS

---

### Post by aks44 on 2007-07-03
Thanks PuckStopper31, but would you mind to elaborate on this please?

I have gone through the linker section of the g++ manual, and didn't found how to solve that problem.

According to the tests I made (I checked the compiled binary with ldd),

**g++ file.cpp -o out.a -l somelib**    will dynamically link somelib, but also libc, libstdc++ etc, while

**g++ file.cpp -o out.a -l somelib -static**    will statically link everything.


What I want is statically linking somelib, while libc, libstdc++ etc are still dynamically linked.

Looks like I am missing something obvious...

---

### Post by hod139 on 2007-07-03
gcc, to my knowledge, will always try and link against the dynamic library even if the static library exists and you ask it to use the static lib.

The command that you are suppose to use would be something like:
```

g++ file.cpp -o out  -static -lX11 -dynamic -lm
```
which is suppose to statically link libX11 and dynamically link libm, but I'm pretty sure gcc would still link X11 dynamically.  

Good luck.

---

### Post by geraldm on 2007-07-04
for older compiler/linkers, the rule was that the command line entries before the
source were dynamic; after the source only static would be linked.  In more
recent tools, you need to look at the linker used, and its keywords: -Bdynamic -Bstatic
and others.  The keyword governs for all libraries following it.  "info ld"  should
give the details.
Gerald

---

### Post by aks44 on 2007-07-06
Thanks for the answers (and sorry for the late reply).

For the record, here's the command line that does what I wanted :

```
g++ file.cpp -o out -Wl,-Bstatic -lsomestaticlib -Wl,-Bdynamic
```

The last **-Wl,-Bdynamic** switch is needed to avoid linker errors on the shared system libraries (libc, libgcc_s, libstdc++, ...).

---

