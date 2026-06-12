---
title: "[PyQt4] Want to connect a window's close button"
date: 2009-05-10
forum: Programming Talk
---

### Post by dodle on 2009-05-10
I want to connect the "x" button on my program's main window with a function that I created.  I know how to do it in wxPython:
```
self.Bind(wx.EVT_CLOSE, self.onQuit)

```

But I can't figure out how to do it with PyQt4.  I've tried:
```
self.connect(self, Qt.SIGNAL('quit()'), self.onQuit)

```and
```
self.connect(self, Qt.SIGNAL('destroyed()'), self.onQuit)

```

---

### Post by dodle on 2009-05-10
Figured it out with the help of [http://zetcode.com/tutorials/pyqt4/firstprograms/](http://zetcode.com/tutorials/pyqt4/firstprograms/)

I just had to rename my function to "closeEvent", and then connect to it:
[php]    self.connect(self, Qt.SIGNAL('triggered()'), self.closeEvent

def closeEvent(self, event):
    print "Closing"
    self.destory()[/php]

---

### Post by fifth on 2009-05-11
> **dodle said:**
> Figured it out with the help of [http://zetcode.com/tutorials/pyqt4/firstprograms/](http://zetcode.com/tutorials/pyqt4/firstprograms/)

I just had to rename my function to "closeEvent", and then connect to it:
[php]    self.connect(self, Qt.SIGNAL('triggered()'), self.closeEvent

def closeEvent(self, event):
    print "Closing"
    self.destory()[/php]

self.destroy() might give you some problems, although maybe not visibly if its the last application window your closing. You might be better off using;

```
self.deleteLater()
```

Qt will then destroy the object when its no longer being used.

---

### Post by tollboy on 2009-07-03
thanxs i was searching for this [:)]

---

