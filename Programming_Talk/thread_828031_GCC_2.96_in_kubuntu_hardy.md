---
title: "GCC 2.96 in kubuntu hardy"
date: 2008-06-13
forum: Programming Talk
---

### Post by pavallokazzo on 2008-06-13
I need Gcc 2.96 to compile speech tools and festival... at this point seems the only way to run it.
How can I obtain it?

---

### Post by nvteighen on 2008-06-13
> **pavallokazzo said:**
> I need Gcc 2.96 to compile speech tools and festival... at this point seems the only way to run it.
How can I obtain it?

Are you really sure you can't do that with gcc 4.2.3 (the version in the repos)?

---

### Post by pavallokazzo on 2008-06-15
can you try?

---

### Post by ad_267 on 2008-06-15
Why do you think you need 2.96? Have you tried with the latest version? Most things you need for compiling are in the build-essentials package.

---

### Post by pavallokazzo on 2008-06-16
> **ad_267 said:**
> Why do you think you need 2.96? Have you tried with the latest version? Most things you need for compiling are in the build-essentials package.

[http://ubuntuforums.org/showthread.php?t=821204](http://ubuntuforums.org/showthread.php?t=821204)
```
../include/EST_TMatrix.h:310: warning: friend declaration ‘std::ostream& operator<<(std::ostream&, const EST_TMatrix<T>&)’ declares a non-template function
slib.cc: In function ‘void gc_mark_and_sweep()’:
slib.cc:1088: warning: dereferencing type-punned pointer will break strict-aliasing rules
gmake[1]: *** [slib.o] Error 1
gmake: *** [siod] Error 2

```

[http://www.cstr.ed.ac.uk/projects/festival/](http://www.cstr.ed.ac.uk/projects/festival/)
INSTALL
Festival should run on any standard Unix platform.  It has already run
on Solaris, SunOS, Linux and FreeBSD.  It requires a C++ compiler (GCC
2.7.2, 2.8.1, 2.95.[123], 3.2.3 3.3.2 RedHat "gcc-2.96" and gcc 3.3 are
our standard compilers) to install. A port to Windows XP/NT/95/98 and
2000 using either Cygnus GNUWIN32 and Visual C++ is included, this is
still new but many people are successfully using it.


I noted now 3.2 and 3.3.2 are supported, didn't tried that but I did tried 3.1 and won't work...
Will try the gcc 3.2 and I'll let you know

---

