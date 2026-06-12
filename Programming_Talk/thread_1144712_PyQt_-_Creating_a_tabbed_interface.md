---
title: "PyQt - Creating a tabbed interface?"
date: 2009-05-01
forum: Programming Talk
---

### Post by dodle on 2009-05-01
I have become familiar with wxPython and created an application with it.  I would now like to create a version using Qt so that it integrates well with KDE, but I'm having trouble getting started.  Creating the tabbed interface has got me stuck.  How do I add widgets to a tab?

Here is the code I have so far:
[php]import os, sys
from PyQt4 import QtGui, QtCore

class MainWindow(QtGui.QWidget):
    def __init__(self):
        QtGui.QWidget.__init__(self)
        
        self.setGeometry(0,0, 500,650)
        self.setWindowTitle("Debreate")
        self.setWindowIcon(QtGui.QIcon("icon.png"))
        self.resize(500,650)
        self.setMinimumSize(500,650)
        self.center()
        
        # --- Menu --- #
        open = QtGui.QAction("Exit", self)
        save = QtGui.QAction("Save", self)
        build = QtGui.QAction("Build", self)
        exit = QtGui.QAction("Quit", self)
        
        menu_bar = QtGui.QMenuBar()
        file = menu_bar.addMenu("&File")
        help = menu_bar.addMenu("&Help")
        
        file.addAction(open)
        file.addAction(save)
        file.addAction(build)
        file.addAction(exit)
        
        tabs = QtGui.QTabWidget(self)
        tab_bar = QtGui.QTabBar(tabs)
        
        tab_1 = tab_bar.addTab("Main")
        tab_2 = tab_bar.addTab("Description")
        
        vbox = QtGui.QVBoxLayout()
        vbox.addWidget(menu_bar)
        vbox.addWidget(tabs)
        
        self.setLayout(vbox)
    
    
    def center(self):
        screen = QtGui.QDesktopWidget().screenGeometry()
        size = self.geometry()
        self.move((screen.width()-size.width())/2, (screen.height()-size.height())/2)


app = QtGui.QApplication(sys.argv)
frame = MainWindow()
frame.show()
sys.exit(app.exec_())[/php]

I've been going over Qt's references but I'm having trouble.  There are a few tutorials at [http://zetcode.com/tutorials/pyqt4/]("http://zetcode.com/tutorials/pyqt4/"), but they are somewhat limited.  Does anyone know of any other good tutorials or references?

---

### Post by OutOfReach on 2009-05-01
Well the way I do it is like this.
First I define my tab widget:
```

tab_widget = QTabWidget()

```
Then I define a tab...
```

tab1 = QWidget()

```
It may seem weird but you'll understand why I am doing this.
Now I will create my layout...
```

layout = QVBoxLayout(tab1)

```
and I add widgets to that layout as usual...Now when I want to add the tab into the tab widget I just:
```

tab_widget.addTab(tab1, "Test Tab")

```
Now keep doing this until you have all the tabs you want, now we set the dialog (or main window's) main layout:
```

mainLayout = QVBoxLayout()
mainLayout.addWidget(tab_widget)

```
and then set this as the main layout....
```

thisForm.setLayout(mainLayout)

```

Hope this helped a little

---

### Post by dodle on 2009-05-01
Thank you.  That helps me out a lot!

[php]import os, sys
from PyQt4 import QtGui, QtCore

class MainWindow(QtGui.QWidget):
    def __init__(self):
        QtGui.QWidget.__init__(self)
        
        self.setGeometry(0,0, 500,650)
        self.setWindowTitle("Debreate")
        self.setWindowIcon(QtGui.QIcon("icon.png"))
        self.resize(500,650)
        self.setMinimumSize(500,650)
        self.center()
        
        # --- Menu --- #
        open = QtGui.QAction("Exit", self)
        save = QtGui.QAction("Save", self)
        build = QtGui.QAction("Build", self)
        exit = QtGui.QAction("Quit", self)
        
        menu_bar = QtGui.QMenuBar()
        file = menu_bar.addMenu("&File")
        help = menu_bar.addMenu("&Help")
        
        file.addAction(open)
        file.addAction(save)
        file.addAction(build)
        file.addAction(exit)
        
        tab_widget = QtGui.QTabWidget()
        tab1 = QtGui.QWidget()
        tab2 = QtGui.QWidget()
        
        p1_vertical = QtGui.QVBoxLayout(tab1)
        p2_vertical = QtGui.QVBoxLayout(tab2)
        
        tab_widget.addTab(tab1, "Main")
        tab_widget.addTab(tab2, "Description")
        
        button1 = QtGui.QPushButton("button1")
        p1_vertical.addWidget(button1)
        
        vbox = QtGui.QVBoxLayout()
        vbox.addWidget(menu_bar)
        vbox.addWidget(tab_widget)
        
        self.setLayout(vbox)
    
    
    def center(self):
        screen = QtGui.QDesktopWidget().screenGeometry()
        size = self.geometry()
        self.move((screen.width()-size.width())/2, (screen.height()-size.height())/2)


app = QtGui.QApplication(sys.argv)
frame = MainWindow()
frame.show()
sys.exit(app.exec_())[/php]

---

### Post by Zancarius on 2009-06-26
I hate to bump this (relatively) old post over something petty, but you might also want to try:

```
size = self.frameSize()
```

Instead of

```
size = self.geometry()
```

as the former will take into account the full window with (frame borders and all) rather than the internal geometry.

It's only a handful of pixels, but if you're looking at doing a "CenterOnScreen()" wxPython work-alike, that's another way to do it. I'm sure there's others.

---

