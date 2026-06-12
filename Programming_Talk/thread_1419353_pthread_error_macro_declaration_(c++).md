---
title: "pthread error macro declaration (c++)"
date: 2010-03-01
forum: Programming Talk
---

### Post by silentIm on 2010-03-01
Sorry to ask a beginner question. Why i get undeclared error declaration, and i don't see any error macro declaration in pthread.h.

```


#include <pthread.h>
...

int status = pthread_cond_timedwait(&cond, &mutex);
if(status != 0 && status != ETIMEDOUT) // ETIMEDOUT not declared compile-error
...

```The same code is compilable and run on mingw and pthread-win32.
GCC version is 4.4.1.

---

### Post by azagaros on 2010-03-01
type gcc -v to see the version you are compiling under.  

I assume you are compiling on gcc 4.4.1 on a Ubuntu.

It is assuming something is undefined in your code, so the first thing is to start checking versions of the libraries under gcc and or if all the libraries are there.

---

### Post by silentIm on 2010-03-01
so i run  getconf GNU_LIBPTHREAD_VERSION
and it says NPTL 2.10.1

or how do I check for the library version? may be the one that is used by GCC and the one that used by my system is different.

---

### Post by dwhitney67 on 2010-03-01
Error types (macro definitions) such as the one you have listed are typically available if you include <cerrno>, or <errno.h> in C.

---

### Post by silentIm on 2010-03-02
thx dude. Works like charm!

---

### Post by gg31 on 2012-02-08
Thanks :P!

It's <errno.h> in C for add ETIMEDOUT

:)

---

