---
title: "using software rendering - mesa?"
date: 2011-01-21
forum: Programming Talk
---

### Post by i.n.g.o. on 2011-01-21
Hello.

I wrote a little program based on GTK+ using gtkgl. for the rendering i use shaders. its works fine on my laptop with a real graphics card.
but. i want to use this program and the shaders on an eeepc-T101, which happens not to support shaders when using hardware-accelerated rendering. (well at least i get an error when checking the shader-abilities...)

so. i want to try out software-rendering and see how far i get with this.
what i figured out is, that this should be possible with mesa3d... but how? (could not find any examples...)

so here is the question:
- how do i use a software opengl renderer for my gtk+ project? (mesa3d)
(using llvmpipe should be fast?)

i found "libgl1-mesa-swx11" library in the repository... do i just use this?

thanks for any advice.
i.n.g.o.

---

### Post by i.n.g.o. on 2011-01-21
Found it.

Software renderer was already installed...

just added this to the code and it uses the software renderer:

putenv("LIBGL_ALWAYS_SOFTWARE=1");

---

### Post by hakermania on 2011-01-22
Mark as Solved please :)

---

