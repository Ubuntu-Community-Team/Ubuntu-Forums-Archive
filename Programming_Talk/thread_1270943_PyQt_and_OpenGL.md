---
title: "PyQt and OpenGL"
date: 2009-09-20
forum: Programming Talk
---

### Post by glaze on 2009-09-20
I'm trying to make a 3D editor using PyQt and OpenGL, but I can't create the OpenGL widget. I'm trying to use QGLWidget, but python cannot find QtOpenGL. I'm using Kubuntu 9.04 and have installed various packages related to Python, Qt and OpenGL.

```

import sys
from PyQt4 import QtCore, QtGui, QtOpenGL

class MyGLWidget(QtOpenGL.QGLWidget):

    def __init__(self, parent = None):
        QtOpenGL.QGLWidget.__init__(self, parent)
        self.xsize = 512
        self.ysize = 512

    def initializeGL():
        glClearColor(0.0, 0.0, 0.0, 0.0);

    def paintGL():
        glClearColor(0.0, 0.0, 0.0, 0.0);

    def resizeGL():
        glClearColor(0.0, 0.0, 0.0, 0.0);

```

edit: solved! I didn't have package "python-qt4-gl" installed.

---

