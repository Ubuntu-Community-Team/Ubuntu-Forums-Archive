---
title: "how to compile multiple .py into 1 .exe for windows users."
date: 2011-03-29
forum: Programming Talk
---

### Post by pivotraze on 2011-03-29
Hi there everyone,

I'm a relatively new programmer on linux, and a lot of my friends have stayed on Windows.

I'm developing an application that is very heavily on their interest, and they would like to see it's various stages as it gets brought up.

Here's the problem: They don't have python. I dont feel the need for them to have it, and want them to use a pre-provided .exe (not that I could convince them to install a python at all for them to run it).

Yes, the source code can be downloaded by them, and they know that, but they still want .exe :\

Now, how do I do this?

I downloaded pyinstaller and tried doing that, but it didn't compile into .exe, only an executable file for Linux

I need help here. 
My .py files:
aboutDialog.py
loadsave.py
menu.py
prefDlg.py
RunMe.py (or main.py)
stkCreator.py
updateDlg.py

All of these must compile into one file that ends in .exe and is actually runnable on Windows (XP and up only)

Thanks for the help.

BTW, I downloaded the Command Line Version of py2exe but idk how to use it for a wxpython application. :\

---

### Post by Some Penguin on 2011-03-29
[http://wiki.wxpython.org/index.cgi/DistributingYourApplication]("http://wiki.wxpython.org/index.cgi/DistributingYourApplication")

---

### Post by pivotraze on 2011-03-29
That's how to do it on Windows... I am using Ubuntu right now.. and I need to compile it to .exe

I can't really use py2exe (in my knowledge) because it's a windows program :p

---

### Post by Dark_Stang on 2011-03-29
> **pivotraze said:**
> That's how to do it on Windows... I am using Ubuntu right now.. and I need to compile it to .exe

I can't really use py2exe (in my knowledge) because it's a windows program :p

You'll need to compile it on windows.

---

### Post by pivotraze on 2011-03-29
Grr. :\ What if I don't have access to a windows computer?

---

### Post by Dark_Stang on 2011-03-29
> **pivotraze said:**
> Grr. :\ What if I don't have access to a windows computer?

Then tell your friends to man up and download python. They seem to be the problem anyway.

---

### Post by deathadder on 2011-03-30
Either install Windows into VirtualBox to do the compilation, or make them install python... :)

---

### Post by 102jon on 2011-03-30
I'm sure there are hacked versions of windows you could get for free (similar to the Hackintosh) and put it on a virtual machine.

---

