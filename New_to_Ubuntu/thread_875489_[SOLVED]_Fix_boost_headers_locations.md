---
title: "[SOLVED] Fix boost headers locations"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by Sydius on 2008-07-30
I had boost installed with apt-get but decided to remove it and manually build/install it.  I think it went okay, but it put everything in /usr/local, and now my code can't find the headers.

How do I go about making it so that they can be found?

---

### Post by Sydius on 2008-07-30
I tried ldconfig, but I don't think that helped--it's only for library object files, I assume.

---

### Post by Sydius on 2008-07-30
Nevermind, I just used the -I directive for g++.

---

