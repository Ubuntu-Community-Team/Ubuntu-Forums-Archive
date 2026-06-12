---
title: "Ubuntu, OpenCV 2.0 and the new Python API."
date: 2010-04-01
forum: Packaging and Compiling Programs
---

### Post by gijzelaar on 2010-04-01
Karmic doesn't contain OpenCV 2.0. Lucid does contain 2.0, but doesn't contain the new Python API. I've made new OpenCV packages for Ubuntu karmic and Lucid and put them in a PPA.

Read more about it on my blog:
[http://gijs.pythonic.nl/blog/2010/apr/1/ubuntu-opencv-20-and-new-python-api/](http://gijs.pythonic.nl/blog/2010/apr/1/ubuntu-opencv-20-and-new-python-api/)

---

### Post by gijzelaar on 2010-04-07
Opencv 2.1 packages for Ubuntu karmic and Ubuntu Lucid:

[http://gijs.pythonic.nl/blog/2010/apr/7/opencv-21-ubuntu-packages/](http://gijs.pythonic.nl/blog/2010/apr/7/opencv-21-ubuntu-packages/)

---

### Post by richlowe101 on 2010-04-23
Thanks for this, I had problems with compiling from source so this is a massive help. Keep up the good work!

---

### Post by Furious_Angel on 2010-05-08
[COLOR=#000000][FONT=Arial][FONT=Verdana]With your repo there was a problem. The modules are not added for a python.
[/FONT][/FONT][/COLOR]I get an error
```
Traceback (most recent call last):
  File "my.py", line 5, in <module>
    from opencv import cv, highgui, adaptors
  File "/usr/lib/python2.6/dist-packages/opencv/highgui.py", line 25, in <module>
    _highgui = swig_import_helper()
  File "/usr/lib/python2.6/dist-packages/opencv/highgui.py", line 21, in swig_import_helper
    _mod = imp.load_module('_highgui', fp, pathname, description)
ImportError: libavutil.so.49: cannot open shared object file: No such file or directory
```Any ideas?
[COLOR=#000000][FONT=Arial][FONT=Verdana]
[/FONT][/FONT][/COLOR]

---

