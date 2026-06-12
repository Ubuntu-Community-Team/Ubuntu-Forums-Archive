---
title: "Pythen TypeError Regarding Number Of Arguments"
date: 2012-04-29
forum: Programming Talk
---

### Post by dniMretsaM on 2012-04-29
Ok, so I'm attempting to learn GUI programming with PyQt4 (Python 3). I'm writing this basic GUI that looks like a shut down dialog (might eventually be functional, don't know). Here's the code (I'm learning, so please excuse any n00bish mistakes. Also ignore the size button placement values, I jut threw them in there.):
```
#!/usr/bin/python3                                                                                                                                                        

import sys
from PyQt4 import QtGui

class Dialog(QtGui.QWidget):
    def __init__(self):
        super(Dialog, self).__init__()

        self.initUI()

    def button(label, tooltip, x, y, self):
        btn = QtGui.QPushButton(self.label)
        btn.setToolTip(self.tooltip)
        btn.resize(btn.sizeHint())
        btn.move(self.x, self.y)


    def initUI(self):
        QtGui.QToolTip.setFont(QtGui.QFont('SansSerif', 12))

        Dialog.button("Log out", "Return to the login screen.", 25, 25)
        Dialog.button("Reboot", "Restart the computer.", 25, 100)
        Dialog.button("Shut down", "Turn off the computer.", 25, 175)
        Dialog.button("Hibernate", "Put the computer to sleep.", 25, 250)
        Dialog.button("Cancel", "Retunr to the desktop.", 25, 325)

        self.resize(500, 500)
        self.center()
        self.show()

    def center(self):
        qr = self.frameGeometry()
        cp = QtGui.QDesktopWidget().availableGeometry().center()
        qr.moveCenter(cp)
        self.move(qr.topLeft())

def main():
    app = QtGui.QApplication(sys.argv)
    ex = Dialog()
    sys.exit(app.exec_())

if __name__ == "__main__":
    main()
```The error I get is this:
```
Traceback (most recent call last):
  File "./Power.py", line 44, in <module>
    main()
  File "./Power.py", line 40, in main
    ex = Dialog()
  File "./Power.py", line 10, in __init__
    self.initUI()
  File "./Power.py", line 22, in initUI
    Dialog.button("Log out", "Return to the login screen.", 25, 25)
TypeError: button() takes exactly 5 arguments (4 given)
```Now, I think kind of know what the problem is, but I have no idea how to fix it. I've done quite a bit of Googling (which is how I figured out the problem), but I didn't really find any info that would help me fix it. Any info someone could toss my way would be greatly appreciated.

---

### Post by cgroza on 2012-04-29
The "self" argument in button should go first. When you access that method from the other functions, you should refer to it using self and not Dialog.

I assumed you want button to be an instance method and not a class function.

That should fix the TypeError.

---

### Post by dniMretsaM on 2012-04-29
> **cgroza said:**
> The "self" argument in button should go first. When you access that method from the other functions, you should refer to it using self and not Dialog.

I assumed you want button to be an instance method and not a class function.

That should fix the TypeError.

Ok, fixed that error, but now I get this:
```
Traceback (most recent call last):
  File "./Power.py", line 44, in <module>
    main()
  File "./Power.py", line 40, in main
    ex = Dialog()
  File "./Power.py", line 10, in __init__
    self.initUI()
  File "./Power.py", line 22, in initUI
    self.button("Log out", "Return to the login screen.", 25, 25)
  File "./Power.py", line 13, in button
    btn = QtGui.QPushButton(self.label)
AttributeError: 'Dialog' object has no attribute 'label'
```

EDIT: Love your avatar, by the way.

---

