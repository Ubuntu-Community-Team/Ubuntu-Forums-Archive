---
title: "Help with Python/PyQt4 Programming, please?"
date: 2007-02-03
forum: Programming Talk
---

### Post by alefterasm on 2007-02-03
Hey! I'm running into some issues with a program I'm developing for a nonprofit. I've starred out the sensitive stuff, but here it is. Any chance you could tell me where its going bad?
```

import sys
from PyQt4.Qt import *
from buspass import BuspassUi


class BusPassProgram(QApplication):

    def __init__(self, args):

        QApplication.__init__(self,args)
        self.buspass = Buspass(None)
        print self
        self.setMainWidget(self.buspass)
        self.buspass.show()
        self.exec_loop()

class Buspass(BuspassUi):

    def __init__(self, parent):

        BuspassUi.__init__(self, parent)

        
        self._connectSlots()

    def _connectSlots(self):
        self.connect(self.save, SIGNAL("clicked()"), self._slotSaveClicked)
        self.connect(self.exit, SIGNAL("clicked()"), self._slotExitClicked)

    def _slotSaveClicked(self):

        db = QSqlDatabase.addDatabase("QMYSQL")
        db.setHostName("localhost")
        db.setDatabaseName("*****")
        db.setUserName("*****")
        db.setPassword("*****")
        db.open()

        personu = self.person.text()
        idnumberu = self.idnumber.text()
        dateu = date.today()
        userinfofile = open("userinfo.txt")
        userinfo = userinfofile.readline()

        q = QSqlQuery()
        q.prepare("INSERT INTO ***** (name, dateissued , buspassID, user)"
                   "VALUES (personu, dateu, idnumberu, userinfo")
        q.exec_()

    def _slotExitClicked():

        self.quit()


if __name__ == "__main__":

    app = BusPassProgram(sys.argv)
```

Aaaand..
Here's the errors produced.

Traceback (most recent call last):
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 60, in <module>
    app = BusPassProgram(sys.argv)
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 14, in __init__
    self.buspass = Buspass(None)
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 27, in __init__
    self._connectSlots()
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 30, in _connectSlots
    self.connect(self.save, SIGNAL("clicked()"), self._slotSaveClicked)
AttributeError: 'Buspass' object has no attribute 'connect'


I would really appreciate your help with this, thanks!

Melody```
[CODE][CODE]
```[/CODE][/CODE]

---

### Post by jblebrun on 2007-02-03
> **alefterasm said:**
> Hey! I'm running into some issues with a program I'm developing for a nonprofit. I've starred out the sensitive stuff, but here it is. Any chance you could tell me where its going bad?

#!/usr/bin/env python


import sys
from PyQt4.Qt import *
from buspass import BuspassUi


class BusPassProgram(QApplication):

    def __init__(self, args):

        QApplication.__init__(self,args)
        self.buspass = Buspass(None)
        print self
        self.setMainWidget(self.buspass)
        self.buspass.show()
        self.exec_loop()

class Buspass(BuspassUi):

    def __init__(self, parent):

        BuspassUi.__init__(self, parent)

        
        self._connectSlots()

    def _connectSlots(self):
        self.connect(self.save, SIGNAL("clicked()"), self._slotSaveClicked)
        self.connect(self.exit, SIGNAL("clicked()"), self._slotExitClicked)

    def _slotSaveClicked(self):

        db = QSqlDatabase.addDatabase("QMYSQL")
        db.setHostName("localhost")
        db.setDatabaseName("*****")
        db.setUserName("*****")
        db.setPassword("*****")
        db.open()

        personu = self.person.text()
        idnumberu = self.idnumber.text()
        dateu = date.today()
        userinfofile = open("userinfo.txt")
        userinfo = userinfofile.readline()

        q = QSqlQuery()
        q.prepare("INSERT INTO ***** (name, dateissued , buspassID, user)"
                   "VALUES (personu, dateu, idnumberu, userinfo")
        q.exec_()

    def _slotExitClicked():

        self.quit()


if __name__ == "__main__":

    app = BusPassProgram(sys.argv)

Aaaand..
Here's the errors produced.

Traceback (most recent call last):
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 60, in <module>
    app = BusPassProgram(sys.argv)
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 14, in __init__
    self.buspass = Buspass(None)
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 27, in __init__
    self._connectSlots()
  File "C:\Documents and Settings\Administrator\Desktop\Project\buspassprogram.py", line 30, in _connectSlots
    self.connect(self.save, SIGNAL("clicked()"), self._slotSaveClicked)
AttributeError: 'Buspass' object has no attribute 'connect'


I would really appreciate your help with this, thanks!

Melody

This python code is impossible to read, because all tabs have been removed. Can you edit the post so that the code is enclosed by code tags?

As for your problem, is looks like the problem is with a third-party library (buspass) that you import. The base class does not have a connect method. Most likely, this buspass thing is not a Qt-based library... am I right? If so, it doesn't have slots and signals for you to connect. You can only use slots and signals in a class that derives from a Qt4 base class.

---

### Post by alefterasm on 2007-02-05
Thank you for your reply! I've fixed the post, as you suggested. How can I go about connecting the slots, then, if not using that method? That's what I find in all of the examples..

Thank you,

Melody

---

