---
title: "PyQt-Signals and Slots: How do I do it?"
date: 2010-09-28
forum: Programming Talk
---

### Post by xaegis on 2010-09-28
I am programming in Python 2.6 and Qt4/PyQt from repo.
I was wondering if anyone could explain the signals and slots I should use to make QtextEdit display my print statements from my program. I cant seem to get the self.ui.textEdit to display  print("") functions from my other running module. 
I feel as though I am thinking about this all wrong but I an stuck. I have a copy of _*Rapid GUI programming with Python and Qt*_ but I just don't get it.
Can someone please explain how I can get the textEdit box to display the output from my program?

Thanks,

Sorry for the noobish post.

---

### Post by spjackson on 2010-09-29
I don't have that book, but I do know how to use signals and slots in Qt. I doubt that I could explain them any better than the many tutorials and examples out there.

If you post your code (or a minimal runnable part thereof), I might be able to see where you are going wrong.

---

### Post by xaegis on 2010-09-29
Thanks:


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
#import SW_Gui_Qt
from test import Ui_Form


#TODO: learn how to use MUTEX threads to lock the files being accessed by the thread.
class MyThread ( threading.Thread ):

   def run ( self ):
        #RUN CHARACTER CREATOR
        SW_CharacterCreator.main()  
        #RUN COMBAT
        SW_CombatX.Combat()
            
def main():
    #Again, Qt boilerplate... 
    app = QtGui.QApplication(sys.argv)
    myapp = SWForm_ui()     
    myapp.show()
    sys.exit(app.exec_())

    return(0) 
    
class SWForm_ui(QtGui.QMainWindow):
    
    def __init__(self, parent=None):
        QtGui.QWidget.__init__(self, parent)
        self.ui = Ui_Form()
        self.ui.setupUi(self)
        QtCore.QObject.connect(self.ui.pushButton, QtCore.SIGNAL("clicked()"), self.ui.textEdit.clear )
        QtCore.QObject.connect(self.ui.lineEdit, QtCore.SIGNAL("returnPressed()"),self.updateUi)
    
    def onChanged(self, text):
      
        self.label.setText(text)
        self.label.adjustSize()
        self.ui.textEdit(text)

    def add_entry(self):
        self.ui.textEdit.selectAll()
        self.ui.textEdit.cut()
        self.ui.textEdit.append("")
        self.ui.textEdit.paste()
        

    def updateUi(self):
        try:
            text = unicode(self.lineedit.text())
            self.ui.textEdit.append("%s = <b>%s</b>" % (text, eval(text)))
        except:
            self.ui.textEdit.append(
                "<font color=red>%s is invalid!</font>" % text)


if __name__ == "__main__":    

    try:
        #launches threaded window containing SW backend        
        MyThread().start()          
    except:
        print ("NO THREADING AVAILABLE")
        import sys
        sys.exit(1)

    main()[CODE]
```
[/CODE]

I just don't understand what I'm doing wrong. :(

---

### Post by xaegis on 2010-09-29
Where in the code  do I (am i supposed to) link my back-end to the signals and slots methods?

---

### Post by Bachstelze on 2010-09-29
Have a look here: [http://ftp.itsuki.fkraiem.org/pub/NALG/NALG-0.1rc3/](http://ftp.itsuki.fkraiem.org/pub/NALG/NALG-0.1rc3/)

It's quite old so I have forgotten exactly how it works, but it's something using slots and signals.  Basically, it's a GUI for the Nero Digital AAC encoder, the encoder runs in a QThread, and after it's done encoding, it sends a signal to the main app, which displays an "Encoding finished" popup.

---

### Post by xaegis on 2010-09-29
I'm examining your code now. I'll read this more closely when I get home from work. Thanks. :)

So far this jumps out at me!

```

self.emit(SIGNAL("encodingFinished"), self.__output)

```
From here:

```

class neroEncodingQThread(QThread) :

    def __init__(self, command) :
        QThread.__init__(self)

        self.__command = command

    def run(self) :

        #For some weird reason, the Nero Digital AAC encoder outputs its error
        #messages to stdout and its "normal" output to stderr.
        #
        #Long story short, no, I didn't mix things up here ;)
        (self.__err, self.__out) = os.popen3(self.__command)[1:]

        #Store output and error in a dict
        self.__output = {"out": self.__out.readlines(),
                         "err": self.__err.readlines()}

        self.emit(SIGNAL("encodingFinished"), self.__output)

```
if I use a Qthread I can just grab the output and possibly append it to the textEdit box. Is this correct?

---

### Post by Bachstelze on 2010-09-29
Yes, look at lines 435-436:

```
435         self.connect(self.encodingThread, SIGNAL("encodingFinished"),
436                 self.encodingFinished)

```

self here means my QMainWindow, so when the QThread emits the encodingFinished signal, the program will call the encodingFinished method of my QMainWindow, which is:

```
445     def encodingFinished(self, outputDict) :
446 
447         self.startButton.setText("Encode!")
448         self.startButton.setEnabled(True)
449         self.__encodingInProgress = False
450 
451         output = outputDict["out"]
452         error = outputDict["err"]
453 
454         curTime = time.strftime("%H:%M:%S")
455 
456         if len(error) == 0 :
457 
458             self.writeToLog("Encoding completed successfully.")
459             QMessageBox.information(self, "Encoding succeeded",
460                     "Encoding terminated successfully.")
461 
462         else :
463 
464             self.writeToLog("Encoding failed.")
465             self.writeToLog(error[0].rstrip("\n"));
466             QMessageBox.information(self, "Encoding failed",
467                     "Encoding failed. See the log for details.")
468 

