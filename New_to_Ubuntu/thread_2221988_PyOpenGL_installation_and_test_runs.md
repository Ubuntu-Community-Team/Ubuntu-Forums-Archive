---
title: "PyOpenGL installation and test runs"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by micahpage on 2014-05-04
I am trying to install/run basic OpenGL demo programs in PYthon, but i keep getting errors.

i installed these packages:
[https://pypi.python.org/pypi/PyOpenGL-accelerate/3.1.0b2](https://pypi.python.org/pypi/PyOpenGL-accelerate/3.1.0b2)
[https://pypi.python.org/pypi/PyOpenGL/3.1.0b2](https://pypi.python.org/pypi/PyOpenGL/3.1.0b2)
via 
```
sudo python2 setup.py install
```
```
metulburr@arch ~ $ python2 
Python 2.7.6 (default, Feb 26 2014, 12:07:17) 
[GCC 4.8.2 20140206 (prerelease)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import OpenGL
>>> 

```

Thats all fine and dandy, but i also installed the demos and tried them and come up with these errors:


```
metulburr@arch /usr/lib/python2.7/site-packages/PyOpenGL-Demo/tom $ python2 cone.py
No handlers could be found for logger "OpenGL.Tk"
Traceback (most recent call last):
  File "cone.py", line 15, in <module>
    from OpenGL.Tk import *
  File "/usr/lib/python2.7/site-packages/PyOpenGL-3.1.0b2-py2.7.egg/OpenGL/Tk/__init__.py", line 119, in <module>
    _default_root.tk.call('package', 'require', 'Togl')
_tkinter.TclError: can't find package Togl
metulburr@arch /usr/lib/python2.7/site-packages/PyOpenGL-Demo/tom  $ 

```
```
metulburr@arch /usr/lib/python2.7/site-packages/PyOpenGL-Demo/GLE  $ python2 texas.py
Traceback (most recent call last):
  File "texas.py", line 67, in <module>
    maintest.main(DrawStuff)
  File "/usr/lib/python2.7/site-packages/PyOpenGL-Demo/GLE/maintest.py", line 40, in main
    glutInit(sys.argv)
  File "/usr/lib/python2.7/site-packages/PyOpenGL-3.1.0b2-py2.7.egg/OpenGL/GLUT/special.py", line 326, in glutInit
    _base_glutInit( ctypes.byref(count), holder )
TypeError: 'NoneType' object is not callable
metulburr@arch /usr/lib/python2.7/site-packages/PyOpenGL-Demo/GLE  $ 
```

one of mekires opengl scripts
```
metulburr@arch ~/Downloads/Mekire-gltut-python-pygame-pyopengl-b6eb9a66403e/01_h
ello_triangle  $ python2 01_hello_triangle.py
Traceback (most recent call last):
  File "01_hello_triangle.py", line 84, in <module>
    main()
  File "01_hello_triangle.py", line 72, in main
    MyGL = GLtests()
  File "01_hello_triangle.py", line 35, in __init__
    self.shader = compileProgram(compileShader(VERT,GL.GL_VERTEX_SHADER),
  File "/usr/lib/python2.7/site-packages/PyOpenGL-3.1.0b2-py2.7.egg/OpenGL/GL/shaders.py", line 226, in compileShader
    shaderType,
RuntimeError: ('Shader compile failure (0): 0:2(10): error: GLSL 3.30 is not supported. Supported versions are: 1.10, 1.20, 1.30, and 1.00 ES\n', ['\n       #version 330\n       layout(location = 0) in vec4 position;\n       void main()\n       {\n          gl_Position = position;\n       }'], GL_VERTEX_SHADER)
metulburr@arch ~/Downloads/Mekire-gltut-python-pygame-pyopengl-b6eb9a66403e/01_h
ello_triangle  $ 
```

I am not sure what exactly is wrong. I can assume from the last one that the version might conflict, but the first two shouldn't be, because they are the demos from that version. I am not sure if i am missing another package that may be needed? Or if there is a step to the installation i missed?

---

