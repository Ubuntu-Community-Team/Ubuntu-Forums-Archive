---
title: "Python, global keyboard accelerators??"
date: 2008-06-17
forum: Programming Talk
---

### Post by joann on 2008-06-17
Hello,

I am writing an application, and I want the program to be able to respond to hot keys even when the application is minimized or not on the top level window. Essentially I want global keyboard accelerators that map specific keyboard combinations to specific callbacks. So far I have been able to do this with pyatspi, but I am not sure if this is the best (or most efficient) way to get what I want. Any suggestions?

Here is a little code snippit of what I have now:

```

#!/usr/bin/env python
#
# A simple test of the pyatspi
# keystrokelistener, it will listen for
# some keys and respond

import pyatspi

class monitor:
  def keypress_super_a (self):
    if self.history is 115:
        print "You just pressed <Super>A"

  def keypress_super_ins(self):
    if self.history is 115:
	print "You just pressed <Super>Ins"

  def keypress_super_del(self):
    if self.history is 115:
	print "You just pressed <Super>Del"

  def keylisten_cb(self, event):
    #print event

    # 38  = A
    # 106 = insert
    # 107 = delete
    # 115 = Super/Window
    if event.hw_code is 38:
      self.keypress_super_a ()
    if event.hw_code is 106:
      self.keypress_super_ins ()
    if event.hw_code is 107:
      self.keypress_super_del ()
    self.history = event.hw_code

  def __init__(self):
    # Register to listen to all events using pyatspi
    # I don't know if this is realy the best way to 
    # get global keyboard accelerators, but it seems to
    # work well
    self.reg = pyatspi.Registry
    self.reg.registerKeystrokeListener(self.keylisten_cb, mask=pyatspi.allModifiers())

    self.history = None

  def start(self):
      self.reg.start()

if __name__=="__main__":
  b = monitor()
  b.start()

```


- Joann

---

