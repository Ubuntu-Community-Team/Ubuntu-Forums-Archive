---
title: "Implementing a Push Button function using PyQt4"
date: 2011-10-27
forum: Programming Talk
---

### Post by craigdele on 2011-10-27
I wish to change the text of the QLabel  temp2lbl after pressing the calculate button. However this fails with the error "NameError: global name 'temp2lbl' is not defined".

Why can't the result(self): function see this label?

Dele

#!/usr/bin/python
# -*- coding: utf-8 -*-
#
# tempConverter.py

"""
Basic Window shell

"""

import sys
from PyQt4 import QtGui, QtCore

class Example(QtGui.QWidget):
    
    def __init__(self):
        super(Example, self).__init__()
        
        self.initUI()
        
    def initUI(self):
        
        # Declare widgets
        templbl = QtGui.QLabel("Enter Temperature : ", self)
        temp2lbl = QtGui.QLabel("Degrees", self)
        tmpentryLEdit= QtGui.QLineEdit(self)
        calculateBtn = QtGui.QPushButton("Calculate")
        clearBtn = QtGui.QPushButton("Clear")
        
        calculateBtn.clicked.connect(self.result)

        # first line widgets
        hBox1 = QtGui.QHBoxLayout()
        hBox1.addWidget(templbl)
        hBox1.addStretch(1)
        hBox1.addWidget(tmpentryLEdit)
        
        # second line widgets
        hBox2 = QtGui.QHBoxLayout()
        hBox2.addWidget(temp2lbl)

        
        # third line widgets
        hBox3 = QtGui.QHBoxLayout()
        hBox3.addStretch(1)
        hBox3.addWidget(calculateBtn)
        hBox3.addWidget(clearBtn)
        
        vbox = QtGui.QVBoxLayout()
        vbox.addLayout(hBox1)
        vbox.addLayout(hBox2)
        vbox.addStretch(1)
        vbox.addLayout(hBox3)
        
        self.setLayout(vbox) 
        
        self.setGeometry(300, 300, 500, 250)
        self.setWindowTitle("Temperature Converter")    
        self.show()
    

    def result(self):
        temp2lbl.setText("Fred")
     


        
def main():
    
    app = QtGui.QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()

---

### Post by 11jmb on 2011-10-27
Please use code tags, especially when posting long pieces of code


your problem is the scope of the variables. you declare temp2lbl in initUI and try to call it from result

instead make it an instance variable by calling it self.temp2lbl

---

### Post by craigdele on 2011-10-30
thanks for help, but I now get "NameError: global name 'temp2lbl' is not defined".

Why would this occur when it has been declare in initUI()

regards

Dele


```

#!/usr/bin/python
# -*- coding: utf-8 -*-
#
# tempConverter.py

import sys
from PyQt4 import QtGui, QtCore

class Example(QtGui.QWidget):
    
    def __init__(self):
        super(Example, self).__init__()
        
        self.initUI()
        
    def initUI(self):
        
        # Declare widgets
        templbl = QtGui.QLabel("Enter Temperature : ", self)
        self.temp2lbl = QtGui.QLabel("Degrees", self)
        tmpentryLEdit= QtGui.QLineEdit(self)
        self.calculateBtn = QtGui.QPushButton("Calculate")
        self.clearBtn = QtGui.QPushButton("Clear")
        
        self.calculateBtn.clicked.connect(self.result)

        # first line widgets
        hBox1 = QtGui.QHBoxLayout()
        hBox1.addWidget(templbl)
        hBox1.addStretch(1)
        hBox1.addWidget(tmpentryLEdit)
        
        # second line widgets
        hBox2 = QtGui.QHBoxLayout()
        hBox2.addWidget(temp2lbl)

        
        # third line widgets
        hBox3 = QtGui.QHBoxLayout()
        hBox3.addStretch(1)
        hBox3.addWidget(calculateBtn)
        hBox3.addWidget(clearBtn)
        
        vbox = QtGui.QVBoxLayout()
        vbox.addLayout(hBox1)
        vbox.addLayout(hBox2)
        vbox.addStretch(1)
        vbox.addLayout(hBox3)
        
        self.setLayout(vbox) 
        
        self.setGeometry(300, 300, 500, 250)
        self.setWindowTitle("Temperature Converter")    
        self.show()
    

    def result(self):
        self.temp2lbl.setText("Fred")
     
    

        
def main():
    
    app = QtGui.QApplication(sys.argv)
    ex = Example()
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()


```

---

### Post by gmargo on 2011-10-30
Looks like you missed one reference to temp2lbl, see second line of grep output below:
```

$ grep -n temp2lbl py1.py 
20:        self.temp2lbl = QtGui.QLabel("Degrees", self)
35:        hBox2.addWidget([COLOR=Red]temp2lbl[/COLOR])
58:        self.temp2lbl.setText("Fred")

```

---

### Post by craigdele on 2011-10-31
:D Thanks.

---

