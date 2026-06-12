---
title: "gdb can't open coredump"
date: 2008-08-14
forum: Packaging and Compiling Programs
---

### Post by roman.simakov on 2008-08-14
Hello,

The first of all, sorry if my thread is offtopic and please move it in correct place.

I use Ubuntu 8.04.1 and compile Firebird2 under it. But previously I install gcc, g++ 4.3.1 sinse 4.2 had problem with optimization.
gdb is native for this version of Ubuntu. 6.8-debian.

Now about my problem,
When I do this, all right:
gdb fb_smp_server
run
<Ctrl-c>
info threads (here I can see function names in stack)
gcore
quit

When I try to open just saved coredump I can't see function names in stack.
gdb fb_smp_server core.1111
info threads (here I can see "????" instead of real function names)

What I do wrong? It seems that gdb can't read symbols from file but in the first case it did?

---

### Post by loell on 2008-08-14
most likely you did not enable debugging options

---

### Post by roman.simakov on 2008-08-14
> **loell said:**
> most likely you did not enable debugging options
Yes. I used release configuration but gcc and g++ are using -g and -ggdb flags. Unfortunally, on real debug build I can't catch a bug. But why when I attach to process or run it under gdb, debug symbols have been readed ok?

---

