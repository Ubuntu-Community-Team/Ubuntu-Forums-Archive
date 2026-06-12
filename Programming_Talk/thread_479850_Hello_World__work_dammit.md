---
title: "Hello World  work dammit"
date: 2007-06-20
forum: Programming Talk
---

### Post by pascalosti on 2007-06-20
Im trying to run a simple "hello world",  Using Anjuta with c++  (im very new to ubuntu)
Error:
No targets specified and no makefile found. Stop.

I already have (solution from google)
libglib2.0-dev package installed


any other packages i should install

edit
I also have "build Essentials" installed and every ligblib2....
Compile with make:  says success, but console window never shows up

Build All:  I get the error message from above

---

### Post by kknd on 2007-06-20
Anjuta needs a lot of developing libraries =S

To compile it, just type g++ source.cpp -o HelloWord

---

### Post by pascalosti on 2007-06-20
Im sorry I havent figured out this whole command concept.

Ill try to explain what my (obviously wrong ) logic im trying to follow.

I take out src folder which contians   main.cc (hello code) and Makefile.am

I place them in my main user folder (not sure where the beginning directory is)

Open terminal
g++ main.cc -o src

error:
No such file or directory

I have this feeling I am way off.  Does Anjuta not create a cpp or an excecutable?

---

### Post by OhioYJ on 2007-06-20
I was in the same boat here recently. I had to use the Auto Generate option in the build menu. Then Compile with Make, then Build. Then the program would execute in the terminal. 

The first time I ran the Auto Generate option I found I didn't have a bunch of libraries installed, so scroll through that list and install anything you are missing. I just use the Synaptic Package manager to install anything I was missing.

---

### Post by xtacocorex on 2007-06-20
This is a classic case where you should read the sticky threads and stay away from IDE's when you are starting off.  Learning the command line compilation is far more important early on than messing with an IDE.

---

### Post by PandaGoat on 2007-06-21
[http://ubuntuforums.org/showthread.php?t=458510]("http://ubuntuforums.org/showthread.php?t=458510")
He had the same problem that I answered in my posts.  Just read them.

---

