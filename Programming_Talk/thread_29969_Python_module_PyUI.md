---
title: "Python module PyUI"
date: 2005-04-26
forum: Programming Talk
---

### Post by Icarus315 on 2005-04-26
Does anyone know where I can get the PyUI package that is built on top of pygame?  In addition to the base repository, I have the universe and multiverse repositories activated and it is not in either.  I have tried to install it from the source package from [http://pyui.sourceforge.net/](http://pyui.sourceforge.net/) but it will not install properly.  I have pygame installed for both python2.3 and python2.4.

---

### Post by DJ_Max on 2005-04-26
PyUI hasn't been updated in two years, wouldn't even bother installing it. If you wanna make games in Python, use PyGame. Else use PyGTK.

---

### Post by Quest-Master on 2005-04-26
DJ_Max is right. Use those or wxPython for cross-platform and short development time goodness. :)

---

### Post by Icarus315 on 2005-04-27
[QUOTE=DJ_Max]PyUI hasn't been updated in two years, wouldn't even bother installing it. If you wanna make games in Python, use PyGame. Else use PyGTK.[/QUOTE]

The thing is, I just bought a book called Game Programming with Python ( [http://www.amazon.ca/exec/obidos/ISBN%3D1584502584/702-0378297-9756035](http://www.amazon.ca/exec/obidos/ISBN%3D1584502584/702-0378297-9756035) ) and it uses pyUI pretty well throughout the book.  I don't need pyUI as it's only covered in detail in a chapter or two but it would be nice to get it installed so I can run all the example code that came with the book on a cd.

Thems the breaks I guess.  Thank you for your help.

---

### Post by kudu on 2005-10-23
[QUOTE=Icarus315]The thing is, I just bought a book called Game Programming with Python ( [http://www.amazon.ca/exec/obidos/ISBN%3D1584502584/702-0378297-9756035](http://www.amazon.ca/exec/obidos/ISBN%3D1584502584/702-0378297-9756035) ) and it uses pyUI pretty well throughout the book.  I don't need pyUI as it's only covered in detail in a chapter or two but it would be nice to get it installed so I can run all the example code that came with the book on a cd.

Thems the breaks I guess.  Thank you for your help.[/QUOTE]

Same here. Pain in the butt. I found PyUI095 and installed it but I get the following errors when I try to run the example code from the book:

>>> Running '/home/kudu/python/gpwp/chapter4/main.py' ...
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/_spe/sm/scriptutils.py", line 49, in run
    exec codeObject in mainDict
  File "<source>", line 49, in ?
  File "<source>", line 43, in run
  File "/usr/lib/python2.4/site-packages/pyui/core.py", line 65, in init
    from renderers.openglPygame import OpenGLPygame
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglPygame.py", line 25, in ?
    from pyui.renderers import openglBase
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglBase.py", line 49, in ?
    from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC
  File "/usr/lib/python2.4/site-packages/OpenGL/WGL/__init__.py", line 2, in ?
    from WGL__init__ import *
ImportError: No module named WGL__init__
Exception raised while running script  <source>
>>> 

Really pissing me off! Can't figure out a cure.

kudu

---

### Post by kudu on 2005-10-24
[QUOTE=Icarus315]Does anyone know where I can get the PyUI package that is built on top of pygame?  In addition to the base repository, I have the universe and multiverse repositories activated and it is not in either.  I have tried to install it from the source package from [http://pyui.sourceforge.net/](http://pyui.sourceforge.net/) but it will not install properly.  I have pygame installed for both python2.3 and python2.4.[/QUOTE]


I got pyUI running. You need to install it per the Python 2.4 devHelp documentation regarding modules. Then hash out this line thusly:

#from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC

from the openglBase.py file located in the /usr/lib/python2.4/site-packages/pyui/renderers folder.

Next extract the hoops folder from the book CD and put a copy in the /python2.4/site-packages folder. That should get the example code operational. Hope this helps!

Regards,
kudu

---

