---
title: "pyqt4 closeWindow and help Dialog"
date: 2008-05-30
forum: Programming Talk
---

### Post by tsic on 2008-05-30
Hello,
I have two things to ask
1) I have an help Dialog. So when I ask for the show from the mainWindow it does an error. I guess it's because I don't have a def run(self): in my interface help code. But What kind of code can I write in the def run if my help interface has just a label in wich I putted a QPixmap?

2) I want that in the menu/File/kit does the same work as closeEvent. I did a function def  closeEvent(self,event) it works.
My code seems like that:
[PHP]
def __init__(.......)
     self.connect(self.actionQuitter, QtCore.SIGNAL("triggered()"), self.kit)

....
def closeEvent(self,event):
  QmessageBox(...)

def kit(self, event):
        self.closeEvent(event)

[/PHP]   

kit doesn't work and raise an error message. How can I fixe that  or should I copy and paste the same code of closeEvent in my def kit.


Thank you.

---

