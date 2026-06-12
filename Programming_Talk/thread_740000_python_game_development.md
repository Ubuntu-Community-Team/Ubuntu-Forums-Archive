---
title: "python game development"
date: 2008-03-30
forum: Programming Talk
---

### Post by A_B on 2008-03-30
Hi,

I already have a basic knowledge op python and I learned some pygame too, but is pygame actually commonly used in linux 2d programs? Is there an other python extension I should take a look at?

Thanks
Alex

---

### Post by finer recliner on 2008-03-30
openGL ;)

---

### Post by days_of_ruin on 2008-03-30
Isn't openGL mainly 3d stuff?If you want to do 2d go ahead and use pygame.

---

### Post by Wybiral on 2008-03-30
PyGame is pretty common. [Galcon]("http://www.imitationpickles.org/galcon/index.html"), for instance, uses PyGame. As far as OpenGL goes, it can be used for 2d games as well as 3d games, but for simple stuff it's usually overkill (especially when you can just use PyGame's functionality instead). But if you need to use OpenGL for some reason, it works very well with PyGame (via PyOpenGL).

---

### Post by Can+~ on 2008-03-30
PyGame is based on SDL

OpenGL also draws in 2d, but finding documentation for python is difficult, instead, you should look at NeHe examples on python (located at the bottom of the page).

[http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02](http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=02)

OpenGL adds the advantage, that if you suddenly want a 3d object in a 2d game, you could do it without troubles.

You should also look for pre-made game engines on opengl, like the one on peach.

---

### Post by Wybiral on 2008-03-30
> **Can+~ said:**
> OpenGL adds the advantage, that if you suddenly want a 3d object in a 2d game, you could do it without troubles.

That's true. It also gives you room for neat effects like blending / matrix transformations / etc. And it's usually faster because it takes advantage of graphics hardware. The main downside is that you're stuck with OpenGL, so you're giving up the freedom to port to systems that either don't have OpenGL or don't have hardware support for it (such as the One Laptop Per Child laptops) where using it is likely to make things much slower (because it has to be software rendered).

---

### Post by A_B on 2008-03-30
Ok, I think i'll stick with pygame then.

If I ever make a decent game (which is not something for next week) is it possible to make my debian package install pygame so my game can run without the user actually having to go to the synaptic package manager to install it?  What if I want to make the same game for Windows / mac?

Thanks
Alex

---

### Post by A_B on 2008-03-30
oh, and why can't pygame do matrix transformations?
Or do you mean that it's more complicated to do with pygame?

---

### Post by days_of_ruin on 2008-03-30
> **A_B said:**
> Ok, I think i'll stick with pygame then.

If I ever make a decent game (which is not something for next week) is it possible to make my debian package install pygame so my game can run without the user actually having to go to the synaptic package manager to install it?  What if I want to make the same game for Windows / mac?

Thanks
Alex

py2exe is for windows.Haven't tried it yet though:P

---

### Post by pmasiar on 2008-03-30
> **A_B said:**
>  is it possible to make my debian package install pygame so my game can run without the user actually having to go to the synaptic package manager to install it?  What if I want to make the same game for Windows / mac?

If you define pygame as dependency, apt will install it if not there. Windows does not have apt (to handle library dependencies), this is exactly the reason why it sucks so badly :-)

---

### Post by A_B on 2008-03-31
After some research I found out pygame seems to be pretty slow at updating the entire screen, which is necessary in most larger game, as it is a large game that I eventually want to work on (an rts with sidescrolling) I decided to star pyopengl.

I tried to find 2d pyopengl tutorials but couldn't find any :(
Does anyone here know of some good tutorials?

Thanks
Alex

---

### Post by Wybiral on 2008-03-31
PyGame is only as slow as you make it. There are all kinds of things you can do to speed it up (caching non-moving sections to their own surface, for instance).

As far as 2d OpenGL, just learn how to render quads with textures. Any OpenGL tutorial will do, just ignore the Z axis :)

---

### Post by A_B on 2008-04-01
so basically you make planes with alpha textures and place them all on the same height, camera in top view? Then is there an easy way to say which plane renders above to other? Does doing it all in a 3d environment affect the speed of the game, the file size?
Can u please give me some examples of 2d games made with pyopengl?

Thanks
Alex

---

