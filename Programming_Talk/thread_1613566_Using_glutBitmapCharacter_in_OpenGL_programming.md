---
title: "Using glutBitmapCharacter in OpenGL programming"
date: 2010-11-04
forum: Programming Talk
---

### Post by Gunnlaugur on 2010-11-04
Hi there.

I'm doing a project in computer graphics in the university where the goal is to create a random maze. I've compleated all the tasks except one small thing.

The player will complete the maze when he finds a diamond I put in a random place. What I then want to do is to disable all the keys on the keyboard (I can do that) and then display a text using the following code fragment. The text is printed but It takes on the color of the lights I have placed around the maze.

How can I make my text print on the board without the text being affected by the lights color?

```

void drawString(float x, float y, float z)
{ 
    glColor3f(1.0, 0.0, 0.0);
    glRasterPos3f(x, y, z);
    char scoreArr[300];
    sprintf_s(scoreArr, "Mission compleated");

    for (const char* c=scoreArr; *c != '\0'; c++)
    {
        glutBitmapCharacter(GLUT_BITMAP_HELVETICA_18, *c); // Updates the position
    }
}

```Thanks in advance.

-Gunnlaugur

---

