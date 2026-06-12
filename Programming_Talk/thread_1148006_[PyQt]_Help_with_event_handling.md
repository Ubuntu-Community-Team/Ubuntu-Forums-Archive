---
title: "[PyQt] Help with event handling"
date: 2009-05-03
forum: Programming Talk
---

### Post by dodle on 2009-05-03
I am connecting widgets with event handlers in PyQt and trying to find the widget that was used.  I learned to do this in wxPython:
[php]    button1 = wx.Button(self, -1, "Button 1")
    button2 = wx.Button(self, -1, "Button 2")
    button3 = wx.Button(self, -1, "Button 3")
    
    button_group = (button1, button2, button3)
    
    for entry in button_group:
        entry.Bind(wx.EVT_BUTTON, self.onButton)


def onButton(self, event):
    eventVal = event.GetEventObject()
    labelVal = eventVal.GetLabel()
    
    print "%s pressed" % labelVal
[/php]
But I am having trouble figuring out how to do this with PyQt.  This is the only way that I know how to catch events:
[php]    button1 = QtGui.QPushButton("Button 1")
    button2 = QtGui.QPushButton("Button 2")
    button3 = QtGui.QPushButton("Button 3")
    
    button_group = [button1, button2, button3]
    
    for entry in button_group:
        self.connect(entry, QtCore.SIGNAL('clicked()'), self.onButton)


def onButton(self):
    """
    I do not know what to put here.
    """
    pass
[/php]

---

### Post by dodle on 2009-05-04
I've got some of this worked out.  Here is what I have so far:
[php]#! /usr/bin/env python
"""
Mapping
"""
 
import sys
from PyQt4 import Qt
 
class MainWindow(Qt.QWidget):
    def __init__(self):
        Qt.QWidget.__init__(self)
        
        button1 = Qt.QPushButton("Button 1")
        button2 = Qt.QPushButton("Button 2")
        button3 = Qt.QPushButton("Button 3")
        
        self.button_mapper = Qt.QSignalMapper()
        
        button_group = [button1, button2, button3]
        
        for entry in button_group:
            self.connect(entry, Qt.SIGNAL('clicked()'), self.onButton)
            self.button_mapper.setMapping(entry, "blah")
        
        sizer = Qt.QVBoxLayout(self)
        sizer.addWidget(button1, 1)
        sizer.addWidget(button2, 1)
        sizer.addWidget(button3, 1)
 
    def onButton(self):
        eventVal = self.button_mapper.mapping("blah")
        labelVal = eventVal.text()
        print labelVal
 
app = Qt.QApplication(sys.argv)
frame = MainWindow()
frame.show()
sys.exit(app.exec_())
[/php]

But every button that I press prints out "Button 3".  How can I make it to where each button prints out its own label?

---

### Post by regomodo on 2009-05-04
#

---

### Post by dodle on 2009-05-04
That is *exactly* what I was looking for.  Thank you.

---

