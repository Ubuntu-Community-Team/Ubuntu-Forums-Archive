---
title: "[Python] High-level opengl library?"
date: 2008-10-02
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-02
Is there any frontends/libraries/wrappers for pyopengl? I find pygame can't draw textured polygons and is a bit slow for some things, so I gotta use pyopengl.

But pyopengl is so damn hard, and there are no good tutorials for it. But perhaps there is a library that has some high-level macros for using pyopengl?

And by the way, I don't want 3d graphics, just simple 2d polygons. I tried google but found no good pyopengl tutorials.

I want either a high-level macro library for pyopengl, **OR** then a lot good pyopengl tutorials for noobs & beginners, or perhaps another way to draw textured 2d polygons?

Edit: Let me rephrase: ***_How can I draw a 2D triangle with a bitmap texture laid on?_***

---

### Post by snova on 2008-10-02
PyOpenGL isn't a library in of itself, it's a Python wrapper around the OpenGL api, which is natively written in C. Don't go looking for tutorials on PyOpenGL, look for OpenGL. Better yet, get a book- OpenGL is immensely rich and complex.

Either you need to learn the basics of the OpenGL API, or you want a graphics engine.

OpenGL *does* do texturing. You just have to know how to make it do what you want. I have no idea myself, I only know the basics of vertexes.

In the case of the graphics engine, get out of PyOpenGL and look into Panda3D or Ogre. Both have Python wrappers; Panda is even *meant* to be used in Python.

---

### Post by nihilocrat on 2008-10-02
I'm not sure if this is the sort of thing you are looking for, but perhaps you should look into [pyglet]("http://pyglet.org") and/or [cocos2d]("http://cocos2d.org"). The aim is to use OpenGL for the sake of 2d graphics.

---

### Post by crazyfuturamanoob on 2008-10-03
But I just want to render a textured 2d vertex on pygame surface. Think this is possible?

---

