---
title: "Starting to program; a few questions"
date: 2007-08-21
forum: Programming Talk
---

### Post by DeathOnJuice on 2007-08-21
I just started programming a few days ago in Python (my first program can be seen here: [http://python-forum.org/py/viewtopic.php?p=21392](http://python-forum.org/py/viewtopic.php?p=21392)), and I liked the language. I know a lot about computers in general and some about programming concepts, so I can jump into language (except, maybe, assembly :) ). However, before I throw all my effort into one language, I have a few questions to ask.

1. For game development (both 2D and 3D), or just working with 3D graphics, which language would you suggest? I'm guessing C++ works for both or Python for 2D, but I'm not quite sure.

2. For a general-purpose language (file parsing, GUIs, basic networking stuff, etc.), what would you suggest? Again, I'm guessing Python (probably) or C++.

3. I know that the -dev packages (i.e. freeglut3-dev) are used for creating programs. However, I thought that dynamically linked libraries (I may be way off on this) were only used when the program was run. So, what's the use of the non-dev packages?

4. Could someone give a brief explanation of OpenGL, SDL, and what languages they can be used with? I'm especially confused about SDL.

5. Finally, could I get a couple book or tutorial suggestions for the languages you recommend (as in one for C++ Games, one for Python general purpose, etc.)? I know there are many in the sticky, but I was hoping to narrow down the choices a bit.

Thanks for reading all that. If some of the questions are unanswerable (I tried to be specific), could you give some pros and cons? In case it matters much, I'm doing everything in Ubuntu.

---

### Post by Mirrorball on 2007-08-22
> **DeathOnJuice said:**
> so I can jump into language (except, maybe, assembly :) ).
n00b :)

> **DeathOnJuice said:**
> 1. For game development (both 2D and 3D), or just working with 3D graphics, which language would you suggest? I'm guessing C++ works for both or Python for 2D, but I'm not quite sure.
Both will do 2D and 3D graphics, but if you write your game in Python and performance isn't good, you will have to translate all or part of it to C or C++. It depends on how complicated the game is.

> **DeathOnJuice said:**
> 2. For a general-purpose language (file parsing, GUIs, basic networking stuff, etc.), what would you suggest? Again, I'm guessing Python (probably) or C++.
Python would be way easier than C++ for these simple programs.

> **DeathOnJuice said:**
> 3. I know that the -dev packages (i.e. freeglut3-dev) are used for creating programs. However, I thought that dynamically linked libraries (I may be way off on this) were only used when the program was run. So, what's the use of the non-dev packages?
The dev packages contain mostly *headers* for C and C++; we need them to compile programs written in those languages. The dynamic libraries are in the non-dev packages.

> **DeathOnJuice said:**
> 4. Could someone give a brief explanation of OpenGL, SDL, and what languages they can be used with? I'm especially confused about SDL.
OpenGL is a graphics library useful for creating accelerated 3D graphics, as in games. SDL is a library for graphics, sound, and other stuff you would need to create a game. It's not just for graphics. And you can call OpenGL functions from SDL for fast 3D graphics. OpenGL and SDL can be used with a lot of programming languages, including C, C++, and Python.

> **DeathOnJuice said:**
> 5. Finally, could I get a couple book or tutorial suggestions for the languages you recommend (as in one for C++ Games, one for Python general purpose, etc.)? I know there are many in the sticky, but I was hoping to narrow down the choices a bit.
I don't know what to suggest, sorry. :(

---

### Post by DeathOnJuice on 2007-08-22
Could you point me to a simple example of SDL and OpenGL being used together? I don't really understand why you would call OpenGL graphics functions with SDL, as opposed to the normal way. They're both cross-platform.

---

### Post by scooper on 2007-08-22
There are a couple of free Python books and tutorials online.  Check out [http://www.python.org](http://www.python.org) for links.  For books you can start by looking at [http://diveintopython.org/](http://diveintopython.org/) and [http://www.mindview.net/Books/TIPython](http://www.mindview.net/Books/TIPython).  I don't have personal knowledge of how good they are, but they're popular.

I didn't like the Lutz books (Learning Python and ???)  on Python, despite their high recommendations.

---

### Post by pmasiar on 2007-08-22
> **DeathOnJuice said:**
> I can jump into language 

Syntax of a language is the easy part. hard part is the libraries and idioms/pattern (how solve common problems), including debugging.

> 1. For game development (both 2D and 3D), or just working with 3D graphics, 
Python has libraries (written in C) for that. So if you use Python, big part of your code is  C.

2. For a general-purpose language (file parsing, GUIs, basic networking stuff, etc.), what would you suggest? Again, I'm guessing Python (probably) or C++.

Python, with flying colors! It's common myth that Python is slow - in fact, in most cases if fast enough.

> 4. Could someone give a brief explanation of OpenGL, SDL, and what languages they can be used with? I'm especially confused about SDL.

Did you tried wikipedia articles?

> 5. book or tutorial suggestions 

If your claim of being experienced programmer is valid :-) "Dive into Python" is for you. Pythonchallenge is good "obstacle course" to train, or see wiki in my sig.

Don't dive into GUI, learn command-line python first, and learn using shell to test little snippets of code (without writing complicated scaffolding to just try one function call).

For games, look at pygames.

Python has only one con: Anybody can learn it, so you don't have bragging rights :-)

---

### Post by DeathOnJuice on 2007-08-23
Thanks again, everyone. Still, I just need one more thing that I mentioned in an earlier post - an explanation of how you use SDL and OpenGL together, as opposed to only using one or the other.

---

### Post by LaRoza on 2007-08-23
> **DeathOnJuice said:**
> Thanks again, everyone. Still, I just need one more thing that I mentioned in an earlier post - an explanation of how you use SDL and OpenGL together, as opposed to only using one or the other.

[http://www.libsdl.org/opengl/index.php](http://www.libsdl.org/opengl/index.php)

[http://www.linuxdevcenter.com/pub/a/linux/2003/10/23/sdl_anim.html](http://www.linuxdevcenter.com/pub/a/linux/2003/10/23/sdl_anim.html)

If you just started a few days ago, you might want to start with simpler tasks.

(using google (or live), will get you many results, wikipedia also have informative articles and is very useful, as mentioned earlier)

---

### Post by Smygis on 2007-08-23
> **DeathOnJuice said:**
> Thanks again, everyone. Still, I just need one more thing that I mentioned in an earlier post - an explanation of how you use SDL and OpenGL together, as opposed to only using one or the other.

SDL itself only allows for lightwight graphics. But combined with OpenGL you can do advanced 3D games. Using SDL for keyboard, sound and some other important stuff and opengl for graphics.

---

