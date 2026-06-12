---
title: "Python"
date: 2014-10-13
forum: Programming Talk
---

### Post by jgsamuel on 2014-10-13
I'm a beginner wherein programming is involved. My primary question is why the Python version that comes with Ubuntu is so outdated and if it will affect my learning.

---

### Post by TheFu on 2014-10-13
There is a difference between what an OS needs from python and what a software developer needs from python.
The OS needs stability. No change. The version used needs to have been tested, well understood and 200 other python applications included in the distro need to work with it.

A software developer needs a specific version of python so that libraries work with it.  It is a best practice for the dynamic language developer (perl, ruby, python) to completely control the scripting language, libraries, tools used for each of their programs.  Perl has perlbrew. Ruby has RbEnv and RVM. I think python has something similar (not a python programmer here).

So .... the first thing you need is to setup the python version manager, install the version of python you need (newer is NOT better), get the libraries you need for the stuff you are doing, and find a mentor.  

Any good python book or teacher should explain this stuff.

Oh ... and if you are targeting your programs for a specific version of any OS, it is best to use the exact same version of python that distro already includes.

Programs are seldom forward compatible, but languages tend to be backwards compatible. Clients would rather be on an older version than be force to upgrade an entire OS just for 1 stupid program.

I hope all this makes sense.

---

### Post by tdawgf on 2014-10-13
Since the poster above answered the question of why Ubuntu is not running the latest version of Python, I will tackle the second part. There are some differences between the two, and those differences will lead to slightly different code. My suggestion is, since you are beginning Python, is to download the latest version (or anything 3+) and start. However, if you don't want to do this, at one point there were far more libraries and references for python 2 than 3 (although this might not be the case anymore). This means that either way you will learn, and you should be able to learn well. Professionally I come from a .NET background, but in my spare time I am using Python to create a game, and I must say you are picking a fantastic language. I would love to be able to use it more at work.

---

### Post by oldfred on 2014-10-13
With 14.04 two versions of python are installed:

fred@trusy-ar:~$ python --version
Python 2.7.6
fred@trusy-ar:~$ python3 --version
Python 3.4.0

---

### Post by ofnuts on 2014-10-13
AFAIK you have both versions (2.7 and 3+) of Python in all Ubuntu releases.  IIRC that was already the case in my Ubuntu Lucid (2010...)

---

### Post by llanitedave on 2014-10-15
But the default still seems to be Python 2.7.  If I download some Python application or library from the software center, even one that is supposedly compatible with Python 3, for example PyQt4, it automatically gets installed in Python 2.7.  I'm not sure how to change that.

---

### Post by TheFu on 2014-10-15
> **llanitedave said:**
> But the default still seems to be Python 2.7.  If I download some Python application or library from the software center, even one that is supposedly compatible with Python 3, for example PyQt4, it automatically gets installed in Python 2.7.  I'm not sure how to change that.

#!/usr/bin/env python3

Doesn't that work?

Or just look at ** ls -al /usr/bin/python***

---

### Post by oldfred on 2014-10-15
Whatever you do, do not change default as that will break entire system.

You should be able to run python2 or python3 to get version you want. 
Default currently is set to python2, but future versions may change to python3 as default or the version you get if just running python.

---

