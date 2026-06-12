---
title: "Python  directory"
date: 2009-04-15
forum: Programming Talk
---

### Post by tdawg on 2009-04-15
Ight so Im still completely new to ubuntu and Python, and I was learning from windows but am trying seriously to use ubuntu, therefore i need to know python in ubuntu. I already have it installed and am using IDLE. What I need to know is, where do I save my .py files? I cannot locate the python directory at all.

---

### Post by sekinto on 2009-04-15
You save them anywhere. Paths should only matter within your project.

---

### Post by Can+~ on 2009-04-15
> **tdawg said:**
> where do I save my .py files? I cannot locate the python directory at all.

Python scripts are just like any regular file, why would you need to store them in a special place? You can place them wherever you want.

And you're not forced to use IDLE to program in python, you can create a .py in any editor, gedit for example (don't underestimate gedit, check the options) and run them with python myscript.py

For example, the first thing I made when installing ubuntu, was a folder named "Programming" in my home folder, and have everything organized per language.

---

### Post by tdawg on 2009-04-16
> **Can+~ said:**
> Python scripts are just like any regular file, why would you need to store them in a special place? You can place them wherever you want.

And you're not forced to use IDLE to program in python, you can create a .py in any editor, gedit for example (don't underestimate gedit, check the options) and run them with python myscript.py

For example, the first thing I made when installing ubuntu, was a folder named "Programming" in my home folder, and have everything organized per language.

See, I'm under the impression that that #! /usr/bin/python/ thing is a specific place where you need to keep your .py files. Or if it is, then I would need to change that to wherever I place my .pys ?

---

### Post by slavik on 2009-04-16
no, there is no special place to place anything (except for places when some program looks for it)

Can, I do the same, except my dir is named "code" :)

---

### Post by Can+~ on 2009-04-16
> **tdawg said:**
> See, I'm under the impression that that #! /usr/bin/python/ thing is a specific place where you need to keep your .py files. Or if it is, then I would need to change that to wherever I place my .pys ?

The **#!/usr/bin/env python** is called the "[shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")". It's a common bash *nix convention that allows code to be passed to it's interpreter just by executing it.

You should learn that python interpreter reads a file (.py) and creates executable code from it, that's why you can run your scripts with "python filename.py" (or executing it with the proper shebang). The shebang just points to the location of the interpreter and calls it with the name of the script.

So, in short terms (if the file is executable and has a shebang):
./pyscript.py <=> python pyscript.py

---

### Post by M4rotku on 2009-04-16
+1 for the programming folder sorted by languages

---

### Post by tdawg on 2009-04-16
Thanks guys
:guitar:

---

### Post by Anthon on 2009-04-16
As an extension to earlier answers including '#/usr/bin/env python' in your script.
If you do that, you don't need the .py extension at all.

If you want to keep Python things together and don't want to use the shebang header line you can also put your .py files in pythons site-packages directory (/usr/lib/python2.5/site-packages for python version 2.5,). Doing so allows you to start a script abc.py using:
  python -m abc
from any location.
If you don't want to write your stuff directory in the .../site-packages directory
make a subdirectory under site-packages called e.g 'tdawg' and a empty file in tdawg with name '__init__.py' and a file under site-packages called anthon.pth with one line of content (the name of the directory):
  tdawg
This combination of things (the .pth file and the __init__.py file) will make sure the tdawg subdir is searched as well if you do 'python -m abc'

---

### Post by Wybiral on 2009-04-16
> **Anthon said:**
> ... you can also put your .py files in pythons site-packages directory (/usr/lib/python2.5/site-packages for python version 2.5,). Doing so allows you to start a script abc.py using:
  python -m abc
from any location.

I wouldn't recommend doing that though, as it will make your script a module for that Python install (so if the name collides with any other common modules, you'll have problems).

---

### Post by Arndt on 2009-04-16
> **Anthon said:**
> As an extension to earlier answers including '#/usr/bin/env python' in your script.
If you do that, you don't need the .py extension at all.



This is true, but one good reason for keeping the .py extension is to make editors automatically detect that it's Python code, and do the right thing. On the other hand, some editors can interpret comments in a particular format to indicate the language used, so you have a choice.

Yet another way to keep the .py extension from confusing or irritating a user is to create a symbolic link prog -> prog.py.

Then there are the byte-compiled Python files, with extension .pyc. It seems (I just tried it) that if you set the execution bit on such a file, it behaves as a runnable program.

---

