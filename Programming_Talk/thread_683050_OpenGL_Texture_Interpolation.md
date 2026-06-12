---
title: "OpenGL Texture Interpolation"
date: 2008-01-30
forum: Programming Talk
---

### Post by Lster on 2008-01-30
Hi everyone yet again!

It seems I've been running into problem after problem with extensions  which I parted put down to the poor documentation I could find. Although multitexturing is easy for many simple things I am struggling to even comprehend how to interpolate four textures about a square as I need to. I can do a multipass (?) algorithm which I find too slow so I need to achieve it in some other way.

I considered specifying a texture opacity on each vertex (if possible) and using four texture units, which would achieve this. That way I could define the alpha of each texture unit at all the vertexes to achieve this.

If this is possible, how? I have found GL_TEXTURE_ENV_COLOR and a whole load of settings but have no idea what they all do. Any pointers, example or ideas would be great.

Thank you,
Lster

---

### Post by Lster on 2008-01-31
Sorry to be asking for so much help recently but I can't find anything on it. I think that there must be a way to do texture interpolation with multitexturing but I can't find any resources on it.

---

### Post by Shuffle777 on 2008-04-11
Hi!

Maybe I'm a bit late, but still I answer that you certainly can do what you want using CG shaders.
I don't know if you can do it using "plain" OpenGL (I'm really not a guru though :) ).

But of course, you'll need that CG toolkit from nVidia (sudo aptitude install nvidia-cg-toolkit) and then you have to learn using it... There are plenty of tutorials on the Web (especially NeHe's)

This may not be the way you want to go, so I won't go deeper in that subject. But if you are interested, I may help you further.

There is also GLSL, but I've never used it so I can't help you there.

Also, if you already managed to get it right, I'm interested in the solution (always good to learn something).

---

