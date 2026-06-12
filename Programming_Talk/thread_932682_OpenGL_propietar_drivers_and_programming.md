---
title: "OpenGL propietar drivers and programming"
date: 2008-09-28
forum: Programming Talk
---

### Post by trunks14 on 2008-09-28
Hi!, here's my question:

When you install a propietary driver for a video card, How do you program oepngl programs without using mesa, to get the advantage of the hardware acceleration...in other words, do you get the .so and .a libraies with a propietary driver? or how do you correctly program something that uses the hardware acceleration?

---

### Post by snova on 2008-09-28
You don't have to do anything. The proprietary drivers expose the same OpenGL api as any other implementation, closed source or not. They simply shift more of the work to the GPU is all. It's transparent.

If you were referring to linking with the correct libraries, the package manager automatically replaces the Mesa driver with the new one, and all programs use it whether they know it or not. They are binary compatible.

---

