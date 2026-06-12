---
title: "PyQt5 Question"
date: 2015-11-06
forum: Programming Talk
---

### Post by qkzoo on 2015-11-06
I'm playing around with PyQt5 on Lubuntu and have run into a snag just running the examples on [http://zetcode.com/gui/pyqt5/menustoolbars/](http://zetcode.com/gui/pyqt5/menustoolbars/) (examples lock up where .quit is issued) and it begged the question, where do I go for support?  I'm assuming this is probably not the right place, or, perhaps it is.  I'm pretty new to Python, so any pointers on where I should turn for help in this area would be appreciated!

---

### Post by matsuzine on 2015-11-07
Did you figure out the issue? I tried one of the examples from that page an everything worked for me. Could you post an example of code that's causing the issue?

I'm running on stock Ubuntu 15.10 / Unity, so we're using different desktop environments. 

Regarding support, this forum seems like a good place to start. StackOverflow is also a great resource if you're stuck, but not very friendly for casual questions. If you post on SO, be sure to read the guidelines first to properly format your question.

---

### Post by qkzoo on 2015-11-07
No, I haven't yet resolved the issue.  It freezes whenever it executes the code to quit.  For example, the menu bar tutorial on the page I listed above (posted below), the code executes fine, the window pops up, but when I click the exit button, the window freezes, and I have to force close it.  This happens with ALL the code examples on the first two tutorial pages that issue .quit() code.  If I close the windows that pop up using the X for the windows, they close fine, it's when I close them using one of the programmed .quit methods.

```

#!/usr/bin/python3
# -*- coding: utf-8 -*-

"""
ZetCode PyQt5 tutorial 

This program creates a menubar. The
menubar has one menu with an exit action.

author: Jan Bodnar
website: zetcode.com 
last edited: January 2015
"""

import sys
from PyQt5.QtWidgets import QMainWindow, QAction, qApp, QApplication
from PyQt5.QtGui import QIcon


class Example(QMainWindow):
    
    def __init__(self):
        super().__init__()
        
        self.initUI()
        
        
    def initUI(self):               
        
        exitAction = QAction(QIcon('exit.png'), '&Exit', self)        
        exitAction.setShortcut('Ctrl+Q')
        exitAction.setStatusTip('Exit application')
        exitAction.triggered.connect(qApp.quit)

        self.statusBar()

        menubar = self.menuBar()
        fileMenu = menubar.addMenu('&File')
        fileMenu.addAction(exitAction)
        
        self.setGeometry(300, 300, 300, 200)
        self.setWindowTitle('Menubar')    
        self.show()
        
        
if __name__ == '__main__':
    
    app = QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())  


```


[IMG][[IMG]http://s19.postimg.org/djsfx12mn/2015_11_07_212154_1366x768_scrot.jpg[/IMG]]("http://postimg.org/image/djsfx12mn/")[/IMG]

---

### Post by qkzoo on 2015-11-07
In case it matters, to install qt5 for Python, this is how I installed it:

```

sudo apt-get install python3-pyqt5
sudo apt-get install qtcreator

```

Perhaps, I missed installing something important?

---

### Post by matsuzine on 2015-11-08
Oh, thanks for posting that picture, it gave me the clue that I'm pretty sure is the answer to your problem! It looks like you're running it from inside the IDLE editor. IDLE has some weird quirks when running GUI applications. I was able to reproduce the problem in IDLE but not when running it directly from the command line.

Try running the code from a terminal instead of from within IDLE. Like this:

```

python3 tut7.py

```

---

### Post by qkzoo on 2015-11-08
Okay, when I try to run it from the command line, I run into another snag:

```

andrew@andrew-Satellite-P755:~/Programming/Python$ python tut8.py
Traceback (most recent call last):
  File "tut8.py", line 16, in <module>
    from PyQt5.QtWidgets import QMainWindow, QAction, qApp, QApplication
ImportError: No module named PyQt5.QtWidgets
andrew@andrew-Satellite-P755:~/Programming/Python$ 

```

From a quick search online of the error, it looks like I may need to correct my imports, or is there something else going on?

[http://stackoverflow.com/questions/20749819/pyqt5-failing-import-of-qtgui](http://stackoverflow.com/questions/20749819/pyqt5-failing-import-of-qtgui)

*edit*

Of course, when I try what suggested, I get:

```

andrew@andrew-Satellite-P755:~/Programming/Python$ python tut8.py
Traceback (most recent call last):
  File "tut8.py", line 16, in <module>
    from PyQt5 import QtCore, QtWidgets, QtGui
ImportError: No module named PyQt5

```

Is this maybe some kind of path issue, like it can't find the modules?

---

### Post by qkzoo on 2015-11-08
Whoops, never mind, I typed

```

python tut8.py

```

instead of

```

python3 tut8.py

```

Runs the way it should, now, thanks!!

---

### Post by matsuzine on 2015-11-08
So glad it works! 

Is there a way to mark the thread as solved?

---

### Post by qkzoo on 2015-11-08
Yep, marked as solved

Thanks :)

---

