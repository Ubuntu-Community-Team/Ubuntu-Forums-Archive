---
title: "PyQt: Exiting Process"
date: 2011-02-26
forum: Programming Talk
---

### Post by Sailor5 on 2011-02-26
Greetings!

So currently when the 'X' button is pressed the window disappears and the process carries on. I simply need to raise SystemExit when the 'X' button is pressed and everything will be tip-top. But I'm having trouble figuring out how to do such. I've come up with this but it doesn't work.

```
QtCore.QObject.connect(self, QtCore.SIGNAL('triggered()'), 
           self.Exit())
```

Anyone know how to do this?

Thanks bye!

---

### Post by tseliot on 2011-02-26
Maybe something like this?

```
sys.exit(app.exec_())
```

Where "app" is your QApplication:

```
app = QtGui.QApplication(sys.argv)
```

---

### Post by Sailor5 on 2011-02-26
> **tseliot said:**
> Maybe something like this?

```
sys.exit(app.exec_())
```Where "app" is your QApplication:

```
app = QtGui.QApplication(sys.argv)
```

I already appear to have that.```

def Window():
    app = QtGui.QApplication(sys.argv)
    Form = QtGui.QWidget()
    ui = Ui_Form()
    ui.Chimera(Form)
    Form.show()
    sys.exit(app.exec_())
```The process still doesn't exit upon exiting the window.

---

### Post by tseliot on 2011-02-26
Maybe you can reimplement QWidget.closeEvent ?

I can't be sure about what's going on without seeing the full code.

---

### Post by Sailor5 on 2011-02-26
> **tseliot said:**
> Maybe you can reimplement QWidget.closeEvent ?

I can't be sure about what's going on without seeing the full code.

Somebody on IRC gave me this```

#!/usr/bin/python
from PyQt4.QtCore import *
from PyQt4.QtGui import *
import sys

class MyWindow(QWidget):
    def __init__(self, parent=None):
        QWidget.__init__(self, parent)
        self.label = QLabel("Hi, I'm a window", self)
        self.button = QPushButton("&Quit", self)
        self.connect(self.button, SIGNAL("clicked()"), QCoreApplication.instance(), SLOT("quit()"))
        lay = QVBoxLayout()
        lay.addWidget(self.label)
        lay.addWidget(self.button)
        self.setLayout(lay)

app = QApplication(sys.argv)
mw = MyWindow()
mw.show()
sys.exit(app.exec_())

```

Upon pushing the button the window exits and so does the process. But that's when you press the button. How can I do that when the 'X' button is pressed? My mind seems rather muddle. After this I think I'll retire for today :)

---

### Post by tseliot on 2011-02-26
You can reimplement closeEvent, as I suggested and call either deleteLater() or destroy() from there, as in this example.

[PHP]#!/usr/bin/python
from PyQt4.QtCore import *
from PyQt4.QtGui import *
import sys

class MyWindow(QWidget):
    def __init__(self, parent=None):
        QWidget.__init__(self, parent)
        self.label = QLabel("Hi, I'm a window", self)
        self.button = QPushButton("&Quit", self)
        self.connect(self.button, SIGNAL("clicked()"), QCoreApplication.instance(), SLOT("quit()"))

        lay = QVBoxLayout()
        lay.addWidget(self.label)
        lay.addWidget(self.button)
        self.setLayout(lay)

    def closeEvent(self, event):
        print "Closing the app"
        self.deleteLater()

if __name__ == '__main__':
    app = QApplication(sys.argv)
    mw = MyWindow()
    mw.show()
    sys.exit(app.exec_())[/PHP]

---

