---
title: "executable python scripts"
date: 2007-11-01
forum: Programming Talk
---

### Post by Mr.popo on 2007-11-01
Ok when i was using windows and programming in c++ i could compile a program and it would be a executable program. Since i have switched to linux i have started to learn to program in python. I likke it but i  dont how you cant make an executable program when i save it has a .py it is just a text file. am i missing something here?

cheers.*

---

### Post by LaRoza on 2007-11-01
Yes, you are missing something.

Python is meant to be an interpreted language, C++ is a compiled language.

[http://laroza.wikidot.com/one](http://laroza.wikidot.com/one)

Read the notes too.

In Ubuntu, you can use C++ also, and you have to compile it. In Windows, you can use Python also. Look in my wiki for the required package. (the one in my sig, not the above wiki)

---

### Post by Bliepo32 on 2007-11-01
[http://ubuntuforums.org/archive/index.php/t-299437.html](http://ubuntuforums.org/archive/index.php/t-299437.html)

---

### Post by Mr.popo on 2007-11-01
But ifyou were to make a gui program how could say send it to someone
wouldnt they have to have python then run the source code

---

### Post by Bliepo32 on 2007-11-01
Please read my link first, because there is a way to compile python (even though it's an interpreted language).

---

### Post by CptPicard on 2007-11-01
Yes, they would. :)

But it's not that much of a problem, Linux typically has all sorts of interpreters available if not by default, at least a few clicks away in an installer... or if you deploy as a package with dependencies set properly, it gets automatically fetched...

Compiling Python to native is not really such a great idea or neccessary in 99% of cases IMO...

---

### Post by LaRoza on 2007-11-01
> **Mr.popo said:**
> But ifyou were to make a gui program how could say send it to someone
wouldnt they have to have python then run the source code

You can use py2exe or Freeze.

Or you can make Python and its required modules be a requirement for the program. Python comes with almost all Linux distros, all Macs (now), and HP and Compaq computers.

For Windows, you can get ActivePython, and wxWidgets, among others, so you can write cross platform apps.

You can also compile Python scripts to byte code, which is faster than a script, but stil requires the interpreter.

---

### Post by Mr.popo on 2007-11-01
ok thanks

---

### Post by Mr.popo on 2007-11-01
Sorry for double post but im still confused.(sorry if im being annoying). IN widnows when a creatd a script and saved it as  a .py i could run it in a console window. In linux when i save as a .py and open it just opens a text file. i want the program to run.

---

### Post by LaRoza on 2007-11-01
Mark it as executable, as the wiki mentioned before stated. That was in my first post, post 2 of this thread.

And run it in the terminal.

---

### Post by Mr.popo on 2007-11-01
> **LaRoza said:**
> Mark it as executable, as the wiki mentioned before stated. That was in my first post, post 2 of this thread.

And run it in the terminal.

ok thanks

---

