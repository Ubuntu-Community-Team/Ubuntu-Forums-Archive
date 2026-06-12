---
title: "XUbuntu 13.04 OpenGL Problems"
date: 2013-09-10
forum: Programming Talk
---

### Post by mike94 on 2013-09-10
I am trying to use glEdgeFlag() using openGL libraries, and I have been able to use all of the basic functions working normally glEnable(), glVertex*(), glColor*(), etc. 

However with this simple line of code there it should be possible to "remove" the right edge of the triangle in the code below, but it does not occur on my system. I am currently running XUbuntu 13.04 on a virtual machine in Virtualbox.

Here is my display function:
```
void display (void)
{
    glClear (GL_COLOR_BUFFER_BIT);
    glPolygonMode (GL_FRONT, GL_LINE);

    glColor3f(1.0f,0.0f,0.0f); // red outline triangle
    glBegin(GL_POLYGON);
    glEdgeFlag(GL_TRUE);
    glVertex2s(50,40); // visible
    glEdgeFlag(GL_FALSE);
    glVertex2s(40,60); // invisible (right edge)
    glEdgeFlag(GL_TRUE);
    glVertex2s(30,40); // visible 
    glEnd();

    glFlush();
}
```

[IMG]http://i.imgur.com/WSXiPUP.png[/IMG]

---

### Post by Toz on 2013-09-11
Hello and welcome to the forums.

I've moved this thread to the more appropriate **Programming** subforum to hopefully attract the kind of responses you are looking for.

---

### Post by mike94 on 2013-09-21
Anyone? I could really use some help on this. Does it look like a virtualization problem with Xubuntu and OpenGl? I do have the latest OpenGL libraries. 
Or does my glEdgeFlag() code look wrong and if not why could it be producing this result?

Thanks.

---

