---
title: "OpenGL programming / questions about extensions"
date: 2011-12-30
forum: Packaging and Compiling Programs
---

### Post by fr4nko on 2011-12-30
Hi all,

I'm playing a little bit with opengl programming on linux and I've some simple questions.

The glxinfo gives me the following for the OpenGL version:

> OpenGL version string: 2.1 Mesa 7.11


I guess this means that my system support OpenGL 2.1 using the Mesa implementation. Can someone confirm this is correct ?

The, if I look at GL/gl.h from /usr/include I found something like:

> 
#define GL_VERSION_1_1   1
#define GL_VERSION_1_2   1
#define GL_VERSION_1_3   1
#define GL_ARB_imaging   1


so the GL_VERSION_xx are not defined for 1.4, 1.5, 2.0. So my question is, why the header file does not include the definitions for GL versions up to 2.0 (at least) ?
I'm supposed to change the GL/gl.h header file with something more appropriate ?

Please note that if I do nothing I get this sort of linker warning:

> /usr/bin/ld: Warning: type of symbol `glBlendFuncSeparate' changed from 2 to 1 in ../OGLD/libOGLD.a(OGLDif.o)

and I guess that this is related to the missing declarations for opengl 1.4+.

For information, I'm running on a standard ubuntu installation with oneiric. My graphical card in an ATI radeon mobility 2300 and I'm using the driver provided by X.org, here some more informations from glxinfo:

> OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20


Any help will be greatly appreciated. Thanks in advance.

Francesco

---

