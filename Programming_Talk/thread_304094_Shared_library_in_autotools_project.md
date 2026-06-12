---
title: "Shared library in autotools project"
date: 2006-11-21
forum: Programming Talk
---

### Post by lucien on 2006-11-21
Hi,

I'm currently working on a project using the autotools (autoconf, automake, ...). I want to export a specific part of the project as shared library, to keep the executable small, the library exchangeable and especially to learn a bit more about managing a autotools project.
I started using libtool and the library is built correctly. The executable is also linked correctly with it (including all depencies) using the following line in the Makefile.am:
```

foo_LDADD = ../bar/libbar.la

```
But now I have the following problem. The library uses some headers of an other library in its own headers. So I must place their includepath in the Makefile.am of the executable. What would be the "right" way to do this? I know I could add them just the same way I did for the library but I want a more automatic way. So when using further headers in the library their includepaths are automatically added for the executable.

I hope someone understands what I mean. I have really no idea, and can't find any information that helps me.

Greetings,
lucien

---

