---
title: "Can anyone suggest a good python IDE which can handle both the GUI and Code?"
date: 2014-04-21
forum: Programming Talk
---

### Post by wannabelinuxgeek on 2014-04-21
[COLOR=#000000][FONT=Arial]I want to develop a desktop application in Python which can send data to the web. The web application will be a django application. But I am not able to find a good IDE for GUI development. I need something like Qt Creator which can handle GUI and code both.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can anyone suggest me something ? An algorithmic guide for this project of mine will be helpfull will be helpful as I am new to python. I have creator some working application in C++ using Qt. I want something same with python.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks in Advance.[/FONT][/COLOR]

---

### Post by llanitedave on 2014-04-21
I don't know why you'd need a special IDE for GUI.  In PyQT, for example, you build the GUI using Python classes and functions just as you would any other part of an application.  That said, one IDE that uses QT itself and has support for QT forms, etc. is **Eric**:  [http://eric-ide.python-projects.org/](http://eric-ide.python-projects.org/)

I haven't tried it in a few years, back in the day it was a bit buggy, but there was a lot I liked about it.  It looks like its pretty actively maintained, so any faults I could mention have probably been fixed by now.

---

### Post by nidzo732 on 2014-04-21
You can use QtCreator (or Qt Designer) to draw the GUI, and then you can load that GUI in python with PyQt.
For the code, I recommend PyCharm IDE.
Have a look at the PyQt documentation and look for the Pyuic tool. It is used to convert guis writen in qtcreator into python modules.

---

