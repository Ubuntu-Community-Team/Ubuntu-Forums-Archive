---
title: "X error trying to create window using GLX 1.3 functions"
date: 2008-07-11
forum: Programming Talk
---

### Post by PaladinOfKaos on 2008-07-11
I'm trying to create a GLX context and window using the GLX 1.3 (new-style) functions. Everything seems to be going smoothly, until I try to create my X window (using XCreateWindow). I get an X error: Bad Request.

I think the problem is in the 'class' argument. The value I'm using (InputOutput) doesn't match the value found in the XVisualInfo struct I'm getting from GLX. I can't use the value in the struct, though - it's '4', which isn't a valid value for the class argument. I get an X error to that effect if i try to use it.

The full code is [here](http://pastebin.com/d5d85ab8) (pastebin.com).

---

