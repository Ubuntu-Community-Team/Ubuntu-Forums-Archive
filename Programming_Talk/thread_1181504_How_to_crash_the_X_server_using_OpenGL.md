---
title: "How to crash the X server using OpenGL"
date: 2009-06-08
forum: Programming Talk
---

### Post by HyperHacker on 2009-06-08
1) Create a full-screen 1680x1050 OpenGL window (I used gtkglext but I imagine that doesn't make much difference).
2) Render some things.
3) Use glReadPixels() to read out the entire frame buffer, and bind it to a texture.
4) On the next frame, render a quad with that texture before anything else.
5) Boom!

This is using a GeForce 6200, nVidia driver version 177.82. Anyone else had such a thing happen?

---

