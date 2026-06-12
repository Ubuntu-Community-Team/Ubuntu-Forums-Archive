---
title: "Can't found OpenGL headers on ubuntu"
date: 2005-10-11
forum: Programming Talk
---

### Post by martincho on 2005-10-11
Hi, I'm new at ubuntu.
I installed gcc and then SDL. I compiled on ubuntu some SDL games that I made in windows and worked good. But when I tried to compile games that uses SDL and OpenGl, don't works. It seems that there is no OpenGl headers. How can I install opengl headers and libs?
Thanks.

---

### Post by jamesstansell on 2005-10-12
[QUOTE=martincho]Hi, I'm new at ubuntu.
I installed gcc and then SDL. I compiled on ubuntu some SDL games that I made in windows and worked good. But when I tried to compile games that uses SDL and OpenGl, don't works. It seems that there is no OpenGl headers. How can I install opengl headers and libs?
Thanks.[/QUOTE]
It depends on which version of Ubuntu you are using.  For hoary, I'm using the xlibmesa-gl-dev and xlibmesa-glu-dev packages.

The names have changed in breezy, but I think that there should be packages that provide libgl-dev and libglu-dev.  For example, in breezy try the libgl1-mesa-dev package.

---

