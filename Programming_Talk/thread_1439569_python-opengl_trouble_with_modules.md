---
title: "python-opengl: trouble with modules"
date: 2010-03-26
forum: Programming Talk
---

### Post by akudewan on 2010-03-26
Hi,

I'm making a simple project (for learning) in python-opengl and wxPython.

When I execute my program, I get this error message:
```

INFO:OpenGL.acceleratesupport:No OpenGL_accelerate module loaded: No module named OpenGL_accelerate
INFO:OpenGL.formathandler:Unable to load registered array format handler numpy:
Traceback (most recent call last):
  File "/usr/lib/python2.6/site-packages/OpenGL/arrays/formathandler.py", line 44, in loadPlugin
    plugin_class = entrypoint.load()
  File "/usr/lib/python2.6/site-packages/OpenGL/plugins.py", line 14, in load
    return importByName( self.import_path )
  File "/usr/lib/python2.6/site-packages/OpenGL/plugins.py", line 28, in importByName
    module = __import__( ".".join(moduleName), {}, {}, moduleName)
  File "/usr/lib/python2.6/site-packages/OpenGL/arrays/numpymodule.py", line 11, in <module>
    raise ImportError( """No numpy module present: %s"""%(err))
ImportError: No numpy module present: No module named numpy

INFO:OpenGL.formathandler:Unable to load registered array format handler numeric:
Traceback (most recent call last):
  File "/usr/lib/python2.6/site-packages/OpenGL/arrays/formathandler.py", line 44, in loadPlugin
    plugin_class = entrypoint.load()
  File "/usr/lib/python2.6/site-packages/OpenGL/plugins.py", line 14, in load
    return importByName( self.import_path )
  File "/usr/lib/python2.6/site-packages/OpenGL/plugins.py", line 28, in importByName
    module = __import__( ".".join(moduleName), {}, {}, moduleName)
  File "/usr/lib/python2.6/site-packages/OpenGL/arrays/numeric.py", line 15, in <module>
    raise ImportError( """No Numeric module present: %s"""%(err))
ImportError: No Numeric module present: No module named Numeric

```

However, when I look into my site-packages, I see those modules present there:
```

[akshay@kobol OpenGL]$ pwd
/usr/lib/python2.6/site-packages/OpenGL

[akshay@kobol OpenGL]$ ls -1 acceleratesupport.py arrays/
acceleratesupport.py

arrays/:
formathandler.py
formathandler.pyc
numbers.py
numbers.pyc
numericnames.py
numericnames.pyc
_numeric.py
numeric.py
_numeric.pyc
numeric.pyc
numpymodule.py
numpymodule.pyc
#and many more...

```

These are the import statements from my program:
```

import wx
import sys
import solcube #this is my own
import logging
from time import time, sleep
try:
    from wx import glcanvas
    haveGLCanvas = True
except ImportError:
    haveGLCanvas = False

try:
    # The Python OpenGL package can be found at
    # http://PyOpenGL.sourceforge.net/
    from OpenGL.GL import *
    from OpenGL.GLU import *
    from OpenGL.GLUT import *
    haveOpenGL = True
except ImportError:
    haveOpenGL = False

```

I downloaded the wxpython demos, which has a similar program using GLCanvas and it works fine. What am I doing wrong here?

Edit: My program does run, but it looks ugly. (no anti-aliasing)

---

### Post by akudewan on 2010-03-27
I have managed to reduce the error message down to just one:

```

INFO:OpenGL.acceleratesupport:No OpenGL_accelerate module loaded: No module named OpenGL_accelerate

```

I installed the python-numpy and python-numeric packages provided by my distro to solve the earlier problems. The demo GLCanvas program seemed to be working fine even without these packages, which is quite strange...

What do I do about this acceleratesupport problem? (The program works fine when I'm using only GLUT and no wxPython)

---

