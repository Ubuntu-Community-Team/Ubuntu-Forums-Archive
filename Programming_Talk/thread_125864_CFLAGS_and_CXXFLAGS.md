---
title: "CFLAGS and CXXFLAGS?"
date: 2006-02-05
forum: Programming Talk
---

### Post by arjun on 2006-02-05
Hi.  How can I edit my CFLAGS and CXXFLAGS variables in Ubuntu and Debian based OSes? I want to compile some software that is customized to my system.

---

### Post by engla on 2006-02-05
Well don't you do however you always do when you compile, regardless of distro?

I would use something like
$ CFLAGS= -Os ./configure

---

