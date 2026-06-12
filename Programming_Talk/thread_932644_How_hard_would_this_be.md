---
title: "How hard would this be?"
date: 2008-09-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-09-28
in C/C++ to make a system call or something to increase fan speed...preferably platform independent (simple curiosity) i tried google but could not find anything

---

### Post by Caduceus on 2008-09-28
I don't think any programming problem is inherintly "hard", but for something like that be prepared for a lot of "close to the metal" code, and for that I'd start looking into a C solution, C++ isn't usually used for that sort of thing.

---

### Post by snova on 2008-09-28
First of all, choice of language has nothing to do with it.

Secondly, there isn't a cross-platform solution. Interfacing with device drivers is different on every single platform, for every different type of hardware.

For example, on a Dell Inspiron running Linux, such as my own, I would issue calls to the i8kutils kernel modules via ioctl(). If I were programming for any other OS, the API would be totally different. If I were running on any other model, the driver would be totally different.

So no, there isn't a solution. And yes, it'd be hard.

---

