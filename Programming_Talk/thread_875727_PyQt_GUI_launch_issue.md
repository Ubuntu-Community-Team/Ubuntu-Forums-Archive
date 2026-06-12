---
title: "PyQt GUI launch issue"
date: 2008-07-31
forum: Programming Talk
---

### Post by gvanto on 2008-07-31
I'm having some trouble getting a Qt Designer-designed 
form launched in python. 

I have installed PyQt and run pyuic4 to transform the resulting mytest.ui 
into mytest.py (code below):
```


# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'mytest.ui'
#
# Created: Thu Jul 31 17:40:29 2008
#      by: PyQt4 UI code generator 4.4.2
#
# WARNING! All changes made in this file will be lost!

from PyQt4 import QtCore, QtGui

class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(519,505)
        self.centralwidget = QtGui.QWidget(MainWindow)
        self.centralwidget.setGeometry(QtCore.QRect(0,30,519,452))
        self.centralwidget.setObjectName("centralwidget")
        self.btnOne = QtGui.QPushButton(self.centralwidget)
        self.btnOne.setGeometry(QtCore.QRect(50,290,101,28))
        self.btnOne.setObjectName("btnOne")
        self.txfOne = QtGui.QLineEdit(self.centralwidget)
        self.txfOne.setGeometry(QtCore.QRect(50,40,113,24))
        self.txfOne.setObjectName("txfOne")
        self.lwgtOne = QtGui.QListWidget(self.centralwidget)
        self.lwgtOne.setGeometry(QtCore.QRect(50,80,256,192))
        self.lwgtOne.setObjectName("lwgtOne")
        MainWindow.setCentralWidget(self.centralwidget)
        self.menubar = QtGui.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0,0,519,30))
        self.menubar.setObjectName("menubar")
        self.menuHelloFile = QtGui.QMenu(self.menubar)
        self.menuHelloFile.setObjectName("menuHelloFile")
        MainWindow.setMenuBar(self.menubar)
        self.statusbar = QtGui.QStatusBar(MainWindow)
        self.statusbar.setGeometry(QtCore.QRect(0,482,519,23))
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)
        self.menuHelloFile.addSeparator()
        self.menubar.addAction(self.menuHelloFile.menuAction())

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        MainWindow.setWindowTitle(QtGui.QApplication.translate("MainWindow", "MainWindow", None, QtGui.QApplication.UnicodeUTF8))
        self.btnOne.setText(QtGui.QApplication.translate("MainWindow", "Try Me!", None, QtGui.QApplication.UnicodeUTF8))
        self.menuHelloFile.setTitle(QtGui.QApplication.translate("MainWindow", "HelloFile", None, QtGui.QApplication.UnicodeUTF8))


```


My problem is, I need to now somehow launch this little GUI (only contains one button and a textfield)

Does anyone know what I need to do in my main method to launch it? :-)

```

from PyQt4 import QtCore, QtGui

from mytest import *
import sys


if __name__ == "__main__":
    	
	#something here to launch my GUI
	# can't just do Ui_MainWindow()
	


```


Help much appreciated!

Gerry
Qt/PyQt newbie

---

### Post by henchman on 2008-07-31
well, i can show you how to do it in C++

```

QMainWindow widget;
Ui::myCreatedWindow mywidget;
mywidget.setupUi( &widget );
widget.show();

```

The python implementation will surely be similar... Perhaps just leave the ';' out :) 

The Ui:: is a namespace thingy from the c++ implementation in Qt. Apparently there is no such thing in the python version...

from my limited python skills, i would recommend trying 

```

widget = QMainWindow()
mywidget = Ui_MainWindow()
mywidget.setupUi( widget )
widget.show()

```

hf :)

---

### Post by gvanto on 2008-07-31
thanks alot this did the trick just fine!

---

