---
title: "py2exe problems - won't build"
date: 2009-02-04
forum: Programming Talk
---

### Post by jworr on 2009-02-04
I'm trying to package a python app I wrote under linux for windows.  py2exe seems like the best choice for this but I've encountered a problem that I can't find an answer for.  I've basically followed the py2exe tutorial but here is the error I get when I run python setup.py py2exe:

C:\Python26\lib\site-packages\py2exe\build_exe.py:16: DeprecationWarning: the sets module is deprecated
  import sets
running py2exe
*** searching for required modules ***
error: h: No such file or directory


The version of python I'm running is: 2.6.1
py2exe version: 0.6.9 for python 2.6

I've attached setup.py and hello.py

Right now I'm just trying to get this hello world program to work before I attempt packaging my more complicated one.

---

### Post by rabbitman on 2009-02-04
I'm using Python v2.6.1 & Py2Exe v0.6.9 too, I tested your setup.py & it successfully built the hello.exe after I changed the following line.

From...

```

setup(console='hello.py')

```

To...

```

setup(console=['hello.py'])

```

---

### Post by jworr on 2009-02-04
thanks, that did it.  I feel a little stupid for missing that, though the error message it gave me was useless.

---

### Post by fiddler616 on 2009-02-04
> **jworr said:**
> thanks, that did it.  I feel a little stupid for missing that, though the error message it gave me was useless.
Yeah, all I've ever been able to get out of error messages in Python is a line number, and sometimes not even that.
Java (or is it JCreator) has really nice error messages--"Semicolon expected on line 68", and "userInput may not have been initialized". Python should take notes.

---

