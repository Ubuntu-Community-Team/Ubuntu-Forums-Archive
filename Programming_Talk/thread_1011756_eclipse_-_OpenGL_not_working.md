---
title: "eclipse - OpenGL not working"
date: 2008-12-15
forum: Programming Talk
---

### Post by miroslav_karpis on 2008-12-15
Hi All,
I just yesterday installed ubuntu on my pc (now I have dual boot with Vista - where open GL works without problem) and when I want to compile one openGL program the compiler can not find open GL. This is what I get on every openGL function (the variable is different):

Description Resource Path Location Type
‘GL_COLOR_BUFFER_BIT’ was not declared in this scope openGLtest.cpp openGLtest/src 28 C/C++ Problem


please where can I define it?

---

### Post by Kazade on 2008-12-15
Have you included gl.h? ( #include <GL/gl.h> )

---

### Post by miroslav_karpis on 2008-12-15
yes I did...I also checked and gl.h is in the right place (I think) /usr/include/GL

---

### Post by escapee on 2008-12-15
You need to link against OpenGL. I believe (not sure) that its GL and possibly GLU as well.  If you're using glut make sure to link against that as well.  I'm not sure how Eclipse handles adding em in, but through the command line, should be:
```
gcc yourfile.c -lGL -lGLU -lglut -o yourprog
```

I'm sure one of the GL guys will be around soon to verify, but give it a try.

---

