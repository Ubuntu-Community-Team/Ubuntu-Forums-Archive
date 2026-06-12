---
title: "PyQt4 - no menu bar?!?"
date: 2012-05-05
forum: Programming Talk
---

### Post by memilanuk on 2012-05-05
Hello all,

So, working my way thru learning PyQt4 using the book 'Intro to Python Programming & Developing GUI Applications with PyQT, 1st ed.'.  I'm using Python 2.7.3 on Ubuntu 12.04, PyQt4, Qt Designer & PyDev.

Everything was going along pretty well until I hit the section on creating a menu bar.  I put the UI together using QT Designer, and typed in the code for the main program that calls the UI module... and no menu bar.  I went over this a number of times, even to the point of starting over completely.  No change.  So I headed over to zetcode.com and typed in the menu bar example from the [PyQt tutorial]("http://zetcode.com/tutorials/pyqt4/menusandtoolbars/") over there.

It does the same thing.  I get a window, with no menu bar whatsoever.

Here is the code from that simpler example:

```

#!/usr/bin/python
# -*- coding: utf-8 -*-

"""
ZetCode PyQt4 tutorial 

This program creates a menubar. The
menubar has one menu with an exit action.

author: Jan Bodnar
website: zetcode.com 
last edited: August 2011
"""

import sys
from PyQt4 import QtGui

class Example(QtGui.QMainWindow):
    
    def __init__(self):
        super(Example, self).__init__()
        
        self.initUI()
        
    def initUI(self):               
        
        exitAction = QtGui.QAction(QtGui.QIcon('exit.png'), '&Exit', self)        
        exitAction.setShortcut('Ctrl+Q')
        exitAction.setStatusTip('Exit application')
        exitAction.triggered.connect(QtGui.qApp.quit)

        self.statusBar()

        menubar = self.menuBar()
        fileMenu = menubar.addMenu('&File')
        fileMenu.addAction(exitAction)
        
        self.setGeometry(300, 300, 300, 200)
        self.setWindowTitle('Menubar')    
        self.show()
        
        
def main():
    
    app = QtGui.QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()  

```

Any idea why I wouldn't be seeing a menu bar at all?

TIA,

Monte

---

### Post by r-senior on 2012-05-05
I just cut and pasted that and it worked OK for me on 12.04.

I hesitate to say this but you are looking in the right place aren't you? Right up at the top of the screen, not in the window itself?

---

### Post by memilanuk on 2012-05-05
> **r-senior said:**
> I hesitate to say this but you are looking in the right place aren't you? Right up at the top of the screen, not in the window itself?

Ahhhhh... nuts.  

PyDev uses its own menu bar (probably because its a java-based app?) so when the pyqt window opened I didn't even think to look up over in the corner.

Sheesh...  :oops:

---

### Post by r-senior on 2012-05-06
> **memilanuk said:**
> Sheesh...  :oops:
I've done *exactly* the same thing with Glade -- preview the window and the menu is there but run it and it has "disappeared". Then spend half an hour trying to figure out why. :-P

---

