---
title: "IOQuake3 Mod Programming"
date: 2006-12-10
forum: Programming Talk
---

### Post by RiggenBlaque on 2006-12-10
I have what i hope will be an easy question from an absolute beginner in game programming.

I'm attempting to create a simple quake3 mod by editing the files of IOQuake3.  No matter what file i change, however, the change will not appear in game.  

The code i'm currently implementing is a simple command line operation to turn on homing missiles.  I know the code is correct, so thats not a problem.

My two main suspicions are that i'm either 1) compiling and running the game completely wrong (edit files -> sudo make -> ./ioquake3.i386) 2) or i'm completely off track here and have no idea what i'm doing.

Any suggestions on what exactly to do would be greatly appreciated, as documentation on how to edit quake3 source on linux is really lacking.

---

### Post by RiggenBlaque on 2006-12-10
bump

---

### Post by shining on 2006-12-10
I don't think this is a correct place for asking questions specific to a project. :)
Better see with ioq3 people. Start with their site:
[http://ioquake3.org/?page=home](http://ioquake3.org/?page=home)
There is a discuss page for different kinds of contact (mailing list, irc, forums), and a help page.

If you are not editing the game engine itself, but only the game logic, that's possible since the game is released. The whole source code isn't needed, only the sdk. And there are probably a lot of informations on the web about how creating q3 mods.

In the meantime, maybe this would do it for a quick try:

> 
Using shared libraries instead of QVMs

To force Q3 to use shared libraries instead of
QVMs run it with the following parameters:

+set sv_pure 0 +set vm_cgame 0 +set vm_game 0 +set vm_ui 0


---

### Post by c-ron on 2009-01-24
> Using shared libraries instead of QVMs

To force Q3 to use shared libraries instead of
QVMs run it with the following parameters:

+set sv_pure 0 +set vm_cgame 0 +set vm_game 0 +set vm_ui 0 


This works. I used it to load a modded qagamex86.dll for Win32 ioquake3. Thanks!

---

