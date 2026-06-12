---
title: "using OpenGL display lists to render strings"
date: 2007-10-01
forum: Programming Talk
---

### Post by moshy on 2007-10-01
I have found the FTGL library to be very good at rendering fonts in OpenGL, but I need to be able to do this in between glNewList(1, GL_COMPILE); and glEndList(); calls - which doesn't seem to work.
Can I get this to work?

---

### Post by moshy on 2007-10-02
```
glNewList(1, GL_COMPILE);
font->Render("");
glEndList();
```

duh!

---

