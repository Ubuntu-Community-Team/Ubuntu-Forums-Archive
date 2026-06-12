---
title: "Missing glu.h!"
date: 2008-06-12
forum: Programming Talk
---

### Post by PureW on 2008-06-12
Hello, I've got this problem with a missing glu.h. I have these libraries installed:
[I][B] mesa-common-dev 
libgl1-mesa-dev 
libx11-dev 
build-essential[/B][/I]
Do I need any other libs?

The reason I ask is because there is no glu.h on the computer and thus I get errors when compiling opengl-programs.
> ls /usr/include/GL/
glext.h  gl.h  gl_mangle.h  glpng.h  glxext.h  glx.h  glx_mangle.h

glxgears runs fine and the drivers are correctly installed (I think).
> glxinfo|grep render
**direct rendering: Yes**
OpenGL renderer string: GeForce 6800 LE/AGP/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 


---

### Post by Lster on 2008-06-12
I had the same problems - which were solved when reading this post:

[http://ubuntuforums.org/showpost.php?p=2365634&postcount=2](http://ubuntuforums.org/showpost.php?p=2365634&postcount=2)

---

### Post by PureW on 2008-06-15
> **Lster said:**
> I had the same problems - which were solved when reading this post:

[http://ubuntuforums.org/showpost.php?p=2365634&postcount=2](http://ubuntuforums.org/showpost.php?p=2365634&postcount=2)

Thank you, the missing package was the libglu1-mesa-dev

---

