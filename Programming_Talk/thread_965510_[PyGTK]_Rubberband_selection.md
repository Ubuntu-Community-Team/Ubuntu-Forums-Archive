---
title: "[PyGTK] Rubberband selection"
date: 2008-10-31
forum: Programming Talk
---

### Post by Scyron on 2008-10-31
Part of an application I'm writing uses a click-drag system to select parts of an image. I have the underlying idea:

```

def __init__ (self):
	self.image = gtk.Image()
	self.imagebox = gtk.EventBox()
	self.imagebox.add(self.image)
	self.imagebox.set_events(gtk.gdk.BUTTON_PRESS_MASK | gtk.gdk.BUTTON_RELEASE_MASK)
	self.imagebox.connect("button_press_event", self.drag_start)
	self.imagebox.connect("button_release_event", self.drag_end)

def drag_start(self, widget, event):
	print "Drag start:",event.x,event.y
	self.drag_start = [event.x, event.y]

def drag_end(self, widget, event):
	print "Drag end:",event.x,event.y
	self.drag_end = [event.x, event.y]
	self.fetch_select_area(self.drag_start, self.drag_end)

```

But I'm at loss at how to graphically represent this. Are there any tools available to implement the selection rectangles like the Nautilus Rubberband? Thanks.

---

### Post by loell on 2008-10-31
maybe you're looking for,

[http://www.pygtk.org/docs/pygtk/class-gdkdragcontext.html#method-gdkdragcontext--set-icon-pixbuf]("http://www.pygtk.org/docs/pygtk/class-gdkdragcontext.html#method-gdkdragcontext--set-icon-pixbuf")

---

### Post by Scyron on 2008-10-31
Thank you for the response. I know about DragContext, but unless I'm reading the documentation incorrectly it's for drag and drop (specifically, between desktop and application).

---

### Post by unutbu on 2008-10-31
Sycron, I don't know enough PyGTK to help you directly, but have you looked at 
/usr/lib/pygtk/2.0/demos/dnd.py ? (part of the python-gtk2 package)

Maybe if you can figure out what all those drag events mean, you can tease out the part you want...

---

### Post by Scyron on 2008-12-11
Okay, GTK doesn't seem to have any click-and-drag selection tools outside of premade widgets. I ended up using a canvas and drawing what I needed. Here's an implementation to tweak with if anyone has the same problem and comes searching.

```

#!/usr/bin/env python
import gtk
import os
import gnomecanvas

class ImageWindow:
	def __init__(self):
		# Create window
		self.window = gtk.Window()
		self.window.set_title('Rubberband Selection')
		self.window.connect('destroy', gtk.main_quit)

		# Create 350x350 antialised drawing canvas
		self.canvas = gnomecanvas.Canvas(aa=True)
		self.canvas.set_size_request(350, 350)
		self.canvas.set_scroll_region(0, 0, 350, 350)
		if os.path.exists("foo.png"):
			self.set_canvas_background("foo.png")

		# Put it together
		self.window.add(self.canvas)
		self.window.set_resizable(False)
		self.window.show_all()

		# Event Handling
		self.canvas.connect("event", self.canvas_event)
		self.dragging = False

	# Set and image in the background
	def set_canvas_background(self, location):
		pixbuf = gtk.gdk.pixbuf_new_from_file(location)
		itemType = gnomecanvas.CanvasPixbuf
		self.background = self.canvas.root().add(itemType, x=0, y=0, pixbuf=pixbuf)

	# Returns a referance to a rectangle drawn on the canvas
	def get_rect(self, x, y):
		itemType = gnomecanvas.CanvasRect
		rect = self.canvas.root().add(itemType, x1=x, y1=y, x2=x, y2=y, #0x0 dimensions at first
						fill_color_rgba=0xFFCC3355, outline_color_rgba=0xFFEECC99,
						width_units=1.0)
		return rect

	# Event handling
	def canvas_event(self, widget, event):
		# Creates a rubberband on left-click
		if (event.type == gtk.gdk.BUTTON_PRESS):
			if (event.button == 1):
				self.dragging = True
				self.startx = event.x
				self.starty = event.y
				self.rubberband = self.get_rect(self.startx, self.starty)

		# Updates the rubberband size while a mouse drags
		if (event.type == gtk.gdk.MOTION_NOTIFY) and (self.dragging):
			self.rubberband.set(x2=event.x, y2=event.y)

		# Destroys the rubberband and sends selection data to the relevant method
		if (event.type == gtk.gdk.BUTTON_RELEASE) and (self.dragging):
			if (event.button == 1):
				self.dragging = False
				self.endx = event.x
				self.endy = event.y
				self.rubberband.set(x2=self.endx, y2=self.endy)
				self.rubberband.destroy()
				self.select([self.startx, self.starty, self.endx, self.endy])

	# Replace this with whatever you want to do
	def select(self, selection):
		print "User selected : ", selection

if __name__ == '__main__':
    imageWindow = ImageWindow()
    gtk.main()

```

---

