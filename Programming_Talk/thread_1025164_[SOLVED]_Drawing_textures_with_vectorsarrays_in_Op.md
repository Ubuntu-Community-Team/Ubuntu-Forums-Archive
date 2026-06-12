---
title: "[SOLVED] Drawing textures with vectors/arrays in OpenGL"
date: 2008-12-29
forum: Programming Talk
---

### Post by jyaan on 2008-12-29
I can't seem to find any examples like this anywhere. Just about everything uses the extremely slow glBegin() (which I have no interest in using anymore). I have been drawing with glDrawArrays() and a vector of vertices; Isn't there a way to do this with textures?

---

### Post by Wybiral on 2008-12-29
If I understand the question, the same way you use vertex arrays:

[http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/texcoordpointer.html](http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/texcoordpointer.html)

---

### Post by jyaan on 2008-12-29
So far I've been trying this way, but I don't have it quite working yet.

```
glClear(GL_COLOR_BUFFER_BIT);
    glLoadIdentity();

    //glTranslatef(0, 300, 0);
    glEnableClientState(GL_VERTEX_ARRAY);
    glEnableClientState(GL_TEXTURE_COORD_ARRAY);

    glVertexPointer(2, GL_FLOAT, 0, &m_vertices[0]);
    glTexCoordPointer(2, GL_FLOAT, 0, &m_texture[0]);
    glDrawArrays(GL_QUADS, 0, 4);

    glDisableClientState(GL_VERTEX_ARRAY);
    glDisableClientState(GL_TEXTURE_COORD_ARRAY);
```

It's showing pure red with the min/mag filters set, and pure white without either. Not a good sign. :S

---

### Post by jyaan on 2008-12-29
The code I posted is working perfectly. :) I accidentally had the wrong coords for the texture.

---

