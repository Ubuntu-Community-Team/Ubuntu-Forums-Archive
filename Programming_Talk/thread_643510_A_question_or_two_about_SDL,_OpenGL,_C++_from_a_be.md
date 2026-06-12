---
title: "A question or two about SDL, OpenGL, C++ from a beginner"
date: 2007-12-17
forum: Programming Talk
---

### Post by tabithaboof on 2007-12-17
I have been doing a bit of research on programing from a making games point of view and have a couple of questions, please be aware I havent dont any programming other than a little HTML since BASIC on the spectrum. I am not thinking of making anything more complex than Frozen Bubble or Geometry Wars and am only thinking about 2D games at the moment. I am fairly confident I can make sprites using Inkscape or the GIMP and I can do sound effects in .ogg or .mp3 format or whatever I am looking for a way to put my sounds and images together to make a game.

I have read that C++ is a good place to start but a lot of tutorials I have seen also talk about OpenGL and SDL, are these alternatives to C++ or something that you use in conjunction with it?

Most of the tutorials talk about these different languages as discrete entities but I havent found one yet that explains how or if they link together.

Secondly I am very enthusiastic about making my game(s) as friendly to the open source community as possible. would C++, OpenGL and SDL (assuming I can get my head around them) be good for that?

Thanks very much!

---

### Post by LaRoza on 2007-12-17
Those languages are better suited for more complex games.

With your experience, and goals, try Python and PyGame, see my wiki for more on each.

Learn Python first with command line programs, then move on.

(Python is used in many games, including Oblivion)

---

### Post by Wybiral on 2007-12-18
I definitely suggest PyGame as well. It's a wrapper to SDL and can be used with PyOpenGL for 3d games. For 2d, you probably wont need OpenGL unless you plan on really jazzy effects, SDL/PyGame will do.

Most importantly, I would suggest learning to actually program before tackling a serious game project. Start with simple tasks and challenges before diving into a game.

---

### Post by AZzKikR on 2007-12-18
> **tabithaboof said:**
> I have read that C++ is a good place to start but a lot of tutorials I have seen also talk about OpenGL and SDL, are these alternatives to C++ or something that you use in conjunction with it?

C++ is a programming language frequently used for games because of its performance, I guess. 

SDL is the Simple Directmedia Layer, which is an API written in the C language. This is a cross-platform API, which handles displaying a screen, drawing on it (displaying images and such), handling sound (music, sound clips and effects), input methods (joystick, keyboard, and mouse events). 

OpenGL is a very popular API for making 3D games. Making 2D games with it is also possible, except you don't use the z axis.

> 
Secondly I am very enthusiastic about making my game(s) as friendly to the open source community as possible. would C++, OpenGL and SDL (assuming I can get my head around them) be good for that? 

Yes, it will be very good for games, but I advise you to learn an object oriented programming language first, such as Python. C++ can be very difficult for a starting programmer.

I've been programming for more than 10 years now (last 5 in Java) and I just started learning C++. Even I had some trouble with it, and I can imagine the 'trouble' you can get when you are starting to learn it :)

It's funny that you mentioned C++/SDL/OpenGL in one post though, since I am involved in a project team which is developing an open source game called iteam (take a look at [http://www.iteamgame.org](http://www.iteamgame.org) and [http://www.iteamgame.org/wiki](http://www.iteamgame.org/wiki)), using those very same technologies :D

---

### Post by slavik on 2007-12-18
> **Wybiral said:**
> I definitely suggest PyGame as well. It's a wrapper to SDL and can be used with PyOpenGL for 3d games. For 2d, you probably wont need OpenGL unless you plan on really jazzy effects, SDL/PyGame will do.

Most importantly, I would suggest learning to actually program before tackling a serious game project. Start with simple tasks and challenges before diving into a game.

World of Warcraft uses Lua, maybe OP should learn that?

@OP:

C++ is a programming language.
OpenGL is a graphics library.
SDL is a library that has similar use as DirectX (but no high end graphic routines like OpenGL). It is used for sound, input and in conjunction with OpenGL for graphics.

If you want the shortest path possible towards making games with high end tools, then that is the combination for you.

---

### Post by tabithaboof on 2007-12-19
Thanks very much everyone!

I think that I am going to give C++ a try, I found a reasonably cheap book on the language and an article at Gamedev.com recmoended it as a starting point. I can always 

> **AZzKikR said:**
> 
It's funny that you mentioned C++/SDL/OpenGL in one post though, since I am involved in a project team which is developing an open source game called iteam (take a look at [http://www.iteamgame.org](http://www.iteamgame.org) and [http://www.iteamgame.org/wiki](http://www.iteamgame.org/wiki)), using those very same technologies :D

Even wierder coincidence, I was looking at just that page while thinking about game design! Just out of curiosity what are SDL, C++ and OpenGL doing in your game?

---

### Post by Wybiral on 2007-12-19
> ... since I am involved in a project team which is developing an open source game called iteam ...
Oh yeah, how's that project going? Did you guys ever get the animations working? I have some revisions I've been planning to pass on to DARKGuy for the GP2D library (if you guys are still using that).

---

### Post by tyoc on 2007-12-19
to the original poster, you can link and use C things from C++ almost the same way (thought the internally have something like exter C {} for clarify that it is a C thingy)

I will suguest [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) it is for C, havent tested it myself on C++, but try to compile it with the C++ compiler instead of C, and I think you will not have troubles (even the same sample code will run if compiled with C++ I think).

glfw isnt as massive as SDL (It is more simple and compact), is more like GLUT, but it will help you in get into OpenGL from C/++. Also there is a C++ implementation of GLUT but right now I dont remember the name. 

After that, if you can, look at ogre3d, for get some perpective from the point of biew of a graphic engine (it is in C++, and is far more advanced and is prewrited, you dont need to code that part).

---

### Post by AZzKikR on 2007-12-19
> Even wierder coincidence, I was looking at just that page while thinking about game design! Just out of curiosity what are SDL, C++ and OpenGL doing in your game?

:D

We use OpenGL for the jazzy effects, and SDL is mainly used for sound, music and input handling. And well, we use C++ to code the engine (GamePower2D) and the game itself in! :)

---

