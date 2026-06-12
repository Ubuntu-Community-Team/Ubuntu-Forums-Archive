---
title: "Python 3.2 &amp; Tkinter Problems"
date: 2013-03-30
forum: Programming Talk
---

### Post by Sky001 on 2013-03-30
Hello everyone, 
About two seeks ago, I tried posting this thread in the Absolute Beginer section, I recieved no response so I'm trying here, hoping this is it's correct home. I've recently bumped into a problem when istalling the Tkinter  package for Python3. I'm using a personal computer and these are the  steps i went through to install Python3 and Tkinter. 

```
sudo apt-get install python3
sudo apt-get install python3-tk
```

Synaptic shows that python3-tk is indeed installed, yet when using **python3 -m Tkinter** i get **/usr/local/bin/python3: No module named Tkinter**. I'm pretty sure i'm doing something wrong. I just don't know what it is.

Typing **whereis python3** in terminal gives:

python3: /usr/bin/python3.2 /usr/bin/python3 /usr/bin/python3.2mu  /etc/python3.2 /etc/python3 /usr/lib/python3.2 /usr/lib/python3  /usr/bin/X11/python3.2 /usr/bin/X11/python3 /usr/bin/X11/python3.2mu  /usr/local/bin/python3.2 /usr/local/bin/python3  /usr/local/bin/python3.2-config /usr/local/bin/python3.2m-config  /usr/local/bin/python3.2m /usr/local/lib/python3.2  /usr/include/python3.2mu /usr/share/python3  /usr/share/man/man1/python3.1.gz

A little while back, I had the same problem with my default Python installation. I did some research and found this solution: 
```

sudo apt-get install-python-support
sudo update-python-modules -a
```

I have no idea what I did with the above code, but it worked. And so i tried modifying it to what is below:

```
sudo apt-get install python3-support
sudo update-python3-modules -a
```

Needless to say, it didn't work. Does anyone know how i can go about solving this issue? I imagine its probably something simple. I just don't know how to go about it!

---

### Post by xb12x on 2013-03-31
Try the command using a small t on tkinter instead of the capital T:

python3 -m tkinter

From
[http://docs.python.org/2/library/tkinter.html](http://docs.python.org/2/library/tkinter.html)

"Note:[ Tkinter]("http://docs.python.org/2/library/tkinter.html#module-Tkinter") has been renamed to tkinter in Python 3.  The [*2to3*]("http://docs.python.org/2/glossary.html#term-to3") tool will automatically adapt imports when converting your sources to Python 3."




And also make sure to do a general update ...   

sudo apt-get update

---

### Post by schragge on 2013-03-31
Try
```

python3 -c 'import sys;print sys.path'|grep lib-dynload

``` If you have got *lib-dynload* on sys.path, Tkinter shall work out of the box. BTW, the interface module is named *_tkinter*, but you should never call it directly: it is a shared library that doesn't have a corresponding .py file, so cannot be called with -m option.

---

