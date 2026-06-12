---
title: "Package fails to link on arm"
date: 2015-09-10
forum: New to Ubuntu
---

### Post by kkotamarthy on 2015-09-10
[SIZE=3]Hello,

When I am trying to compile a package on arm64, It gives me the error   
**hidden symbol 'pthread_atfork' in /usr/lib/aarch64-linux-gnu/libpthread_nonshared.a (pthread_atfokr.oS) is referenced by DSO. fatal link failed:Bad value.**

**gcc version 4.8.2 (Ubuntu/Linaro 4.8.2-19ubuntu1)**

I tried replacing -lpthread with -pthread in make file which of no use. I also tried to cross-compile the package and then run on arm which even resulted in the same error.I have been searching for a solution couldnot find any. The package works well with linux-x86.  …              

Let me know if you need any more information.

Thanks in advance.[/SIZE]

---

