---
title: "[CPP] Can you compile for windows?"
date: 2013-02-22
forum: Programming Talk
---

### Post by horizons187 on 2013-02-22
If I write C++ games on my Linux machine is their an easy way to port them to Windows?

---

### Post by MG&amp;TL on 2013-02-23
Depends how you want to do it, what your preferred build system is (or if you have one at all), and what libraries you use.

In an ideal world, the porting process would go like this:

1) Copy files over to windows system.

2) Recompile using windows version of build tools.

3) Release.

It's typically not that simple though.

---

### Post by NilPointer on 2013-02-23
Typically, you need to put all platform-dependent code into separate module(s) and make versions of it for all target platforms. That way it's going to be relatively easy.

---

