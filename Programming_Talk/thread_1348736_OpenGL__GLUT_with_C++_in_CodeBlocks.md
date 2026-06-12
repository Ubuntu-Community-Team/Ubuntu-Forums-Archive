---
title: "OpenGL / GLUT with C++ in Code::Blocks"
date: 2009-12-07
forum: Programming Talk
---

### Post by example6 on 2009-12-07
So I've got Code::Blocks, I've installed all the GLUT libraries I need, but I really just don't know where they are located or how to use them in a project.

Any help would be greatly appreciated, thanks!

---

### Post by TheBuzzSaw on 2009-12-07
Just make sure you link to GL, GLU, and glut.

Also:
```
#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>
```

Boom. Off you go!

---

### Post by Zugzwang on 2009-12-08
As far as linking against the library is concerned: It's in the manual of Code::Blocks, section 1.1.13:

[http://www.codeblocks.org/docs/manual_en.pdf](http://www.codeblocks.org/docs/manual_en.pdf)

For finding out the filenames of the library files, you can use the packages.ubuntu.com webpage, e.g.:

[http://packages.ubuntu.com/karmic/i386/freeglut3/filelist](http://packages.ubuntu.com/karmic/i386/freeglut3/filelist)

---

### Post by TheBuzzSaw on 2009-12-08
Do not link directly to the filename!

Link to the shorthand versions I listed above: GL, GLU, glut

---

### Post by Zugzwang on 2009-12-08
> **TheBuzzSaw said:**
> Do not link directly to the filename!

Link to the shorthand versions I listed above: GL, GLU, glut

...as written in the manual.

---

### Post by TheBuzzSaw on 2009-12-08
Ah, I misread your comment. ^_^;

---

