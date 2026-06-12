---
title: "OpenGL stencil questions"
date: 2010-05-13
forum: Programming Talk
---

### Post by kahumba on 2010-05-13
Folks, I just can't get stencils in OpenGL, can anyone please answer these questions?

1) When does a stencil pattern start and end? There doesn't seem to be any glBegin(patern)/glEnd(patern).

2) In the following code, why do we need to use glStencinFunc/Op _twice_, first with the params GL_NEVER/GL_INCR and then with GL_NOTEQUAL/GL_KEEP?

3) In same code, why do we need to increment then keep (GL_INCR/GL_KEEP respectively) the value in the stencil buffer? Which value exactly are we incrementing and then keeping and why do we need to do so..

The code snippet follows and whole code which compiles and runs in 1 file is attached.

[PHP]
void RenderScene(void) {
    GLdouble dRadius = 0.1; // Initial radius of spiral
    GLdouble dAngle; // Looping variable

    // Clear blue window
    glClearColor(0.0f, 0.0f, 1.0f, 0.0f);

    glEnable(GL_STENCIL_TEST);
    glClearStencil(0);
    glClear(GL_COLOR_BUFFER_BIT | GL_STENCIL_BUFFER_BIT);

    // All drawing commands fail the stencil test, and are not
    // drawn, but increment the value in the stencil buffer.
    glStencilFunc(GL_NEVER, 0x0, 0x0);
    glStencilOp(GL_INCR, GL_INCR, GL_INCR);

    // Spiral pattern will create stencil pattern
    // Draw the spiral pattern with white lines. We
    // make the lines  white to demonstrate that the
    // stencil function prevents them from being drawn
    glColor3f(1.0f, 1.0f, 1.0f);
    glBegin(GL_LINE_STRIP);
    for (dAngle = 0; dAngle < 360.0; dAngle += 0.1) {
        glVertex2d(dRadius * cos(dAngle), dRadius * sin(dAngle));
        dRadius *= 1.002;
    }
    glEnd();

    // Now, allow drawing, except where the stencil pattern is 0x1
    // and do not make any further changes to the stencil buffer
    glStencilFunc(GL_NOTEQUAL, 1.0f, 1.0f);
    glStencilOp(GL_KEEP, GL_KEEP, GL_KEEP);

    // Now draw red bouncing square
    // (x and y) are modified by a timer function
    glColor3f(1.0f, 0.0f, 0.0f);
    glRectf(x, y, x + rsize, y - rsize);

    // All done, do the buffer swap
    glutSwapBuffers();
}
[/PHP]It's from OpenGL superbible 4th edition, chapter 3.

---

