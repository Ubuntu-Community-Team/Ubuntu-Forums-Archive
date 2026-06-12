---
title: "Trying to compile mesa, configure fails on drigl."
date: 2010-03-19
forum: Programming Talk
---

### Post by Paradox Uncreated on 2010-03-19
checking for DRIGL... configure: error: Package requirements (x11 xext xxf86vm xdamage xfixes) were not met:


Where do I find this package, so I can compile it?

---

### Post by snova on 2010-03-19
> **Paradox Uncreated said:**
> checking for DRIGL... configure: error: Package requirements (x11 xext xxf86vm xdamage xfixes) were not met:


Where do I find this package, so I can compile it?

Why are you trying to compile Mesa? I can think of no good reason at all.

If you need the OpenGL headers, install the **mesa-common-dev** package.

---

### Post by Paradox Uncreated on 2010-03-20
I am compiling the latest version, with optimizations, to test something. Unfortunately the packages related to this in the repository seems out of date.

---

### Post by cubeist on 2010-03-20
There is always a good reason to test unstable software! :P

You will need to grab some packages from git to compile the latest mesa.  They should all be here
```
http://cgit.freedesktop.org/
```

If you don't know how to compile from git you may be in over yer head!

A couple notes of caution.  Since you have to install the latest xserver files, you may not want to do this on your everyday-system as other packages/programs may not work.

---

