---
title: "PyQt : hover events on QGraphicsItem not triggered if mouse pressed"
date: 2009-09-04
forum: Programming Talk
---

### Post by cudjoe on 2009-09-04
I want to receive hoverEnter and hoverLeave whenever mouse enters and leaves, even if mouse buttons are pressed.

I tried drag event, listening from the scene and propagating events, ... I cannot find anything bringing me to the (clean simple) solution. 

It might be a one-liner. Any ideas please ?

I came back to a small example :

```

#!/usr/bin/python
import sys

from PyQt4.QtCore import *
from PyQt4.QtGui import *

class SlotItem(QGraphicsEllipseItem):
    SIZE = 40
    def __init__(self, pos):
        QGraphicsEllipseItem.__init__(self)
        self.setRect(pos.x(), pos.y(), self.SIZE, self.SIZE)
        self.setAcceptHoverEvents(True)

    def hoverEnterEvent(self, event):
        self.setBrush(Qt.yellow)
        QGraphicsEllipseItem.hoverEnterEvent(self, event)
    
    def hoverLeaveEvent(self, event):
        self.setBrush(Qt.green)
        QGraphicsEllipseItem.hoverLeaveEvent(self, event)


class DiagramScene(QGraphicsScene):
    def __init__(self, *args):
        QGraphicsScene.__init__(self, *args)
        self.addItem(SlotItem(QPointF(30,30)))
        self.addItem(QGraphicsTextItem("Hover events on item not triggered if mouse button pressed"))


class MainWindow(QMainWindow):
    def __init__(self, *args):
        QMainWindow.__init__(self, *args)
        self.scene = DiagramScene()
        self.view = QGraphicsView(self.scene)
        self.view.setRenderHint(QPainter.Antialiasing)
        self.setCentralWidget(self.view)

def main(args):
    app = QApplication(args)
    mainWindow = MainWindow()
    mainWindow.setGeometry(100, 100, 500, 40)
    mainWindow.show()

    # Qt Main loop
    sys.exit(app.exec_())


if __name__ == "__main__":
    main(sys.argv)

```

---

### Post by cudjoe on 2009-09-04
I could have something working by adding a custom event method and propagating events, but still don't like it.

What do you think ?

```

class DiagramScene(QGraphicsScene):
    def __init__(self, *args):
        ...
        
    def mouseMoveEvent(self, mouseEvent):
        if mouseEvent.buttons() != Qt.NoButton :
            for i in self.items(mouseEvent.scenePos()):
                if issubclass(i.__class__, SlotItem):
                    # Custom method in SlotItem :    
                    i.moveEvent(mouseEvent)
        QGraphicsScene.mouseMoveEvent(self, mouseEvent)

```

but I loose Enter and Leave events...

---

### Post by cudjoe on 2010-03-23
I can see I am not the only one suffering this bug : [http://bugreports.qt.nokia.com/browse/QTBUG-7765](http://bugreports.qt.nokia.com/browse/QTBUG-7765)

---

### Post by cudjoe on 2010-03-23
I could do this. But I find it quite heavy just because Qt mouse pressed behaviour...

```

class DiagramScene(QGraphicsScene):
    def __init__(self, *args):
        self.slotHover = None
        ...

    def mouseMoveEvent(self, mouseEvent):
        hoverslot = None
        for i in self.items(pos):
            if issubclass(i.__class__, SlotItem):
                hoverslot = i
        # Left
        if hoverslot is None and self.slotHover is not None:
            # Emit hoverLeave on self.slotHover
        # Entered
        if hoverslot is not None and self.slotHover is None:
            # Emit hoverEvent on hoverslot
        # Save for next move
        self.slotHover = hoverslot
        QGraphicsScene.mouseMoveEvent(self, mouseEvent)

```

---

