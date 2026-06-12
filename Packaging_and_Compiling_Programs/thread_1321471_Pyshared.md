---
title: "Pyshared?"
date: 2009-11-10
forum: Packaging and Compiling Programs
---

### Post by Kazade on 2009-11-10
Hi,

So I've managed to package up some of my Python code into DEB packages which is cool. One problem I'm having though is I want to install some shared Python code. I looked around and found most of the Python modules available system wide appear in /usr/share/pyshared. So I added my own module in there, but Python isn't picking it up do I have to do something else to make Python find my module? Create a symlink somewhere perhaps?

---

### Post by SevenMachines on 2009-11-11
excuse my utter ignorance of python if this is wrong (python is on my ever increasing todo list :) ) but perhaps registering the library using pycentral is the needed step.

---

### Post by SevenMachines on 2009-11-11
if you havent already, i'd have a look at 
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)
i'm guessing theres a call to dh_pycentral you might want to add to your debian/rules

---

### Post by yanaek on 2010-07-13
i have the same problem
i only want to put one file into /usr/share/pyshared/MoinMoin/util directory

but after copying it there, import of that module fails, do i have to 'register' this file somwhere?

before Ubuntu and pyshared, i used it on Debian, inside site-packages dir and it worked fine

---

### Post by dv3500ea on 2011-03-18
I have this problem. According to the [Debian Python Policy]("http://www.debian.org/doc/packaging-manuals/python-policy/ch-python.html#s-paths") we are supposed to put python modules that work across versions in /usr/share/pyshared but python doesn't seem to have this in its default path. 

So I'm just starting my executables with:

```
import sys
sys.path.append('/usr/share/pyshared')
```

---

### Post by MadCow108 on 2011-03-18
python-central and python-support are outdated and getting phased out by debian.
dh_python2 (or 3) is the tool you should use for new stuff:
[http://wiki.debian.org/Python/PyCentral2DhPython2](http://wiki.debian.org/Python/PyCentral2DhPython2)

---

