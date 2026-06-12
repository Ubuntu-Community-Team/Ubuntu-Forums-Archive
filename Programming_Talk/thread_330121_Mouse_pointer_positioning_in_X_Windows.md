---
title: "Mouse pointer positioning in X Windows"
date: 2007-01-02
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-01-02
Hey does anyone know what functions to use to get Xwindows to position the mouse as acertain point?

I tried this in SDL but i want to be able to do this regardless of what window has the focus.

Mike

---

### Post by Houman on 2007-01-02
Hi there,

If you have the libx11-dev package installed (which i am assuming you do since you wanna do X programming) just do a "man XQueryPointer",

regards
Houman

---

### Post by Mickeysofine1972 on 2007-01-03
Thats seems to only return the current coords not set them

Mike

---

### Post by tomchuk on 2007-01-03
man 3 XWarpPointer

---

