---
title: "Opengl, Stencil Buffer &amp; Gstreamer"
date: 2010-02-03
forum: Programming Talk
---

### Post by Eirel on 2010-02-03
Hi Everybody

I'm actually working on a c++ program which consist in modifying gstreamer's opengl plugins. By this I mean that I've changed the glimage drawing function, and included video texture in my scene. By now, I would like to have some reflexion on this scene, but dunno how to activate stencil buffer in gstreamer. 
I know I've got to change the attribute given to glXChooseVisual function in gstglwindow_x11.c, but have no idea on what I should set. i've already try to give some value to GLX_DEPTH_SIZE and GLX_STENCIL_SIZE, but it does'nt do anything, or the cure is even worst than the illness. 

Hope somebody will be able to help me...I'm quite blocked lol

thx

---

