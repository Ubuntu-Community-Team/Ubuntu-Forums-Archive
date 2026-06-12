---
title: "[SOLVED] Portable(ish) prefetch in C/C++?"
date: 2008-10-28
forum: Programming Talk
---

### Post by Sydius on 2008-10-28
I've been writing a cache class and would like to play with CPU cache prefetching.  Is there a function/method of doing this above assembly level that might be reasonably expected to work on different (PC) CPUs (AMD, Intel) and, even better, on more than one OS (Linux, Windows)?

---

### Post by Npl on 2008-10-28
Well, gcc has that [Prefetch builtin]("http://gcc.gnu.org/onlinedocs/gcc/Other-Builtins.html"). Its **the** compiler for Linux and versions for Windows exist aswell.

---

### Post by LaRoza on 2008-10-28
> **Npl said:**
> Well, gcc has that [Prefetch builtin]("http://gcc.gnu.org/onlinedocs/gcc/Other-Builtins.html"). Its **the** compiler for Linux and versions for Windows exist aswell.

And OS X.

---

### Post by Sydius on 2008-10-28
If my understanding is correct, it prefetches data just fine, unless it's data pointed to by a pointer, and that's the case I'm in.  I want to prefetch data I only have a pointer for.

Oh, I see.  I can explicitly use the function and not leave it to the optimizer.

---

