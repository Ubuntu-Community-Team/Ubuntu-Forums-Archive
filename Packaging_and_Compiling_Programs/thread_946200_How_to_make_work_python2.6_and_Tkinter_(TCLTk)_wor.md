---
title: "How to make work python2.6 and Tkinter (TCL/Tk) work ?"
date: 2008-10-13
forum: Packaging and Compiling Programs
---

### Post by HorstJENS on 2008-10-13
Hi, i compiled the new python2.6 on my ubuntu8.04 and also compiled pygame1.8.1.

The new python sit now in /usr/local/lib/python2.6 and work good so far. 
However, i did not managed to make Tkinter run. 

i get this error message:

```
>>> import Tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python2.6/lib-tk/Tkinter.py", line 39, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named _tkinter

```

can anyone say me what to do ?

---

### Post by HorstJENS on 2008-10-14
solved, i missed some TK*dev packages before compiling python2.6

---

### Post by go_beep_yourself on 2008-11-22
Are there not any 2.6 deb packages for Ubuntu? Just wondering because that's the version my book is teaching me.

---

### Post by jabapyth on 2009-01-20
I haven't found any official packages of python 2.6, but you can check [my blog]("http://jaredforsyth.com") for instructions on how to install it from launchpad.
[http://jaredforsyth.com/content/install-python-26-ubuntu](http://jaredforsyth.com/content/install-python-26-ubuntu)

---

