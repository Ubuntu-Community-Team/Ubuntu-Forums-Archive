---
title: "c++ SDL_PollEvent() help"
date: 2009-04-26
forum: Programming Talk
---

### Post by Xender1 on 2009-04-26
Right now I am following the tutorial on this site: [http://www.spikedsoftware.co.uk/blog/index.php/2009/01/06/creating-the-sdl-window/](http://www.spikedsoftware.co.uk/blog/index.php/2009/01/06/creating-the-sdl-window/)

for creating an SDL window with C++. I am coding this in netbeans.

The line that I keep getting a error on is
```

while (SDL_PollEvent(&amp;theEvent)) 

```

I have never seen the &amp before, and when i take it out i get a whole set of other errors.

Am i missing some libraries or something?

---

### Post by Namtabmai on 2009-04-26
[QUOTE=Xender1;7155859]
```

while (SDL_PollEvent(&amp;theEvent)) 

```

Sorry is that a forum misprint?  It should be

```

while (SDL_PollEvent(&theEvent)) 

```

Ah it's a problem with the original tutorial you linked. The web site is showing &amp; where it should be just &

---

### Post by Xender1 on 2009-04-26
yea i changed it because ```
while (SDL_PollEvent(&theEvent))
``` is what the correct parameter is.. yet if i do that i get loads of errors.....im gonna keep doing some research and see whats up, any tips will be greatly appreciated

---

### Post by Namtabmai on 2009-04-26
Post the errors and we'll help you through them. :)

---

### Post by Xender1 on 2009-04-26
this is what i get for errors, and its making me think i am missing an SDL library or something since when even copying the code for that section i get these errors as well.
```

build/Debug/GNU-Linux-x86/main.o  
build/Debug/GNU-Linux-x86/pong.o: In function `Pong::Uninitialise()':
/NetBeansProjects/Pong/pong.cpp:103: undefined reference to `SDL_FreeSurface'
/NetBeansProjects/Pong/pong.cpp:105: undefined reference to `SDL_Quit'
build/Debug/GNU-Linux-x86/pong.o: In function `Pong::Run()':
/NetBeansProjects/Pong/pong.cpp:83: undefined reference to `SDL_PollEvent'
/NetBeansProjects/Pong/pong.cpp:95: undefined reference to `glClear'
/NetBeansProjects/Pong/pong.cpp:97: undefined reference to `SDL_GL_SwapBuffers'
build/Debug/GNU-Linux-x86/pong.o: In function `Pong::InitialiseGraphics()':
/NetBeansProjects/Pong/pong.cpp:32: undefined reference to `SDL_Init'
/NetBeansProjects/Pong/pong.cpp:36: undefined reference to `SDL_GL_SetAttribute'
/NetBeansProjects/Pong/pong.cpp:39: undefined reference to `SDL_SetVideoMode'
/NetBeansProjects/Pong/pong.cpp:43: undefined reference to `glEnable'
/NetBeansProjects/Pong/pong.cpp:46: undefined reference to `glViewport'
/NetBeansProjects/Pong/pong.cpp:49: undefined reference to `glClear'
/NetBeansProjects/Pong/pong.cpp:52: undefined reference to `glMatrixMode'
/NetBeansProjects/Pong/pong.cpp:55: undefined reference to `glLoadIdentity'
/NetBeansProjects/Pong/pong.cpp:58: undefined reference to `glOrtho'
/NetBeansProjects/Pong/pong.cpp:61: undefined reference to `glMatrixMode'
/NetBeansProjects/Pong/pong.cpp:64: undefined reference to `glLoadIdentity'
/NetBeansProjects/Pong/pong.cpp:66: undefined reference to `glClearColor'

```

edit:ohhh dont i have to add the SDL / OpenGL to the project properties?

---

### Post by Namtabmai on 2009-04-26
No you didn't, but the fact you realised that is great.
I'm afraid I don't know netbeans, but in gcc terms you need to add the SDL libraries to the linking flags, something like

```
-lSDL -lGL
```

should cover it.

---

### Post by Xender1 on 2009-04-26
word. it compiles perfectly fine from when in the directory i type in the terminal: 
```

g++ -Wall main.cpp Pong.cpp -lSDL -lGL -lSDL_ttf -o word

```
i guess i just need to fix the netbeans compiler now
Anyone know where the directory location is (from a default install) of the lSDL/lGL/lSDL_ttf libraries? (for include directories)
Thanks for the help Namtabmai!

---

### Post by TheBuzzSaw on 2009-04-26
You just have to change the linker properties. I code SDL projects in Netbeans all the time.

---

### Post by Xender1 on 2009-04-26
where are the SDL libraries located? When I installed them I dont remember specifying a location
edit: found out where they are located just having a hard time setting up the linker.... when i change the linker properties do i just add the -lSDL etc tag?

---

### Post by Xender1 on 2009-04-27
->solved
Project Properties -> Linker -> Libraries
then i chose add option and put in all the options i needed there (the -lSDL and two other times for -lGL and -lSDL_ttf).
Now it compiles under netbeans!! thanks everyone!

---

