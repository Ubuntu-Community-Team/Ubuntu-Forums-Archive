---
title: "Non-square textures in OpenGL."
date: 2009-04-21
forum: Programming Talk
---

### Post by hessiess on 2009-04-21
After reading around on the web it appears that OpenGL should be able to handle non-square textures so long as they are a power of two. Howeaver if I try to display a non-square texture I am getting a funny interlace like effect:

[IMG]http://www.hessiess.dyndns.org/files/nsquaretex_artifact.png[/IMG]

I assume that it has something to do with how I have implemented textures in Quad-Ren, but it is strange as square textures work perfectilly.

---

### Post by cb951303 on 2009-04-21
non-square texture support came as an extension. if your card doesn't support it then you won't have it :)

---

### Post by hessiess on 2009-04-21
> **cb951303 said:**
> non-square texture support came as an extension. if your card doesn't support it then you won't have it :)

I know, but according to the nvidia-settings applet, non power of two textures *are* supported, which must mean that non-square textures should also be available.

Do I have to enable it or something?

edit

```

glxinfo | grep non_power

```

lists

```

GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 

```

---

### Post by hessiess on 2009-04-24
Any idea why this is happing when non-square textures are supported by my card(7600GS)?

---

### Post by Zugzwang on 2009-04-24
> **hessiess said:**
> Any idea why this is happing when non-square textures are supported by my card(7600GS)?

What makes you think that "non-power-of-two textures support" is the same as "non-square texture support"? 

The first property should mean that for example textures of size 18x177 are supported but has for example nothing to do with triangular textures, or am I wrong?

---

### Post by hessiess on 2009-04-24
> **Zugzwang said:**
> What makes you think that "non-power-of-two textures support" is the same as "non-square texture support"? 

The first property should mean that for example textures of size 18x177 are supported but has for example nothing to do with triangular textures, or am I wrong?

Where did I say anything about triangular textures? As far as I know there are no image formats that are capable of storing images which are not square/rectangular. If my card can handle textures which are NO-POT, i.e. 800*600, then it should also be able to handle textures which are a power of two and non-square, but currently neither are working.

---

### Post by Zugzwang on 2009-04-24
> **hessiess said:**
> Where did I say anything about triangular textures? As far as I know there are no image formats that are capable of storing images which are not square/rectangular. If my card can handle textures which are NO-POT, i.e. 800*600, then it should also be able to handle textures which are a power of two and non-square, but currently neither are working.

Sorry, I misinterpreted your question. Actually, you might want to try running a different program which also makes use of them and see if it works there. However, I don't know of any.

---

### Post by pinyotae on 2009-10-30
(I know that my reply is too late, but it may help others who hit this page later.)


There is another related OpenGL feature.  It is[ _GL_ARB_texture_rectangle_]("http://www.opengl.org/registry/specs/ARB/texture_rectangle.txt")

It may have other equivalent like 
EXT_texture_rectangle and
NV_texture_rectangleFor more info:
[http://www.opengl.org/registry/specs/ARB/texture_rectangle.txt](http://www.opengl.org/registry/specs/ARB/texture_rectangle.txt)

and
[http://stackoverflow.com/questions/318194/display-arbitrary-size-2d-image-in-opengl](http://stackoverflow.com/questions/318194/display-arbitrary-size-2d-image-in-opengl)

---

