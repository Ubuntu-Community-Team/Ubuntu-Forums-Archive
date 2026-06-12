---
title: "pyqt - multithreading basic question"
date: 2008-02-20
forum: Programming Talk
---

### Post by jayke87 on 2008-02-20
Hey,

This is my first post on the Ubuntu forums, so i apologize if this isn't the right place to post my question. 

I'm pretty new to PyQt, and created my first application [ImageTools]("http://jayke.ulyssis.be/homepage/?tab=3&item=4") this summer. It's got a rename feature that shows thumbnails, but when creating these **the GUI hangs when the files get big**. That's why I'd like to put the **calculation of the thumbnail in a seperate secondary thread. **

I've come up with this so far:

extract primary class:
```
class renamewidget(QWidget):
    def __init__(self, leftwidget, sb, parent=None):
        QWidget.__init__(self, parent)
        ...        
        self.lock = QMutex()
        self.thumbnailgenerator = thumbnailgenerator(self.lock, self)
        
        QObject.connect(self.thumbnailgenerator, SIGNAL("finished(QPixmap)"), self.displaythumbnail)

       ...

    def showthumbnail(self, path):
        self.thumbnailgenerator.initialize(path, self.height(), self.ui.labelimagepreview) 
        self.thumbnailgenerator.start()
        self.ui.labelimagepreview.setText("creating preview")

    def displaythumbnail(self, pixmap):
        self.ui.labelimagepreview.setPixmap(scaledpixmap)

```

A bit of info:
I create an instance of my secondary thread in the constructor of this class, and create a QMutex. Then there are two functions, the first just sets up the secondary thread, then gives the start command, while displaying a notification in the label. The secondary thread (see below) should do the processing and emit a finished signal, which then triggers the second function. The second function should display the pixmap on the label.

secondary class:
```
class thumbnailgenerator(QThread):
    def __init__(self, lock, parent=None):
        super(thumbnailgenerator, self).__init__(parent)
        self.lock = lock
        
    def initialize(self, path, height, label):
        self.path = path
        self.height = height
        self.label = label
                
    def run(self):
        imagepreview = QPixmap(self.path) 
        h = self.height / 2
        transfotype = Qt.FastTransformation
        try:
            self.lock.lock()
            scaledpixmap = imagepreview.scaledToHeight(h,transfotype)
        finally:
            self.lock.unlock()
        
        self.emit(SIGNAL("finished(QPixmap)"), scaledpixmap)
```

When I run this, my application starts, then I select my picture, and the waiting message appears on my label. But then I get all sorts of weird output::
```

Xlib: sequence lost (0x1ff5b > 0x3127) in reply type 0x58!
Xlib: sequence lost (0x1ff53 > 0x3127) in reply type 0x52!
_and so on_
Xlib: sequence lost (0x1ff2c > 0x3128) in reply type 0x15!
Xlib: sequence lost (0x1ff17 > 0x3128) in reply type 0x0!
X Error: 21 21
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0xff251f07
Xlib: sequence lost (0x1ff35 > 0x3128) in reply type 0x1f!
_and so on_
Xlib: sequence lost (0x1ff34 > 0x3128) in reply type 0xe!
Xlib: sequence lost (0x1ff0c > 0x3128) in reply type 0xf!
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    236 (Uknown extension)
  Minor opcode: 177 (Unknown request)
  Resource id:  0xff8c8769
Xlib: sequence lost (0x1ff15 > 0x3128) in reply type 0x1e!
Xlib: sequence lost (0x1ff2b > 0x3128) in reply type 0xe!
_and so on_
Xlib: sequence lost (0x1ff05 > 0x3128) in reply type 0x2!
Xlib: sequence lost (0x1ff01 > 0x3128) in reply type 0x1!
imagetools.py: Fatal IO error: client killed

```

As I said, I'm pretty new to python and Qt, and have no previous expertise with threading. I'm actually not even sure if the QMutex is needed. I believe the error occurs on the statement below, since omitting the emit signal doesn't make a difference.
```
scaledpixmap = imagepreview.scaledToHeight(h,transfotype)
```

I've googled about quiet a while now, but can't find a real sollution. I know only the primary thread can make changes to the GUI, so I tried to work my way around that with a signal. I also found some things about 'Implicit Sharing' on the Qt Docs pages, but I don't know if that's got to do anything with the problem.

Any help or suggestions would be enormously appreciated :-) 
Again, if this isn't the right place, please just tell me and/or refer me to the right place.

---

