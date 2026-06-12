---
title: "[SOLVED] Example of game programming?"
date: 2008-06-27
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-27
I have been working towards making a game for a while now... little surprise being that this is my first attempt at such a thing that I am making mistakes and doing some things too short sighted, which causes me to have to go back and redo them. Does anyone know if any of the Open Source games have source code which is a really good example of how to program a game? I'm using C++, and SDL, so it would probably be best to point me at a game programmed in those. It may also be beneficial to know that my game is (will be) a 2D game, and real time (though its not a stratagy game so do not be confused).

---

### Post by pmasiar on 2008-06-27
game in C++ is hard to make. Try GamaMaker (for windows), or Python/pygame. Both have plenty of tutorials and examples. If you feel like beta-software adventure, try GameBaker (see my sig) and become part of the history :-)

---

### Post by Zeotronic on 2008-06-27
Believe it or not, I have to admit that I am all too familure with Game Maker... and let me be the first to tell you that it is quite simply not possible to make a serious game with it. (besides the fact that it is limited to Windows, and, last I knew, Intel processors... what a joke!) I'd rather stick with C++, as I don't know any python (and judging from the python programs I have seen, don't want to learn it). I will re-iterate, does anyone know any good C++ examples of game programming? I suppose I am open to the idea of using C instead, but that is all the farther I will budge.

---

### Post by myrtle1908 on 2008-06-27
Perhaps this [http://allegator.sourceforge.net/](http://allegator.sourceforge.net/) it is C not C++.

---

### Post by slavik on 2008-06-28
I had a little something in which I am sure I could rip myself a new one for doing dumb things, and find places where I made good decisions.

I called AI Escape: you can get it here: [http://bcacm.org/~slavik/AI-Escape.tar.bz2](http://bcacm.org/~slavik/AI-Escape.tar.bz2)

I have not tested it on amd64 (it did build and work fine on an ATI card with the fglrx driver). You will need the OpenGL and SDL development libraries for g++ to build the game. There is a makefile and a configure script and everything.

---

### Post by tornado89 on 2008-06-28
My Advice Would Be To Use OpenGL with C++
I'm Using It For 5 Years Now..
And It's Awesome... 
If You Plan To Do Any Kind of Games ( 2D or 3D )...
The OpenGL Is Supported On Large Variety of OS/s Unlike
Direct3D...

Most of Computer Intensive Games Are Done Using C++...
So Go For It..

A Great Site To Learn OpenGL From Ground Up Using C++

[http://nehe.gamedev.net](http://nehe.gamedev.net)

It Explains Everything Starting From How To Setup An OpenGL Window On Any OS ......

---

### Post by Diabolis on 2008-06-28
My first program was a C++ game, a simple snake game, maybe the source code would be of help. It is attached to this post.

As I said this was my first program and it is probably the worst code you'll ever see, but maybe tinkering with it will help you.

I wrote it with borland or turbo c libraries (not sure). So you'll need them in order to compile the code, if you don't have them already.

Feel free to contact me if you decide to give a look to the code.

I also attached the .exe, of course it will only run in windows.

---

### Post by Zeotronic on 2008-06-28
> My Advice Would Be To Use OpenGL with C++
I'm Using It For 5 Years Now..
And It's Awesome...
If You Plan To Do Any Kind of Games ( 2D or 3D )...
The OpenGL Is Supported On Large Variety of OS/s Unlike
Direct3D...
When I started learning programming about two years ago I used OpenGL along with C++ (I was taking a video game programming course at my high school... before I graduated). I stopped using it in order to to learn SDL's rendering system, because (and I think this is pretty wild) I wanted to design for a platform which does not have OpenGL acceleration... but instead has SDL acceleration. Now this is a moot point, because this platform is in all likely-hood about to be taken out by an arising competitor (which does have OpenGL acceleration), but I have every intent to support SDL and OpenGL rendering. As for Direct3D, and Direct X in general, being a Linux user I would never even consider using them... would any of us? (though as I understand it using SDL I am inadvertantly using it under Windows)
> Most of Computer Intensive Games Are Done Using C++...
So Go For It..
As I grew up I came to suspect, if not know, that most games used C++, which is why I made it a point to learn it... though as I have stated, according to what I know, I am not in rejection of C, probably due to the 'holy wars'.
> A Great Site To Learn OpenGL From Ground Up Using C++

[http://nehe.gamedev.net](http://nehe.gamedev.net)
I am familure with NeHe... I guess I will have to consider studying it.

As for Diabolis' code... I don't think it will be useful... but I might be able to learn something from myrtle1908's code... I haven't taken a look at slavik's code yet.

---

