---
title: "Beginning Graphics/Game programming"
date: 2007-03-21
forum: Programming Talk
---

### Post by lawentzel on 2007-03-21
I am getting back into programming after a couple decades.  (Yeah I'm oldish).  I want to use what comes with Ubuntu only for the ease sakes.  I have typed in:

```
sudo aptitude install build-essential
```

So, that much is set.  I have installed Anjuta IDE and Glade for interface designs.  What else should I look at?  Any good websites for graphical programming?  I am using Ubuntu (Gnome)

I have found in the past if I set my mind on a goal I want to program, I tend to be more focused.  Mind you my goals aren't always realistic.

I am figuring on using either C or C++.  Both of which I have experience with.  I figure for my first program, I want to create something that will generate fractal landscapes.  From there, I will add features, textures, more functionality and so forth.

Thanks for any help and suggestions in advance.

---

### Post by Wybiral on 2007-03-21
For 3d stuff OpenGL and SDL are almost a must!

I suggest becoming fluent with OpenGL and matrix/vector mathematics.

---

### Post by Poisson_Pilote on 2007-03-21
If you want to generate 3D Landscapes, I suggest OpenGL as well.

---

### Post by lawentzel on 2007-03-21
Does OpenGL come on the system?  Or am I going to need to download something else?  Thanks.

---

### Post by Wybiral on 2007-03-21
The runtime libraries are installed, but not the development files.

Go to synaptic and look for the MesaGL development files.

---

### Post by simplyw00x on 2007-03-21
```
sudo aptitude install mesa-common-dev
```
Should get you part of the way there at least.

[http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+1](http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+1)

is a great tutorial for relative OpenGL newbies (it helped me immeasurably) and also tells you in detail how to set up opengl on ubuntu (here: .[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development))

---

### Post by Wybiral on 2007-03-21
Also, the 9th replay of this thread I put together some links a while back: [http://www.ubuntuforums.org/showthread.php?t=333867](http://www.ubuntuforums.org/showthread.php?t=333867)

NeHe is a particularly great site for OpenGL examples and tutorials.

---

### Post by lawentzel on 2007-03-22
I had actually read the beginning information on programming.  I also searched for various posts on getting started.  The question that usually came up was, what are you going to be programming.  Which is why, I addressed my post as I did.  You are correct Wybiral that there is a lot of helpful information there.  But specifics I have gotten about loading the SDL libraries I don't believe I saw on those various links.  Maybe if I dug around I may have stumbled upon them.  Next time, someone is looking to get started with graphics and game programming, they will find this post, and the various replies and not need to ask the same question.  Regardless, thank you everyone for your help and directions.

Lee

---

### Post by pmasiar on 2007-03-22
You may want to join some game project where they need people with interests like you, creating textures and surfaces etc. And they have sets of libraries selected, and some working code to learn from. Because I assume you are coming to free software communnity to join and help to enhance it?

There is gaming forum where people migh suggest interesting projects looking for developers.

---

### Post by simplyw00x on 2007-03-23
> **lawentzel said:**
> But specifics I have gotten about loading the SDL libraries I don't believe I saw on those various links. 
There are, right here I believe:
[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

---

### Post by maxamillion on 2007-03-23
If you are just wanting to get the hang of things, 2d graphics might be a good place to start and the allegro library is a really nice place to start for such a thing.

---

### Post by Wybiral on 2007-03-23
Another good 2d library is SDL itself.

 Especially when combined with one of it's extensions...

SDL_gfx (handy 2d primitives like lines/ellipses/rectangles)
SDL_ttf (which allows you to use true-type-fonts)
SDL_image (for loading images in a variety formats)

SDL doesn't have to be used with OpenGL if you don't want to use 3d.

---

### Post by Mickeysofine1972 on 2009-06-24
> **simplyw00x said:**
> ```
sudo aptitude install mesa-common-dev
```Should get you part of the way there at least.

[http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+1](http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+1)

is a great tutorial for relative OpenGL newbies (it helped me immeasurably) and also tells you in detail how to set up opengl on ubuntu (here: .[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development))

Glad I can help :D

---

### Post by curvedinfinity on 2009-06-24
Mikey's the best. :)

---

### Post by NielsBhor on 2009-06-24
Try freeglut. I used it. Very simple video tutorial for you if you're interested.

It is using C++. 

Here: [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)

An important part of OpenGL if you have never used it before, you want to know how it render 3D graphics. The various stages such as the frame buffer, texture application, etc...Make sure you know how that goes or else it's a pain to debug.

---

