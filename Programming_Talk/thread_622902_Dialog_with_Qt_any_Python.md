---
title: "Dialog with Qt any Python"
date: 2007-11-25
forum: Programming Talk
---

### Post by NeillHog on 2007-11-25
I have now been playing with Python for a few months. I have written a few very simple utilities where I use Qt for the GUI.
```

Thanks to these forums and all the help I have received I have solved most problems but now I am totally stumped.

I have a program which runs in a main window and now I want to add a second "about" window called through help->about.

I have designed the main window and dialog window with Qt3. The main window works but I can not get the dialog window to appear.

My program (without all the boring details) looks like this

[CODE]
#!/usr/bin/env python

from gui import GUI #the GUI programmed with qt Developer
from about import formAbout

class GPSBabelWrapper(QApplication):
    
	def __init__(self, args):
		QApplication.__init__(self,args)
		self.maindialog = theApp(None)

		self.setMainWidget(self.maindialog)
		self.maindialog.show()
		self.exec_loop()     

class aboutDlg(formAbout):

	def __init__(self,parent):
		# Run the parent constructor and connect the slots to methods.
		formAbout.__init__(self,parent)

class theApp(GUI):

	def __init__(self,parent):
		# Run the parent constructor and connect the slots to methods.
		GUI.__init__(self,parent)
		self._connectSlots()


	def _connectSlots(self):
		self.connect(self.helpAboutAction,SIGNAL("activated()"),self._onAbout)	


	def _onAbout(self):
		aboutDlg.show(self)

if __name__ == "__main__":
	app = GPSBabelWrapper(sys.argv)

```

Whwn I press the about menu point I get the error
TypeError: first argument of unbound method QDialog.show() must be a QDialog instance

In the file about.py is
```

# -*- coding: utf-8 -*-
from qt import *

class formAbout(QDialog):
    def __init__(self,parent = None,name = None,modal = 0,fl = 0):
        QDialog.__init__(self,parent,name,modal,fl)
        if not name:
            self.setName("formAbout")
        self.textLabelAbout = QLabel(self,"textLabelAbout")
        self.textLabelAbout.setGeometry(QRect(50,40,100,20))
        self.languageChange()
        self.resize(QSize(335,222).expandedTo(self.minimumSizeHint()))
        self.clearWState(Qt.WState_Polished)

    def languageChange(self):
        self.setCaption(self.__tr("About"))
        self.textLabelAbout.setText(self.__tr("textLabel1"))

    def __tr(self,s,c = None):
        return qApp.translate("formAbout",s,c)

```

Maybe I am making some stupid fundamental mistake. I would really appreciate any and all help.

Thank you!
Neill

---

### Post by NeillHog on 2007-11-25
This thread is meant to be called "Dialog with Qt and Python" but there seems to be no way to change the name.

I hope "the expert" stumbles over it anyway - because I am really getting no where fast.

Neill

---

