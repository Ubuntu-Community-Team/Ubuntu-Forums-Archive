---
title: "X11 events"
date: 2010-07-01
forum: Programming Talk
---

### Post by sushiboxdev on 2010-07-01
I am developing an OpenGL library for game development that uses X11 for Linux. Everything is working fine but for some reason I cannot handle the close event (when you click the little x at the top of the window). All of my other events are working just fine. Here is my code.

This is at the end of my window creation function.
```

wmDeleteMessage = XInternAtom(objDisplay, "WM_DELETE_WINDOW", false);
XSetWMProtocols(objDisplay, objWindow, &wmDeleteMessage, 1);

```

This isn't all of my events, but its the one that matters.
```

switch(objEvent.type)
{
    case ClientMessage:
        if(objEvent.xclient.data.l[0] == wmDeleteMessage)
        {
            bRunning = true;
        }
    break;
}

```

I really don't know why this isn't working so some insight would be nice. Thanks in advanced! By the way, I just started dabbling into X11 so if I am making a really dumb mistake be nice hah.

---

### Post by sushiboxdev on 2010-07-02
Bump: This is really important and its driving me up the wall.

---

### Post by pbrane on 2010-07-02
I'm not sure what you're trying to do with the delete event. It looks like you are simply setting *bRunning* to *true*. Are you trying to actually close the program?

---

### Post by sushiboxdev on 2010-07-02
Yeah, setting bRunning to false closes the application, but the event seems like its never fired when I click the "X" at the top of the window. But I tried binding the escape key to do the same exact thing and that works fine, its just that specific event...

---

### Post by vek on 2010-07-03
Have you considered looking at the source code for SDL or GLFW?  They both handle this case and are both opengl libraries, too. 

apt-get source libsdl1.2debian 
I think

---

### Post by sushiboxdev on 2010-07-04
Yeah I am familiar with SDL but there is a reason I am using X11 and not glut or SDL. I solved the issue by recoding a lot of my window creation function.

---

