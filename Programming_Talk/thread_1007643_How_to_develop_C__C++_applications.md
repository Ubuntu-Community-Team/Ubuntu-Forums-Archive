---
title: "How to develop C / C++ applications"
date: 2008-12-10
forum: Programming Talk
---

### Post by ScEngMan on 2008-12-10
Hello,

Absolute begginer here :)

I've been searching around about what's the best way to develop c or c++ applications using Ubuntu. I'm a c++ developer and I use Visual Studio 2005 in Win. I was wondering what kind of tools can I use in Ubuntu do compile and debug my code.

A more specific question:

I'm trying to understand how blend modes work in GIMP (the math). I already compiled GIMP and it runs ok, but I don't know how to debug it. How can I place a break point inside GIMP to see the value of the variables.

How can I build GIMP when only one source file has changed. Now I'm using 
./configure && make && make install
but I think it's rebuilding the whole project, and the executables are sent to the final destination.

So my real question would be... What tools do the GIMP developers use to compile, link, debug and test their code?

Thank you!
Diego
[SceneEngine]("http://www.sceneengine.org")
Open Source 3D Production Solution

---

### Post by KIAaze on 2008-12-10
Ask the gimp developers! :)
[http://www.gimp.org/mail_lists.html](http://www.gimp.org/mail_lists.html)

You don't have to run ./configure && make && make install every time.
Just run make.
[LIST]
[*]./configure: makes sure necessary stuff is ready + creates the Makefile (using special options when given)
[*]make: compiles the program
[*]make install: installs it (unecessary if you want to work on the source code, meant to install for normal use)
[/LIST]

Debugging tools:
[LIST]
[*]GNU debugger: gdb (integrated in most IDEs)
[*]valgrind (integrated in KDevelop and maybe others)
[/LIST]

Lists:

[List of Free Software and Freeware IDEs]("http://www.linuxquestions.org/questions/programming-9/list-of-free-software-and-freeware-ides-469623/")

[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662")

Top IDEs as far as I know (unsorted): Anjuta, Geany, KDevelop, Eclipse
Most GNU/Linux text editors are very advanced and can be enhanced by plugins. So they can be useful too.

Please refer to the programming section of the forum too. ;)
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

---

### Post by Muffinabus on 2008-12-10
I've been using Netbeans, seems to be a pretty good IDE.

---

### Post by ScEngMan on 2008-12-12
Thanks guys,
I installed netbeans and it looks very cool, although I couldn't find a GIMP project for it, so I guess I'll have to ask the gimp developers...
Thank you
Diego

---

### Post by snova on 2008-12-12
Ah, you won't find one.

The './configure && make && make install' sequence is used to, respectively: Prepare for building, build it, and install it. Most of the time you only need to do this once, but if you change the source code, only the last two are necessary to rebuild it.

---

### Post by ScEngMan on 2008-12-12
I installed KDevelop and imported GIMP as an automake project and it works. I can compile and build GIMP from within KDevelp, errors are highlighted and if I double click on them KDev sends me to the offending line... That's a huge advance for me now.

My next milestone is to be able to debug stepping into the code with breakpoints. That didn't work, but I haven't tried to debug even a tiny project, so I guess I'll have to learn how to in KDev.

Thank you,
Diego

---

### Post by slavik on 2008-12-12
why do you need to compile GIMP? you just need to read the source code to see the formulas, or am I missing something?

---

### Post by KIAaze on 2008-12-13
It's easier to understand code if you tinker with it I guess. :)

---

### Post by ScEngMan on 2008-12-16
> **slavik said:**
> why do you need to compile GIMP? you just need to read the source code to see the formulas, or am I missing something?

I'm developing an open source 3D Painting application = **[CrackArt]("http://www.sceneengine.org/crackart.php")** = and I need to understand how some paiting tools work, starting with Blending Modes (Multiply, Subtract, etc.)

Getting dirty with the source code is the fastest and easiest (and coolest) way to learn how things work.

Cheers
Diego
[SceneEngine]("http://www.sceneengine.org")

---

