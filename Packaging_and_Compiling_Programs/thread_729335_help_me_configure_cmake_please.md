---
title: "help me configure cmake please"
date: 2008-03-19
forum: Packaging and Compiling Programs
---

### Post by mr tim esquire on 2008-03-19
Im trying to compile a program using Cmake, slowly adding packages needed
any idea what paths i should use for these:
```
 OPENGL_INCLUDE_DIR             OPENGL_INCLUDE_DIR-NOTFOUND                                                                                 
 OPENGL_gl_LIBRARY                OPENGL_gl_LIBRARY-NOTFOUND                                                                                  
 OPENGL_glu_LIBRARY               OPENGL_glu_LIBRARY-NOTFOUND                                                                                 
 OPENGL_xmesa_INCLUDE_DIR OPENGL_xmesa_INCLUDE_DIR-NOTFOUND                                                                          
```
thanks
:)

---

### Post by WW on 2008-03-20
No guarantees, but you could try installing these packages: libgl1-mesa-dev, libglu1-mesa-dev, mesa-common-dev

---

