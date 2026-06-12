---
title: "Hello, I am not able to install VTK in UBUNTU Xenial 16.04."
date: 2016-12-29
forum: Packaging and Compiling Programs
---

### Post by Semn on 2016-12-29
I use the following package:

[https://launchpad.net/ubuntu/+source/vtk/5.10.1+dfsg-2.1build1](https://launchpad.net/ubuntu/+source/vtk/5.10.1+dfsg-2.1build1)

vtk_5.10.1+dfsg.orig.tar.gz

And install using cmake.

I get this after 69% completion:

```
 69%] Building CXX object Rendering/CMakeFiles/vtkRendering.dir/vtkGenericOpenGLRenderWindow.cxx.o
[ 69%] Building CXX object Rendering/CMakeFiles/vtkRendering.dir/vtkXOpenGLRenderWindow.cxx.o
In file included from /usr/include/GL/glx.h:333:0,
                 from /home/sem/Downloads/vtk-5.10.1/Rendering/vtkXOpenGLRenderWindow.cxx:31:
/usr/include/GL/glxext.h:480:143: error: &#8216;GLintptr&#8217; has not been declared
 typedef void ( *PFNGLXCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLenum readTarget, GLenum writeTarget, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                               ^
/usr/include/GL/glxext.h:480:164: error: &#8216;GLintptr&#8217; has not been declared
 typedef void ( *PFNGLXCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLenum readTarget, GLenum writeTarget, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                                                    ^
/usr/include/GL/glxext.h:480:186: error: &#8216;GLsizeiptr&#8217; has not been declared
 typedef void ( *PFNGLXCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLenum readTarget, GLenum writeTarget, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                                                                          ^
/usr/include/GL/glxext.h:481:148: error: &#8216;GLintptr&#8217; has not been declared
 typedef void ( *PFNGLXNAMEDCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLuint readBuffer, GLuint writeBuffer, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                                    ^
/usr/include/GL/glxext.h:481:169: error: &#8216;GLintptr&#8217; has not been declared
 typedef void ( *PFNGLXNAMEDCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLuint readBuffer, GLuint writeBuffer, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                                                         ^
/usr/include/GL/glxext.h:481:191: error: &#8216;GLsizeiptr&#8217; has not been declared
 typedef void ( *PFNGLXNAMEDCOPYBUFFERSUBDATANVPROC) (Display *dpy, GLXContext readCtx, GLXContext writeCtx, GLuint readBuffer, GLuint writeBuffer, GLintptr readOffset, GLintptr writeOffset, GLsizeiptr size);
                                                                                                                                                                                               ^
Rendering/CMakeFiles/vtkRendering.dir/build.make:5894: recipe for target 'Rendering/CMakeFiles/vtkRendering.dir/vtkXOpenGLRenderWindow.cxx.o' failed
make[2]: *** [Rendering/CMakeFiles/vtkRendering.dir/vtkXOpenGLRenderWindow.cxx.o] Error 1
CMakeFiles/Makefile2:3270: recipe for target 'Rendering/CMakeFiles/vtkRendering.dir/all' failed
make[1]: *** [Rendering/CMakeFiles/vtkRendering.dir/all] Error 2
Makefile:138: recipe for target 'all' failed
```

---

### Post by howefield on 2016-12-29
Moved to the "*Packaging and Compiling Programs*" forum for a better fit.

---

### Post by steeldriver on 2016-12-29
May we know why you are trying to build it from source, when it's already in the repository?

Did you install all the required build dependencies?

---

### Post by mc4man on 2016-12-29
When possible one should check if Debian/Ubuntu has patches, so in this case there are a number of them, specific to this issue would likely be "GLX_GLEXT_LEGACY.patch"
For info's sake only  it is this,  though not sure why you'd build what was already built/packaged properly in Ubuntu

```
--- vtk.orig/Rendering/vtkOpenGL.h
+++ vtk/Rendering/vtkOpenGL.h
@@ -19,6 +19,7 @@
 
 // To prevent gl.h to include glext.h provided by the system
 #define GL_GLEXT_LEGACY
+#define GLX_GLEXT_LEGACY
 #if defined(__APPLE__) && (defined(VTK_USE_CARBON) || defined(VTK_USE_COCOA))
 # include <OpenGL/gl.h> // Include OpenGL API.
 #else
--- vtk.orig/Rendering/vtkXOpenGLRenderWindow.cxx
+++ vtk/Rendering/vtkXOpenGLRenderWindow.cxx
@@ -27,7 +27,7 @@
 
 // define GLX_GLXEXT_LEGACY to prevent glx.h to include glxext.h provided by
 // the system
-//#define GLX_GLXEXT_LEGACY
+#define GLX_GLXEXT_LEGACY
 #include "GL/glx.h"
 
 #include "vtkgl.h"
```

---

