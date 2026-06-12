---
title: "PyGTK Widget &quot;Layering&quot; Problem"
date: 2008-09-24
forum: Programming Talk
---

### Post by apathor on 2008-09-24
Hullo Fellow Linux Developer Peoples! 
Does anyone know if there is a way to define the layer that a widget appears on in PyGTK? By that I mean controlling the order in which the GTK objects are drawn. Here is the code so far:

```

import gtk

class DragImage( gtk.Image ):
	def __init__(self, image, layout):
		gtk.Image.__init__(self)
		self.drag = False
		self.drag_x = 0
		self.drag_y = 0
		self.layout = layout
		self.x = 0
		self.y = 0
		self.set_from_file( image )	
		self.event_box =  gtk.EventBox()
		self.event_box.set_visible_window( False )
		self.event_box.add( self )
		self.event_box.add_events( gtk.gdk.POINTER_MOTION_MASK | gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK )
		self.event_box.connect("button-press-event", self.click)
		self.event_box.connect("button-release-event", self.release)
		self.event_box.connect("motion-notify-event", self.mousemove)
		self.layout.put( self.event_box, 0, 0 )
		print self.layout.list_child_properties()
	def click(self, widget, event):
		self.drag =  True
		self.drag_x =  event.x
		self.drag_y =  event.y
	def release(self, widget, event):
		self.drag =  False
	def mousemove(self, widget, event):
		if self.drag:
			self.layout.move( self.event_box, self.x+int(event.x-self.drag_x), self.y+int(event.y-self.drag_y))
			self.x, self.y =  self.layout.child_get( self.event_box, 'x', 'y' )
class move_test( object ):
	def __init__( self ):
		win =  gtk.Window( gtk.WINDOW_TOPLEVEL )
		layout =  gtk.Layout()
		img1 = DragImage( 'img.png', layout)
		img2 = DragImage( 'img.png', layout)
		win.add(layout)
		win.show_all()
move_test()
gtk.main()

```

This produces a window with 2 generic images (called DragImages that are pretty much just EventBoxes + Images) in it that can be dragged around to any position. Is there an easy way to change the layer of these images so that the most recently dragged is on top of the others?  

Any input would be appreciated.
-Apathor

---

