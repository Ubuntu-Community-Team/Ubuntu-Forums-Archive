---
title: "Python help need!!"
date: 2005-10-23
forum: Programming Talk
---

### Post by kudu on 2005-10-23
I downloaded a zip copy of PyUI-095 but I don't know where it belongs. Where does it go ? How do I set it up ?

Thanks!
kudu

---

### Post by kudu on 2005-10-23
Got it done! Thanks anyway...

kudu

---

### Post by kudu on 2005-10-23
Now this:

>>> Running '/home/kudu/python/gpwp/chapter4/main.py' ...
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/_spe/sm/scriptutils.py", line 49, in run
    exec codeObject in mainDict
  File "<source>", line 49, in ?
  File "<source>", line 43, in run
  File "/usr/lib/python2.4/site-packages/pyui/core.py", line 65, in init
    from renderers.openglPygame import OpenGLPygame
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglPygame.py", line 25, in ?
    from pyui.renderers import openglBase
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglBase.py", line 49, in ?
    from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC
  File "/usr/lib/python2.4/site-packages/OpenGL/WGL/__init__.py", line 2, in ?
    from WGL__init__ import *
ImportError: No module named WGL__init__
Exception raised while running script  <source>
>>> 

What the heck does all this mean? How do I fix it, please ? What and where is WGL_init ??? I have python2.4-opengl installed. Help appreciated!

kudu

---

### Post by kudu on 2005-10-23
OK...had a look see. The file exists and is where it's supposed to be. Why is it failing ?

Bugging the **** outta me!

HELP - PLEASE!!

---

### Post by atoponce on 2005-10-24
[quote=kudu]OK...had a look see. The file exists and is where it's supposed to be. Why is it failing ?

Bugging the **** outta me!

HELP - PLEASE!![/quote] 
Can you post some code? It is hard to tell what the error is. Also, it looks like to need to install those libraries first as the import statements are failing. I am new to Python myself, and I don't think those libraries are included in the core language.

---

### Post by kudu on 2005-10-24
I got it solved. WGL __init__ is Windows stuff, specifically in this case to do with microsoft fonts. I hashed the offending line out and the code works fine now.

Thanks for responding though, I do appreciate it.

kudu

---

