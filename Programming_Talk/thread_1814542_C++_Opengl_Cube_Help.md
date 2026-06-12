---
title: "C++ Opengl Cube Help"
date: 2011-07-29
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-07-29
Hi Im new on Videogames Programming, am using C++, Opengl, SDL for the game and im having some troubles with a cube that im trying to rotate...

Here I explain better the problem:

[Linky](http://www.youtube.com/watch?v=7p2m0K05ML0&feature=mh_lolz&list=PLADC954BFAC4E13CF)

I hope somebody help me ):P

---

### Post by PaulM1985 on 2011-07-29
This is a very vague description of the problem.  Have you got any example code which shows this issue?

Paul

---

### Post by ThatCoolGuy220 on 2011-07-29
> **PaulM1985 said:**
> This is a very vague description of the problem.  Have you got any example code which shows this issue?

Paul

Oh silly of me I forgot to include the link, now is included you can check it Is on youtube I explain the problem there.

But basically is that the cube gets de-formed

---

### Post by PaulM1985 on 2011-07-30
Ok.  I am not that great at opengl, but here are a couple of things I expected to see and didn't, so maybe look into these and they might solve your problem:

1.
I expected to see a line something like this:
```

    // Calculate The Aspect Ratio Of The Window

    gluPerspective(45.0f,(GLfloat)width/(GLfloat)height,0.1f,100.0f);

```
It usually lives in your resize function and is related to how things are drawn at depth.  When you applied your rotate functions, everything seemed to be drawn on the same line as though there was no depth.
[http://nehe.gamedev.net/tutorial/creating_an_opengl_window_(win32)/13001/](http://nehe.gamedev.net/tutorial/creating_an_opengl_window_(win32)/13001/)

2.
You might need these function calls in your initialisation code:
```

glClearDepth(1.0f);            // Depth Buffer Setup
glEnable(GL_DEPTH_TEST);       // Enables Depth Testing
glDepthFunc(GL_LEQUAL);        // The Type Of Depth Test To Do 

```

3.
I am not sure what glOrtho is for.  I have never seen it.  Maybe it is unrelated.

Good luck

Paul

---

