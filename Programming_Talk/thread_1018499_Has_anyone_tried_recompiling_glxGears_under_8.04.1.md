---
title: "Has anyone tried recompiling glxGears under 8.04.1?"
date: 2008-12-22
forum: Programming Talk
---

### Post by Greenjacket on 2008-12-22
I've been configuring my Ubuntu 8.04.1 on an Acer Aspire One for OpenGL / freeglut development; I've been through the forums to ensure I've installed all the appropriate libraries etc.

I've noticed some problems when running some OpenGL applications I've found from various books; some of these applications are X-based and some others based on glut. 

The good news is that I am successfully able to render into the OpenGL window, and see what I expect, at the framerates I would expect of hardware acceleration (which I have checked is activated on my Acer).

The bad news is that the application's frame, title bar, menu and the close etc. buttons are all invisible - most of the time. Sometimes the rendering area that is reserved for the frame and title bar appears transparent blue/grey. If I hover the mouse over the expected positions of the menu and title bar buttons, the hints apear, and I can right click to pull down the menu. Otherwise they are generally invisible. I am also seeing that screen refreshing of the desktop is poor after resizing of the OpenGL application - basically it is not happening. I have to manually drag other applications around the desktop to clean up after the graphics application.

I have tried running the default installed glxGears binary, and in this case the OpenGL rendering is again fine, but the frame, title bar and menu etc. are all visible - resizing and desktop refresh etc. are still an issue, and the title bar does go blue/grey sometimes, so it is better, but not perfect.

So I have tried recompiling the original glxGears sourcecode, from the Mesa demo source - and I'm back to my original problem of invisible frame, menu and title bar.

So if two different compilations of the same source code produce quite different rendering results on the same desktop, what has gone wrong?

Many thanks in advance.

---

