---
title: "[PyQt] Please check my code"
date: 2008-07-03
forum: Programming Talk
---

### Post by fifth on 2008-07-03
I am having problems with a QDateEdit widget. When its mapped to a database field I cannot tab through the widget. Hoping someone could be kind enough to try the following code and let me know if you see the same behavior?

Just want to check its not something I'm doing :confused:

```

#!/usr/bin/env python
import os
import sys
from PyQt4.QtCore import *
from PyQt4.QtGui import *
from PyQt4.QtSql import *

class ExampleDlg(QDialog):

    def __init__(self, parent=None):
        super(ExampleDlg, self).__init__(parent)
 
        label1 = QLabel("First Edit:")
        self.edit1 = QLineEdit()
        label2 = QLabel("Unmapped:")
        self.dateTime1 = QDateTimeEdit()
        label3 = QLabel("Mapped:")
        self.dateTime2 = QDateTimeEdit()
        label4 = QLabel("Second Edit:")
        self.edit2 = QLineEdit()
 
        layout = QGridLayout()
        layout.addWidget(label1, 0, 0)
        layout.addWidget(self.edit1, 0, 1, 1, 3)
        layout.addWidget(label2, 1, 0)
        layout.addWidget(self.dateTime1, 1, 1)
        layout.addWidget(label3, 1, 2)
        layout.addWidget(self.dateTime2, 1, 3)
        layout.addWidget(label4, 2, 0)
        layout.addWidget(self.edit2, 2, 1, 1, 3)
        self.setLayout(layout)
 
        self.model = QSqlRelationalTableModel(self)
        self.model.setTable("test")
        self.model.select()

        self.mapper = QDataWidgetMapper(self)
        self.mapper.setSubmitPolicy(QDataWidgetMapper.ManualSubmit)
        self.mapper.setModel(self.model)
        self.mapper.setItemDelegate(QSqlRelationalDelegate(self))
        self.mapper.addMapping(self.edit1, 1)
        #self.mapper.addMapping(self.dateTime1, 2)
        self.mapper.addMapping(self.dateTime2, 3)
        self.mapper.addMapping(self.edit2, 4)
        self.mapper.toFirst()
 
app = QApplication(sys.argv)
filename = os.path.join(os.path.dirname(__file__), "example.db")
db = QSqlDatabase.addDatabase("QSQLITE")
db.setDatabaseName(filename)
if not db.open():
    sys.exit(1)
form = ExampleDlg()
form.show()
sys.exit(app.exec_()

```

---

### Post by fifth on 2008-07-06
Can anyone confirm the behavior?

I'm still stumped by this, it makes the form very unintuitive for users.

---

### Post by LinuX-M@n1@k on 2008-07-06
bump :)

---

