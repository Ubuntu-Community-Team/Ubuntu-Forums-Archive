---
title: "Closing QT/Python app when Ubuntu closes"
date: 2008-11-18
forum: Programming Talk
---

### Post by sjbaugh on 2008-11-18
I have written an app in qt4 and Python using PyQt4. I keep closing it when I don't mean to, so I have overrided the closeEvent method of QMainWindow:

```
   def closeEvent(self,event):     #override inherited method
        """Check to see if it is OK to close."""
        
        #use QMessageBox
        if self.ShowYesNo('Do you want to close the application?')==QtGui.QMessageBox.Yes:
            # clean up...
            event.accept()      #allow app to close
        else:
            event.ignore()      #do not allow app to close
```

This works well, but when I close Ubuntu I would like it to close the app without asking this question. Is there a way to do it?

Thanks, Steve

---

### Post by slavik on 2008-11-18
I am pretty sure your program will get a signal of 15 (SIGTERM) when the kernel is going for a shutdown. also, if you close just X, I am sure your program will die with an exception because there is nowhere it can be drawn to.

---

### Post by sjbaugh on 2008-11-19
slavik,

thanks for your comment.

Pardon my lack of expertise with Qt, but I can't quite work out how to trap this signal with connect(...).

I have the following in __init__ of QMainWindow:
```

        self.ui = Ui_MainWindow()
        self.ui.setupUi(self)
      
        #Connect the Exit button to the inherited close() SLOT
        self.connect(self.ui.pushButtonExit, QtCore.SIGNAL('clicked()'), self, QtCore.SLOT('close()'))
        
        #Connect the signals from the Widgets to methods of this class
        self.connect(self.ui.pushButtonWebPage, QtCore.SIGNAL('clicked()'), self.doWebPage)
        #connect statements for other widgets
 
```

At present the program halts the shutdown process until this question is answered.

Steve

---

### Post by slavik on 2008-11-19
this would be a signal sent by the kernel (SIGTERM) ... and would have to be handled by the underlying code (in Python).

EDIT: you don't have to capture it unless there is something you MUST do when closing the app (like if it might have something in memory that needs to be on disk). by default all apps that don't handle a signal, die. that and kernel also sends SIGKILL after sending everyone SIGTERM.

---

### Post by sjbaugh on 2008-11-19
Thanks I shall look into it. I hoped there would be something like an isClosing() function.

At present it kills the festival server that the program starts on entry. I suppose this would be stopped OK when the kernel closes anyway.

Thanks,

Steve

---

### Post by sjbaugh on 2008-11-19
The plot thickens. I have found how to trap the SIGTERM but before I implemented it I have found that under 8.10 the app closes immediately anyway. I am not sure that closeEvent is even being called now on system shutdown. I'm sure it used to.

Steve

---

