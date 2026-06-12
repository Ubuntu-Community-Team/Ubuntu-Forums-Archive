---
title: "PyQt Missing Icons"
date: 2008-03-14
forum: Programming Talk
---

### Post by xelapond on 2008-03-14
Hello, 

I have been following the guide [here]("http://zetcode.com/tutorials/pyqt4/menusandtoolbars/") for useing PyQt to write GUI apps in python.  I have been running into several prblems with icons not showing up, but essentially this is what happens.  I am making a toolbar with a quit button, that should have the exit icon.  The icon is not there, but I can still click where is would be.

How can I get my icons back?

[PHP]#!/usr/bin/python

# toolbar.py 

import sys
from PyQt4 import QtGui, QtCore

class MainWindow(QtGui.QMainWindow):
    def __init__(self):
        QtGui.QMainWindow.__init__(self)

        self.resize(250, 150)
        self.setWindowTitle('toolbar')

        self.exit = QtGui.QAction(QtGui.QIcon('exit.png'), 'Exit', self)
        self.exit.setShortcut('Ctrl+Q')
        self.connect(self.exit, QtCore.SIGNAL('triggered()'), QtCore.SLOT('close()'))

        self.toolbar = self.addToolBar('Exit')
        self.toolbar.addAction(self.exit)


app = QtGui.QApplication(sys.argv)
main = MainWindow()
main.show()
sys.exit(app.exec_())[/PHP]



Thanks, 

Alex

---

### Post by joq on 2008-11-22
I am having the very same problem.  I don't see any response to this question.  Is this an Ubuntu Hardy bug or a PyQt4 problem?

All help greatly appreciated.

---

### Post by skullmunky on 2008-11-22
Hi,

Easy solution: look around in /usr/share/pixmaps for an 'exit.png' file, or use whatever else you like.  Copy it into the same directory as your python script.  

In theory it seems like there should be some way that Qt would magically know what theme you're using and where the icons are stored, but it sure don't work for me neither.  

You can also set the resource search paths at the beginning of your code so Qt will know other places to look.

---

### Post by uniomni on 2011-12-08
I am having the exact same problem and couldn't find the icons in /usr/share/pixmaps. I tried with some other png files, but nothing shows up.

It would be nice if the otherwise excellent tutorial pointed to them for completeness. Anyway, I plan to buy the advanced tutorial e-book once completed the basic one.

---

### Post by Bachstelze on 2011-12-08
As scullmunky said, you should have the file in the directory where your script is located.

[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qicon.html#QIcon-4](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qicon.html#QIcon-4)

> If fileName contains a relative path (e.g. the filename only) the relevant file must be found relative to the runtime working directory.

Find an icon you like, and copy it into your script's directory. Alternatively (and probably better), use QIcon.fromTheme to get icons from the Qt theme of the user.

[http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qicon.html#fromTheme](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qicon.html#fromTheme)

---

### Post by 5needinput on 2012-04-29
Sorry if I'm posting on an inactive thread, but thought I'd share the simplest method that worked for me...

I just had this exact problem on 11.10 and have now solved it thanks to Bachstelze.
Your link to [http://www.riverbankcomputing.co.uk/static/Docs/PyQt/html/qicon.html#fromTheme]("http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/qicon.html#fromTheme") was especially helpful.
I read a little on this page, then changed my code from:
```
exitAction = QtGui.QAction(QtGui.QIcon('exit.png'), '&Exit', self)
```to:
```
exitAction = QtGui.QAction(QtGui.QIcon.fromTheme('exit'), 'Exit', self)
```and it worked perfectly, thanks very much!

:KS:KS:KS:KS:KS

---

