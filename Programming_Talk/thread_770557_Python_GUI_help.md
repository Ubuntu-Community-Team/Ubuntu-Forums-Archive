---
title: "Python GUI help"
date: 2008-04-27
forum: Programming Talk
---

### Post by Tux.Ice on 2008-04-27
need some programming help,

i writ a few bash scripts, and am looking to do two things.

1. run the bash scripts from python

2. create a graphical environment for the python program.

---

### Post by pofigster on 2008-04-27
Not positive but you could try
```
echo 'deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse'  |  sudo tee -a /etc/apt/sources.list
```
where you just remove any of the options at the end (main, universe, restricted, multiverse) so that it only adds the ones you want.  Then you would need to make sure that you update apt before trying to install anything.

---

### Post by Tux.Ice on 2008-04-27
ok just figured out there is no gksudo -i, anyone know how to do this-

---

### Post by Tux.Ice on 2008-04-27
/bump

---

### Post by pmasiar on 2008-04-27
There are many GUIs for Python, wxPython, GTK bindings, etc. EasyGUI is the simplest.

Not sure why you want to call bash from Python, IMHO more natural (to me) would be do it all in Python, but it is possible, read os.system and friends.

---

### Post by Lau_of_DK on 2008-04-27
> **Tux.Ice said:**
> need some programming help,

i writ a few bash scripts, and am looking to do two things.

1. run the bash scripts from python

2. create a graphical environment for the python program.

TrollTech have done an amazing job with Qt. Its not the simplest place to start, but with a few hours of reading and experimenting, you should be all set.

```

apt-cache search qt | grep python
python-qt-dev - Qt bindings for Python - Development files
python-qt4 - Python bindings for Qt4
python-qt4-dbg - Python bindings for Qt4 (debug extensions)
python-qt4-dbus - DBus Support for PyQt4
python-qt4-dbus-dbg - DBus Support for PyQt4 (debug extensions)
python-qt4-dev - Development files for PyQt4
python-qt4-doc - Documentation and examples for PyQt4
python-qt4-sql - Python bindings for Qt4's SQL module
python-qt4-sql-dbg - Python bindings for Qt4's SQL module (debug extension)
python-qtext - Qt extensions for PyQt
qt4-designer - Qt 4 Designer

```

Install these and youre all set to follow this simple tutorial:

[Your first PyQt GUI]("http://www.cs.usfca.edu/~afedosov/qttut/")


/Lau

---

### Post by LaRoza on 2008-04-27
> **Lau_of_DK said:**
> TrollTech have done an amazing job with Qt. Its not the simplest place to start, but with a few hours of reading and experimenting, you should be all set.


That is overkill.

It seems that zenity is the best bet here. If not zenity, then EasyGUI. 

See my wiki (zenity is under Operating Specific Programming)

---

### Post by Glaxed on 2008-04-27
Yup, get easygui for a Tk looking ui, then
```

import os
from easygui import *

continue = ynbox("Continue?")
# whatever you need

os.system("sh /home/$USER/Desktop/script.sh")

```

---

### Post by Tux.Ice on 2008-04-28
Thanks For all your help guys. :popcorn:

---

