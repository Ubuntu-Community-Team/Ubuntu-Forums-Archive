---
title: "Ubuntu's OpenGL version and Intel G45"
date: 2009-03-08
forum: Programming Talk
---

### Post by glaze on 2009-03-08
I have Intel G45/X4500HD which is a fairly new chipset, but glxinfo shows that my OpenGL version string is 1.4 Mesa 7.2. I think that's why I can't use more advanced features like VBOs or shaders in my OpenGL programs. Direct rendering is enabled and everything works ok, even third party software using shaders etc., but I can't compile my own programs with those features. How can I get these features to work? I'm using Kubuntu 8.10 64-bit.

---

### Post by Sockerdrickan on 2009-03-08
You can dynamically load VBO feaures with glew. Shaders are gonna have to wait for a better driver.

---

### Post by glaze on 2009-03-08
Thanks for the reply. I already found a way to load VBO functions. Example below:
```

#include <GL/glext.h>
...
PFNGLGENBUFFERSARBPROC glGenBuffersARB = (PFNGLGENBUFFERSARBPROC)       SDL_GL_GetProcAddress("glGenBuffersARB");

...
glGenBuffersARB(1, &vboId);

```

---

### Post by Sockerdrickan on 2009-03-08
Yeah that works but in the future you are going to prefer something like this when it gets down to lots of functions:

[php]#include <GL/glew.h>

glewInit();

GLuint vbo;
glGenBuffers(1,&vbo);
//Do stuff
glDeleteBuffers(1,&vbo);[/php][apt://libglew1.5-dev](apt://libglew1.5-dev)

---

