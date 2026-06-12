---
title: "Problem with OpenGL glTranslatef"
date: 2008-01-03
forum: Programming Talk
---

### Post by Fixman on 2008-01-03
Im a very (very) n00b to OpenGL, and started using it some days ago. I always used glLoadIdentity and glVertex3f to draw my shapes, but I preferred using glTranslatef to move them, instead of moving each vertex individually. However I noted that, if I had a shape that I cleared and redrew many times, but with the z param of the glTranslatef each time less, the shape would "go to the middle of the screen" gradually, each time it was farer. Is there any way to address this?

---

### Post by bsenftner on 2008-01-03
that moving to the center is the 3D perspective effect. If you don't want perspective in your 3D, switch to an orthographic camera. 

I also strongly suggest that you get a copy of the OpenGL Programming Guide (the "Red Book"). It has examples that explain all this and walk you through the basics. 

good luck.
bsenftner

---

### Post by Wybiral on 2008-01-04
When you use glTranslatef (or any of the OpenGL matrix transformations) you are altering the modelview matrix. When you alter it, it stays altered. For instance:

```

while 1:
    glTranslatef(0.0, 0.0, -1.0)
    # Draw something here

```

The code above will continue to move further away each iteration. In essence, you're accumulating the Z-axis translation. To combat this, you can either push the matrix onto the matrix stack and pop it off (preserving the original matrix) or you can load the identity matrix each iteration.

Push/Pop
```

while 1:
    glPushMatrix()
    glTranslatef(0.0, 0.0, -1.0)
    # Draw something here
    glPopMatrix()

```

Reload Identity
```

while 1:
    glLoadIdentity()
    glTranslatef(0.0, 0.0, -1.0)
    # Draw something here

```

---

