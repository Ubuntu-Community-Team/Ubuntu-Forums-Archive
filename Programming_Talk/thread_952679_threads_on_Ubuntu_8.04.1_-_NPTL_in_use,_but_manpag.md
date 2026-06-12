---
title: "threads on Ubuntu 8.04.1 - NPTL in use, but manpage says LinuxThreads"
date: 2008-10-19
forum: Programming Talk
---

### Post by meonkeys on 2008-10-19
```

$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.7

```

But when I run "man pthread_attr_init" the bottom of the manpage says "LinuxThreads". I thought modern GNU/Linux systems used the Native POSIX Threading Library. Is there maybe another manpage discussing NPTL threading on Ubuntu 8.04.1?

Thanks!
-Adam

---

### Post by joe_bruin on 2008-10-20
Your man page is valid for both.  LinuxThreads and NPTL are kernel-level threading models.  The user interface to both of them is through the pthread library.  There is no man page for NPTL.  The only people who need to care about how NPTL works are the people writing libpthread.  Everyone else should be using pthreads.

Edit: and yes, your system is using NPTL.

---

### Post by meonkeys on 2008-10-20
Thanks for your reply, **joe_bruin**!

Turns out there is another manpage... after installing the **manpages-posix-dev** package I can now do **man 3posix pthread_attr_init**. This brings up the pthread_attr_init/pthread_attr_destroy manpage from the *POSIX Programmer’s Manual*. I guess the LinuxThreads folks wrote their own version (and they live on in the glibc-doc package). I haven't found any specific differences, but since they are different implementations I imagine there will be differ eso far I prefer the *POSIX Programmer’s Manual*.

> **joe_bruin said:**
> Your man page is valid for both.  LinuxThreads and NPTL are kernel-level threading models.

True, they are both kernel-level threading models. As such, they have both kernel and user-space (GNU C Library) portions. But LinuxThreads is no longer implemented in the kernel, it has been superseded by NPTL in kernels >= 2.6.x.

[http://en.wikipedia.org/wiki/LinuxThreads](http://en.wikipedia.org/wiki/LinuxThreads)
[http://pauillac.inria.fr/~xleroy/linuxthreads/](http://pauillac.inria.fr/~xleroy/linuxthreads/)

But I guess I could imagine that the LinuxThreads code still exists in glibc in case you wanted to use a more recent glibc on a system running a 2.4 kernel, for instance.

So, I would agree the LinuxThreads version of the manpage is valid if you are running a kernel that is using LinuxThreads.

---

