---
title: "Is Qt the best toolkit to use for KDE apps?"
date: 2009-05-02
forum: Programming Talk
---

### Post by dodle on 2009-05-02
I want to build some apps that integrate well with Kde, and from what I understand most apps in Kde are built with qt.  Is this the toolkit I should use?

---

### Post by OutOfReach on 2009-05-02
You don't have to use it, you can use GTK, but yes Qt looks the best in KDE...since KDE is made of Qt

---

### Post by dodle on 2009-05-03
Thank you.  

Also, I am using Python to write my apps.  To import Qt I have been doing the following:
[php]from PyQt4 import QtGui, QtCore[/php]

I get a little tired of typing out "QtGui" before everything.  I've seen a  [tutorial here]("http://vizzzion.org/?id=pyqt") that uses:
[php]import qt[/php]
or:
[php]from qt import *[/php]

But when I try these I get:> ImportError: No module named qt
Am I doing something wrong?

---

### Post by dodle on 2009-05-04
Figured it out:
[php]#! /usr/bin/env python

import sys
from PyQt4 import Qt


class MainWindow(Qt.QWidget):
    def __init__(self):
        Qt.QWidget.__init__(self)

        self.setWindowTitle('Window')

        self.resize(300, 150)

app = Qt.QApplication(sys.argv)
frame = MainWindow()
frame.show()
sys.exit(app.exec_())
[/php]

---

