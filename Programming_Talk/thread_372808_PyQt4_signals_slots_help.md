---
title: "PyQt4 signals slots help"
date: 2007-02-28
forum: Programming Talk
---

### Post by binks on 2007-02-28
hi if i create a Ui.py in designer the run pyuic4 Ui to get Ui.py i can use it in a new app my i can use 
[HTML]from Ui.py import *[/HTML]

with a little code get it to show my Dialog 
but how can i connect the button from Ui.py to signals and slots here is some code from run.py but the signals slots dont connect

[HTML]from PyQt4 import QtCore, QtGui
from test import Ui_Dialog
import sys

class ImageDialog(QtGui.QDialog, Ui_Dialog):
    def __init__(self):
        QtGui.QDialog.__init__(self)

        # Set up the user interface from Designer.
        self.setupUi(self)

        # Make some local modifications.
        self.colorDepthCombo.addItem("2 colors (1 bit per pixel)")

        # Connect up the buttons.
        self.connect(self.okButton, QtCore.SIGNAL("clicked()"),
                     self, QtCore.SLOT("accept()"))
        self.connect(self.cancelButton, QtCore.SIGNAL("clicked()"),
                     self, QtCore.SLOT("reject()"))

app = QtGui.QApplication(sys.argv)
window = QtGui.QDialog()
ui = Ui_Dialog()
ui.setupUi(window)

window.show()
sys.exit(app.exec_())[/HTML]

can anyone steer me in the right direction please 
binks

---

### Post by binks on 2007-03-01
anyone no of a good tutorial for pyqt4 for begginers

---

