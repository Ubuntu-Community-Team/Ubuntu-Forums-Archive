---
title: "[SOLVED] need OpenGL guru's help"
date: 2008-10-23
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-23
I see there are functions for 1D textures in OpenGL. But why? You can't see 1D textures, only 2D!

What is point of 1D textures? I just don't get it.

---

### Post by kjohansen on 2008-10-23
You can apply a 1D texture to a 2 or 3 D object.

You can think of it expanding across the other dimensions


1D texture:
R
G
G
G
G
B

would apply to a 2d and look like:
RRRRRRRRRRRRR
GGGGGGGGGGGGG
GGGGGGGGGGGGG
GGGGGGGGGGGGG
GGGGGGGGGGGGG
BBBBBBBBBBBBB

here is a link with a better explanation in terms of lighting maps in games:
[http://www.gamedev.net/reference/programming/features/celshading/](http://www.gamedev.net/reference/programming/features/celshading/)

---

### Post by crazyfuturamanoob on 2008-10-23
Why not to just have a 2d texture with width 1 then set texture x size huge?

---

### Post by snova on 2008-10-23
Probably some optimization thing. OpenGL is designed to be easily acceleratable; its API reflects the way graphics cards work most efficiently. If that means using 1 dimensional textures, then it will provide that capability.

---

