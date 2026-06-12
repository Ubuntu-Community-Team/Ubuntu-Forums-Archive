---
title: "How to install Tkinter into Python 3 in Xubuntu?"
date: 2014-12-08
forum: Programming Talk
---

### Post by flaymond on 2014-12-08
Hello guys, I'm having a problem with Python 3 these days. I'm a newbie in Python and using Python 3 to learn now. I'm using thinkpython book as my learning source. It was a good book, but I got a problem to import Tkinter into Python 3. I'm using Tkinter to use TurtleWorld program from swampy modules. But, I cannot using it in Python 3. It keep saying that " No module named Tkinter". But, it not happened in python 2 intepreter.....It seem that just not working in Python 3. I tried change the case of the 'Tkinter' to 'tkinter' and somehow worked...but when I try to import the turtle module, it keep saying 'No module named Tkinter'. Here is the code I tried.

Python 3 - Trying to import Tkinter 

```
>>> import **T**kinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'Tkinter'

 
```

Python 3 - Trying to import **t**kinter

```
>>> import tkinter
>>> 


```

Worked! But, when I tried to import the TurtleWorld module, it keep saying the error.

Python 3 - Trying to import TurtleWorld module 

```
>>> from TurtleWorld import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/home/alex/Documents/swampy-2.1.7/build/lib.linux-i686-2.7/swampy/TurtleWorld.py", line 8, in <module>
    from Tkinter import TOP, BOTTOM, LEFT, RIGHT, END, LAST, NONE, SUNKEN
ImportError: No module named 'Tkinter'


```

See?

I tried to import all of these modules in Python 2, and all worked! That mean I'm not in wrong directory. 


How can I install Tkinter in Python 3? I really met a frustation :(

EDIT : That was my bad! I was using TurtleWorld of Python 2! That's why it not working! Sorry!

---

