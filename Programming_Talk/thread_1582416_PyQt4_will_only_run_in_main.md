---
title: "PyQt4 will only run in main???"
date: 2010-09-26
forum: Programming Talk
---

### Post by xaegis on 2010-09-26
I am programming in python 2.6 from repo and I am attempting to thread my gui using OyQt4.

When I did a Tk GUI I was able to run the GUI in a separate thread no problem, but when I try to do the same with QT I get errors.
Is my supposition that Qt4 will only run from the Main thread?

```

import os
import pickle
import sys
import threading
import time

import SW_CharacterX
import SW_CombatX
import SW_CharacterCreator

#Qt gui boilerplate
from PyQt4 import QtGui, QtCore
import SW_Gui_Qt


class ThaThread ( threading.Thread ):

   def run ( self ):
        #RUN CHARACTER CREATOR
        SW_CharacterCreator.main()  
        #RUN COMBAT
        SW_CombatX.Combat()
            
def main():
    #Again, Qt boilerplate...
    app = QtGui.QApplication(sys.argv)
    window = SW_Gui_Qt.MainWindow()  
    window.show()
    sys.exit(app.exec_())    

    return(0) 
    

if __name__ == '__main__':

    try:
        ThaThread().start()          
    except:
        print ("NO THREADING AVAILABLE")
        import sys
        sys.exit(1)

    main()

main

```

Is this the only way to do this or is there a better way?

Thank you in advance!

---

### Post by spjackson on 2010-09-26
> **xaegis said:**
> When I did a Tk GUI I was able to run the GUI in a separate thread no problem, but when I try to do the same with QT I get errors.
Is my supposition that Qt4 will only run from the Main thread?

See [http://doc.trolltech.com/4.6/threads-starting.html](http://doc.trolltech.com/4.6/threads-starting.html) "In GUI applications, the main thread is also called the GUI thread  because it's the only thread that is allowed to perform GUI-related  operations."

This also applies to PyQt.

---

### Post by xaegis on 2010-09-26
That is what I needed to know. Thanks! :)

---