```

Which basically writes the output of the encoder to the log file and displays the popup.  The data (here, it is the encoder output) is passed as the second argument of emit(), and connect() passes it on to the encodingFinished method.

So yeah, you will need a QThread: you need something with an emit() method so that it can emit the signal.

---

### Post by spjackson on 2010-09-29
> **xaegis said:**
> I just don't understand what I'm doing wrong. 
I'm sorry, I can't help you. The code you posted is incomplete so won't run. Furthermore, there is only one print statement, the one in the exception handler, so I don't follow how you expect non-existent print statements to send output to a QTextEdit (which isn't even created in the code you posted).

---

### Post by xaegis on 2010-09-29
> **spjackson said:**
> I'm sorry, I can't help you. The code you posted is incomplete so won't run. Furthermore, there is only one print statement, the one in the exception handler, so I don't follow how you expect non-existent print statements to send output to a QTextEdit (which isn't even created in the code you posted).

Yes it is incomplete because I don't know how to proceed from this point. I am asking for direction on how I should link the print statements I create in another(external) method to the QtextEdit mehtod in this one. It is exactly the methodology that I am missing! I don't know what I don't know but I know that I don't know it. :)

---

### Post by Bachstelze on 2010-09-29
Basically you need to do:

```

yourQTextEdit.connect(yourQThread, SIGNAL("yourSignal"),
                      yourQTextEdit.append)

```

And in your QThread, after it's done doing its thing:

```
self.emit(SIGNAL("yourSignal"), yourString)
```

yourString will be the argument to append().

---

### Post by xaegis on 2010-09-29
> **Bachstelze said:**
> Basically you need to do:

```

yourQTextEdit.connect(yourQThread, SIGNAL("yourSignal"),
                      yourQTextEdit.append)

```

And in your QThread, after it's done doing its thing:

```
self.emit(SIGNAL("yourSignal"), yourString)
```

yourString will be the argument to append().

Thanks, I'll try this!

---

### Post by xaegis on 2010-09-30
Ok, so I got the Qthreading to work properly but now I still cant figure out how to get the sys.stdout to function.
Here is the new code.
How should I redirect the stdout into the emit?

Thanks for all the input by the way!!!


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
#import SW_Gui_Qt
from test import Ui_Form
from PyQt4.QtCore import *
from PyQt4.QtGui import *





class SW_Thread(QThread):
    def __init__(self,) :
        QThread.__init__(self,)        
        self.emit(SIGNAL("textChanged()"), sys.stdout)
        
    def run(self) :  
        #RUN CHARACTER CREATOR
        SW_CharacterCreator.main()  
        #RUN COMBAT
        SW_CombatX.Combat()
        print ("PROGRAM EXIT")
        

            
def main():
    #Again, Qt boilerplate... 
    app = QtGui.QApplication(sys.argv)
    myapp = SWForm_ui()     
    myapp.show()
    sys.exit(app.exec_())

    return(0) 
    
class SWForm_ui(QtGui.QMainWindow):
    
    def __init__(self, parent=None):
        QtGui.QWidget.__init__(self, parent)
        self.ui = Ui_Form()
        self.ui.setupUi(self)
        QtCore.QObject.connect(self.ui.pushButton, QtCore.SIGNAL("clicked()"), self.ui.textEdit.show )
        QtCore.QObject.connect(self.ui.lineEdit, QtCore.SIGNAL("returnPressed()"), self.add_entry) 
        QtCore.QObject.connect(self.ui.textEdit, QtCore.SIGNAL("returnPressed()"), self.add_entry) 
        #QtCore.QObject.connect(self.ui.textEdit, QtCore.SIGNAL("returnPressed()"), self.append()) 

        self.ui.textEdit.connect( doit,SIGNAL("textChanged()"),self.ui.textEdit.append)
    def onChanged(self, text):
      
        self.label.setText(text)
        self.label.adjustSize()
        self.ui.textEdit(text)
       
    def readX(self,string):
        sys.stdin = string
        
    def writeX(string):
        spring = sys.stdout
        print (string)


    def add_entry(self):        
        self.ui.lineEdit.selectAll()
        self.ui.lineEdit.cut()
        self.ui.textEdit.paste()
        self.ui.textEdit.append("")
        
if __name__ == "__main__":
    #spawns the thread    
    doit = SW_Thread() 

    try:
        #launches Qthreaded window containing SW backend        
        doit.start()  
    except:
        print ("NO THREADING AVAILABLE")
        sys.exit(1)

    main()

```

---

### Post by spjackson on 2010-09-30
> **xaegis said:**
> Ok, so I got the Qthreading to work properly but now I still cant figure out how to get the sys.stdout to function.

Attached is a complete runnable example I have put together that does what I think you have said you want. i.e. the output of
```

    print "Message no. ", self.MessageCount

```gets appended to a QTextEdit.

Essentially the steps are:
   1. Replace sys.output with a custom class, overriding write and close.
   2. In the write method, emit a custom signal passing the text to be written.
   3. Connect the custom signal to a slot (which I've called append) that updates the QTextEdit.

---

### Post by xaegis on 2010-09-30
Thanks! But is this the best way to do this or is there another way that is preferable? In other words, is what I am attempting standard practice or is it just my own rube-goldberg way of doing things?

---

### Post by xaegis on 2010-09-30
Thank you sooo much for the great example!!!:)

---

