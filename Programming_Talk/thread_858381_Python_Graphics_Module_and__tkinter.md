---
title: "Python Graphics Module and _tkinter"
date: 2008-07-13
forum: Programming Talk
---

### Post by bcerge on 2008-07-13
Hello everyone, Im a somewhat experienced python programmer, and this is the first time I've used python in another OS than Linux, so I just have a question about a little problem I am having, I wrote a small 2D arcade game for a homework assignment in on of my programming classes, and I wanted to check it out using Ubuntu, so I imported the graphics.py module and that works fine, whenever I try to run the program (running it through the terminal) I am getting this:

 File "Avalanche.py", line 3, in <module>
    from graphics import *
  File "/usr/lib/python2.5/site-packages/graphics.py", line 93, in <module>
    import Tkinter
  File "/usr/lib/python2.5/lib-tk/Tkinter.py", line 41, in <module>
    raise ImportError, str(msg) + ', please install the python-tk package'
ImportError: No module named _tkinter, please install the python-tk package

so I wrote this in the terminal:

sudo apt-get install python-tk

and this is what I am getting:

Building dependency tree       
Reading state information... Done
Package python-tk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.5
E: Package python-tk has no installation candidate

Anyone run into this problem or know a quick fix for it? Thnx in advance.
   
  -bc

---

