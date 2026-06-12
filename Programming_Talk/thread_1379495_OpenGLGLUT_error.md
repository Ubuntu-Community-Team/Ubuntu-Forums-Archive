---
title: "OpenGL/GLUT error"
date: 2010-01-12
forum: Programming Talk
---

### Post by TBBucs on 2010-01-12
I'm new to OpenGL and am trying to compile and run a program that I found in a tutorial.  It compiles, but when I run it, I get this message:

```
freeglut (./basicshapes):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
Major opcode of failed request:  4 (X_DestroyWindow)
Resource id in failed request:  0x0
Serial number of failed request:  20
Current serial number in output stream:  23

```From what I've read in other places, it seems that this usually refers to a problem with my graphics card and OpenGL, but when I check the OpenGL/GLX Information tab of my X Server settings, it says **Direct Rendering: Yes**, which I understand to be what I'm looking for.

This is my glInitDisplayMode line:

```
glutInitDisplayMode(GL_DOUBLE | GL_RGB | GL_DEPTH);
```Like I said, I'm following a tutorial, so I'm not yet sure what those parameters actually do, but I've read that that is sometimes the problem.

Thoughts?

---

### Post by Senesence on 2010-01-12
Could you post the code?

---

### Post by TBBucs on 2010-01-12
Ah, I actually just figured it out.  This line:

```
glutInitDisplayMode(GL_DOUBLE | GL_RGB | GL_DEPTH);
```

...should be

```
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB | GLUT_DEPTH);
```

That's one of the risks of typing it out by hand instead of copying and pasting :)  Thanks for your response, though.

---

