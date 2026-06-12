---
title: "Qt : setVisible() on a group child changes the group selected state"
date: 2010-03-25
forum: Programming Talk
---

### Post by cudjoe on 2010-03-25
I have a group (QGraphicsItemGroup) with 2 ellipses.

[LIST=1]
[*]I select my group.
[*]I hide one of the 2 ellipses. .
[*]The group loose its selection
[/LIST]

And I have no way to distinguish this from a user de/selection.

Here is the demo :

```

#!/usr/bin/python
import sys, thread, time

from PyQt4.QtCore import *
from PyQt4.QtGui import *

class GroupItem(QGraphicsItemGroup):
    """
    Nothing special here.
    """
    def __init__(self, pos):
    	QGraphicsItemGroup.__init__(self)
	self.setFlag(QGraphicsItem.ItemIsSelectable, True)
	
	main = QGraphicsEllipseItem()
	main.setRect(pos.x(), pos.y(), 60, 60)
	self.addToGroup(main)
	
	self.small = QGraphicsEllipseItem()
	self.small.setRect(pos.x()-15, pos.y()+15, 30, 30)
	self.addToGroup(self.small)
    

class DiagramScene(QGraphicsScene):
    """
    See toggle()
    """
    def __init__(self, *args):
        QGraphicsScene.__init__(self, *args)
        self.item = GroupItem(QPointF(20,20))
        self.addItem(self.item)
        self.addItem(QGraphicsTextItem("setVisible() on group's items toggles selected state !"))

    def toggle(self):
    	# Force selection :
    	self.item.setSelected(True)
    	# Hide subpart of group
    	self.item.small.setVisible(not self.item.small.isVisible())
    	# Item is now deselected.
    	

class MainWindow(QMainWindow):
    def __init__(self, *args):
        QMainWindow.__init__(self, *args)
        self.scene = DiagramScene()
        self.view = QGraphicsView(self.scene)
        self.view.setRenderHint(QPainter.Antialiasing)
        self.setCentralWidget(self.view)
        self.th = thread.start_new(self.toggle, ())
        
    def toggle(self):
    	while True:
            self.scene.toggle()
	    time.sleep(1)

def main(args):
    app = QApplication(args)
    mainWindow = MainWindow()
    mainWindow.setGeometry(100, 100, 400, 100)
    mainWindow.show()

    # Qt Main loop
    sys.exit(app.exec_())


if __name__ == "__main__":
    main(sys.argv)

```

---