### Post by Wybiral on 2008-04-01
> **A_B said:**
> so basically you make planes with alpha textures and place them all on the same height, camera in top view? Then is there an easy way to say which plane renders above to other? Does doing it all in a 3d environment affect the speed of the game, the file size?
Can u please give me some examples of 2d games made with pyopengl?

Thanks
Alex

There's nothing different about PyOpenGL and OpenGL. Any OpenGL tutorial will show you what functions / constant to use, all of the OpenGL functions start with "gl" so it's very easy to tell where the GL code is in any language.

But, like I said, you don't need OpenGL for 2d anyway. PyGame has everything you would need to manage sprites and simple drawing primitives. It even handles collision detection between the sprites.

There is no camera in OpenGL, it's all done with matrix multiplication and for 2d games you turn the depth buffer off, so the only thing that affects the order they appear in is the order you render them in.

As far as speed goes, it depends. There are tricks you can do in OpenGL (like display lists and vertex arrays) that can take advantage of the graphics hardware and speed things up quite a bit. But... Performance for 2d games is rarely an issue these days. If PyGame on it's own is too slow for your needs, there's a good chance you're something wrong.

---

### Post by A_B on 2008-04-01
understood :)
I think I am going to use openGL because by learning it, I also learn how to work with 3D 

oh not completely understood, one final question.
So the openGL command you use in python via pyopengl are actually exactly the same as coding openGL in any other language, therefor python specific openGL tutorials are not necessary?

Thanks
Alex

---

### Post by Wybiral on 2008-04-01
Exactly. This code (to draw a square) is the same in C, C++, Python, and probably a handful of other languages with OpenGL bindings (the only real difference is that Python doesn't end each line in a semicolon :p ):

```

glBegin(GL_QUADS)
glVertex2f(0.0, 0.0)
glVertex2f(1.0, 0.0)
glVertex2f(1.0, 1.0)
glVertex2f(0.0, 1.0)
glEnd()

```

So any tutorial you find, just ignore all of the language-specific stuff (like keyboard input / initializing the screen... You can use PyGame to do all of that for you, then use OpenGL to do all the rendering) and only pay attention to the chunks of code that have "gl" or "GL" in them :)

---

### Post by A_B on 2008-04-01
Ok, I've been looking at the nehe tutorials (with the python translation next to me). Am I correct if I say you need to define a couple of functions (or however you call the, always huge discussions about hat :D) those functions handle the screen, 3d objects, textures, sound, keyinput, mouseinput....  Then et the end of the program these functions are used in a "main function" (def main() : ) and then end with some line I dont understand yet :p

am I right?

A completely other thing... Is it my computer or does the ubuntu forums look weird today?

Thanks
Alex

---

### Post by Wybiral on 2008-04-01
lol, yes the forums look weird today, it's April 1st :) (you can change it back with the option in the bottom right of the screen).

As far as the functions / "main" thing goes... It's a program, just like any other program. Use Python exactly how you normally do, just call the OpenGL function to do the rendering. I would use PyGame to open the window and handle input (mouse / keys / window exit) as well as loading images and fonts, then use OpenGL to do all the rendering.

Ignore the style they use on NeHe, that's just their style. If you don't want a "main" function, don't write one. OpenGL is just a library (thus "Graphics Library"), you can use it however you want, just learn what all the OpenGL functions do and what the constants mean.

---

### Post by pmasiar on 2008-04-01
> **Wybiral said:**
> lol, yes the forums look weird today, it's April 1st :) (you can change it back with the option in the bottom right of the screen).


Thanks man. This joke was funny for first 30 secs, but I am past that.

---

### Post by A_B on 2008-04-01
hmm...  Maybe I should first get more familiar with python then, maybe start to make some program with tinker or something.

I don't think I'm familiar  enough with python to develop my own "opengl style"
Well, I can already start learning the basic opengl functions, if I think a while about how to use them I think I can come up with something.

Thanks for the great and very fast responses, I think I'll be busy now for a while..

Alex

---

### Post by Wybiral on 2008-04-01
Yes, when learning any language you need to learn the language first, not some specific library. Start with text based "terminal" games. Get used to writing functions and using the builtin datatypes. A prerequisite for programming OpenGL in Python is the ability to program Python :) Once you're comfortable with Python, then you can learn OpenGL, but until then it isn't going to make much sense to you.

---

