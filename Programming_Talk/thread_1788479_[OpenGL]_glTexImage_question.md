---
title: "[OpenGL] glTexImage question"
date: 2011-06-22
forum: Programming Talk
---

### Post by t1497f35 on 2011-06-22
Hi,
> 
void glTexImage2D(GLenum  target,  GLint  level,
GLint  internalFormat,   //THIS
GLsizei  width,  GLsizei  height,  GLint  border,
GLenum  format,        //AND THIS ONE
GLenum  type,  const GLvoid *  data);
Why is "internalFormat" of type "GLint", while "format" is a "GLenum"? Since they both share same values like GL_RED, GL_RGB GL_RGBA etc shouldn't they be of same type (either GLenum or GLint) ?

---

