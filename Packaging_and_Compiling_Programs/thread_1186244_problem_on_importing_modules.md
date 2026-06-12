---
title: "problem on importing modules"
date: 2009-06-13
forum: Packaging and Compiling Programs
---

### Post by sundeepA1 on 2009-06-13
[LEFT]**when i started ** [B]compiling  dial_tone.py program in audio(/usr/src/gnuradio-3.1.3/gnuradio-examples/python/audio) folder i get this error message
plzz help to solve my problem
[/B][/LEFT]

 sudo python dial_tone.py
[sudo] password for home: 
Traceback (most recent call last):
  File "dial_tone.py", line 23, in <module>
    from gnuradio import gr
ImportError: No module named gnuradio


how to install these modules and site-packages in gnuradio

---

### Post by sundeepA1 on 2009-06-28
when Iam trying to run/compail my gnu program.I got this ------
--------------------------------------------
Traceback (most recent call last):
  File "gnu_19.py", line 2, in <module>
    from gnuradio import gr
  File "/usr/lib/python2.6/dist-packages/gnuradio/gr/__init__.py", line 43, in <module>
    from gnuradio_swig_python import *
  File "/usr/lib/python2.6/dist-packages/gnuradio/gr/gnuradio_swig_python.py", line 23, in <module>
    from gnuradio_swig_py_runtime import *
  File "/usr/lib/python2.6/dist-packages/gnuradio/gr/gnuradio_swig_py_runtime.py", line 6, in <module>
    import _gnuradio_swig_py_runtime
ImportError: libgromnithread.so.0: cannot open shared object file: No such file or directory

Plzzz help me wat is missing?
How to install??

---

