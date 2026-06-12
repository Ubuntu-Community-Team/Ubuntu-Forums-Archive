---
title: "Establishing OpenGL Programming on my PC"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by lusbyclark on 2013-02-08
Yes, I am a newbie not only to Ubuntu and Linux, but also OpenGL programming and I need some assistance.  There is a lot of confusing, even contradictory advice to be found out on the internet regarding what I must download to my PC so I can engage in OpenGL programming.  I am confused first about just which version of GLX I must download - is it the Mesa version or the Cairo version or perhaps just a plain vanilla version or something else I am unaware of as yet ?  What else must be downloaded with it X11, and/or Xlib or what?   

Beyond these few questions, what files must be called out in the "#include  <file>"?  

It would be really helpful if someone would identify a good beginners' tutorial that explains all of this in detail.  I did look for such a tutorial not only only the internet, but this forum as well, but I came up with confusing, contradictory stuff.   

I must say I fully expect someone will respond saying that their advice is to go to some website that comes up at the top of their Google list and they can't imagine how I managed not to find it for myself.  Well, the answer lies in the fact that I am so ignorant of OpenGL stuff that I hardly know how to ask a real human being an intelligent OpenGL question.  That and the fact that I probably did stumble across the afore mentioned website at some point, but failed to recognize it as a good source of info.

Did I say I am easily frustrated.

---

### Post by Impavidus on 2013-02-08
You can install the packages **freeglut3-dev** or **libglfw-dev**. They will pull in a number of dependencies that will get you started. Freeglut is somewhat easier than glfw, but has less advanced features. Of course you also need a lot of non-GL development packages. The rendering work and handling of video memory is all done by gl, but glut and glfw can help you with convenient wrappers for common operations and with creating and destroying windows and mouse/keyboard interaction.

In your code you can include the headers with **#include <GL/glfw.h>** or **#include <GL/glut.h>** (not sure of the last one, I've no example at hand).

Considering learning OpenGL programming: I started with a full semester course at my university. That me be overkill (although convenient, as it brought me some credits). It may be a good idea to find the red book on openGL programming.

Some links that may be helpful:
[http://www.opengl.org/sdk/](http://www.opengl.org/sdk/)
[http://www.glprogramming.com/red/](http://www.glprogramming.com/red/)
[http://www.opengl.org/resources/libraries/glut/](http://www.opengl.org/resources/libraries/glut/)
[http://www.glfw.org/](http://www.glfw.org/)

---

