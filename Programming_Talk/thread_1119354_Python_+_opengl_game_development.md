---
title: "Python + opengl game development?"
date: 2009-04-07
forum: Programming Talk
---

### Post by Jeremy Jackins on 2009-04-07
Hi, as a fun project I want to try to develop a (very) simple 3D game using python and opengl. I installed pyOpenGL, and I've been looking around for some reading/tutorials to get me started, but I'm finding myself overwhelmed by the sheer amount of words that begin with GL: glut, glu, glx, glsl, gle etc. I've noticed something called 'pygame' that might be appropriate for what I'm trying to do, but I thought I'd ask if anyone on here has experience on the subject and could give me some advice or point me towards some relevant tools or reading. Thanks!

---

### Post by soltanis on 2009-04-07
Python has SDL bindings, right? If so, I suggest you use those, since SDL does a lot of the work that OpenGL doesn't directly do for you.

GLut is mostly useless (I think that it has a memory leak or something, or its unmaintained now, or something or another, not suitable for game development), although I guess it might have a few things to help you.

Really, OpenGL is all you need. Maybe GLSL too, and SDL for 2D rendering (inevitable), input, sound, networking, etc.

---

### Post by red_team316 on 2009-04-07
I would definitely look into pygame. It is the python version of SDL. SDL can handle setting up OpenGL windows and meshes really well together. For an OpenGL/SDL game/app you typically would use OpenGL calls for the drawing and only use SDL for keyboard/audio/joystick/etc. 

I've never actually had the need to use pygame(I use C/C++ when using SDL) although have looked at the pygame site a time or two and there is plenty of stuff there to learn from.

---

### Post by Jeremy Jackins on 2009-04-07
thanks! working through a pygame tutorial now.

---

### Post by slavik on 2009-04-08
> **red_team316 said:**
> I would definitely look into pygame. It is the python version of SDL. SDL can handle setting up OpenGL windows and meshes really well together. For an OpenGL/SDL game/app you typically would use OpenGL calls for the drawing and only use SDL for keyboard/audio/joystick/etc. 

I've never actually had the need to use pygame(I use C/C++ when using SDL) although have looked at the pygame site a time or two and there is plenty of stuff there to learn from.
glut was designed to be "get a window on the screen as fast as you can and add some basic keyboard controls." glut was designed with OpenGL demos in mind.

---

### Post by Jiraiya_sama on 2009-04-08
> **soltanis said:**
> 
GLut is mostly useless (I think that it has a memory leak or something, or its unmaintained now, or something or another, not suitable for game development), although I guess it might have a few things to help you.


It does in fact have memory leaks.

---

