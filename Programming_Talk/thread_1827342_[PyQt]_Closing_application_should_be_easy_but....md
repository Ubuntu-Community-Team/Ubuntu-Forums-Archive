---
title: "[PyQt] Closing application should be easy but..."
date: 2011-08-17
forum: Programming Talk
---

### Post by PaulWhipp on 2011-08-17
I'm learning PyQt and I've built a login dialog and a main window that work ok. Here is my main.pyw that launches the application:

```
import sys
from PyQt4.QtCore import SIGNAL, SLOT
from PyQt4.QtGui import QApplication
from main_window import MainWindow

if __name__ == "__main__":

    app = QApplication(sys.argv)
    app.connect(app, SIGNAL("lastWindowClosed()"),
                app, SLOT("quit()"))
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())
```

I'm not sure if I need the lastWindowClosed signal since the documentation says that the application quits by default if the last window is closed.

I want my login to come up automatically on application launch and have the application terminate if the login is not successful. Here is the code snippet I have to do this:

```
class MainWindow(QMainWindow, Ui_MainWindow):
    def __init__(self, parent = None):
        QMainWindow.__init__(self, parent)
        self.setupUi(self)

        self.login_dialog = LoginDialog()

    def show(self):
        QMainWindow.show(self)
        (credentials, ok) = self.login_dialog.login()
        if ok:
            self.statusBar().showMessage('Login successful')
        else:
            self.statusBar().showMessage('Login was cancelled')
            self.close()
```

Sadly it doesn't work. The window closes fine but the Qt application just hangs never terminating.

What is the right way to cleanly close the main window and exit the application? I've gone round in circles with google :(

---

### Post by karlson on 2011-08-17
> **PaulWhipp said:**
> I'm learning PyQt and I've built a login dialog and a main window that work ok. Here is my main.pyw that launches the application:

```
import sys
from PyQt4.QtCore import SIGNAL, SLOT
from PyQt4.QtGui import QApplication
from main_window import MainWindow

if __name__ == "__main__":

    app = QApplication(sys.argv)
    app.connect(app, SIGNAL("lastWindowClosed()"),
                app, SLOT("quit()"))
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())
```

I'm not sure if I need the lastWindowClosed signal since the documentation says that the application quits by default if the last window is closed.

I want my login to come up automatically on application launch and have the application terminate if the login is not successful. Here is the code snippet I have to do this:

```
class MainWindow(QMainWindow, Ui_MainWindow):
    def __init__(self, parent = None):
        QMainWindow.__init__(self, parent)
        self.setupUi(self)

        self.login_dialog = LoginDialog()

    def show(self):
        QMainWindow.show(self)
        (credentials, ok) = self.login_dialog.login()
        if ok:
            self.statusBar().showMessage('Login successful')
        else:
            self.statusBar().showMessage('Login was cancelled')
            self.close()
```

Sadly it doesn't work. The window closes fine but the Qt application just hangs never terminating.

What is the right way to cleanly close the main window and exit the application? I've gone round in circles with google :(

There used to be a program generating PyQT code from the interface file.  I am sure it's still there.

My suggestion would be to use QT Designer first and then generate Python code from it because from what I can gather you are trying to catch a signal from an incorrect object.  Rather then trying to catch last window closed catch "close()" from the MainWindow.

---

### Post by PaulWhipp on 2011-08-17
Thanks for the response.

I did use Qt4 designer to make both the main window and the login dialog. The Qt designer code supplies the Ui_MainWindow class in the code above using pyuic4 which is the code I think you are talking about.

I don't logically need to use an event - I'd just like to call something that closes the entire application down cleanly. I think the lastwindowclosed signal should work though but for some reason, its not doing anything (no error no nothing).

---

### Post by karlson on 2011-08-19
> **PaulWhipp said:**
> Thanks for the response.

I did use Qt4 designer to make both the main window and the login dialog. The Qt designer code supplies the Ui_MainWindow class in the code above using pyuic4 which is the code I think you are talking about.

I don't logically need to use an event - I'd just like to call something that closes the entire application down cleanly. I think the lastwindowclosed signal should work though but for some reason, its not doing anything (no error no nothing).

There is a function in QT called setQuitOnLastWindowClose(true) which will do the same thing.

---

### Post by benson444 on 2011-08-20
I think the problem is that app.exec_() is being called after window.show() returns. The event loop exits on self.close(), which calls app.quit(), but is immediately restarted.

You could enter the event loop conditionally, based on whether the user is legit. Something like this?

```
#!/usr/bin/env python

import sys
from PyQt4.QtCore import *
from PyQt4.QtGui import *

class MainWindow(QMainWindow):
    def __init__(self, parent = None):
        super(MainWindow, self).__init__(parent)
        self.resize(200, 200)
        self.logWin = LoginWindow(self)

    def login(self):
        return self.logWin.exec_() and self.logWin.verifyUser()

class LoginWindow(QDialog):
    def __init__(self, parent = None):
        super(LoginWindow, self).__init__(parent)
        passwdLabel = QLabel('Password')
        self.passwd = QLineEdit()
        self.passwd.setEchoMode(QLineEdit.Password)
        okButton = QPushButton('OK')
        cancelButton = QPushButton('Cancel')
        self.connect(okButton, SIGNAL('clicked()'), SLOT('accept()'))
        self.connect(cancelButton, SIGNAL('clicked()'), SLOT('reject()'))
        layout = QFormLayout()
        layout.addRow(passwdLabel, self.passwd)
        layout.addRow(cancelButton, okButton)
        self.setLayout(layout)

    def verifyUser(self):
        if self.passwd.text().isEmpty():
            return False
        else:
            # If user is legit
            return True

if __name__ == '__main__':
    app = QApplication(sys.argv)
    win = MainWindow()
    win.show()
    ok = win.login()
    if ok:
        sys.exit(app.exec_())
```

---

