---
title: "Python Draw frame..."
date: 2011-09-06
forum: Programming Talk
---

### Post by Drakx on 2011-09-06
Hi

I'm wanting to draw a frame around a given area like shown in this picture from xvidcap as you see the outer red frame is the capture area in this case.

[IMG]http://xvidcap.sourceforge.net/instruct-Screenshot.jpg[/IMG]

Whats the easiest way of doing this within python? I would like to be able to select a 300x300 area for example and have python show a frame thats displayed to the user (in this case me).

Thanks.

---

### Post by Drakx on 2011-09-06
Ok
So I've done a little messing around as you can see from this example I've been able to draw a border around one button but I cannot work out how to get it so that when I click "draw frame" button it then draws the frame around the close button. I would also like it to draw a frame around another window i select hence the os.system("xwininfo -frame") 

```

import pygtk, os
pygtk.require('2.0')
import gtk

class messingWithFrames:
	def __init__(self):
		#Set window
		self.frmMain = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.frmMain.set_position(gtk.WIN_POS_CENTER)
		self.frmMain.set_size_request(200, 100)
		self.frmMain.set_title("Test Draw Frame")
		self.frmMain.connect("destroy", self.closeApp)
		
		# Add some button's
		self.btnClose = gtk.Button("Close")
		self.btnClose.connect("clicked", self.closeApp)
		
		self.btnFrame = gtk.Button("Draw Frame")
		self.btnFrame.connect("clicked", self.drawFrame)
		
		# Frame
		self.frame = gtk.Frame()
		self.frame.set_border_width(2)
		self.frame.modify_bg(gtk.STATE_NORMAL, gtk.gdk.Color(65535))
		self.frame.add(self.btnClose)
		
		# Container for buttons and stuff
		self.vbox = gtk.VBox()
		self.vbox.pack_start(self.btnClose)
		self.vbox.pack_start(self.btnFrame)
		self.vbox.pack_start(self.frame)
		# Display Window
		self.frmMain.add(self.vbox)
		#self.frmMain.add(self.frame)
		self.frmMain.show_all()
	
	def closeApp(self, widget, data = None):
		print "Application Closed."
		gtk.main_quit()
	
	def drawFrame(self, widget):
		os.system("xwininfo -frame")
		
	def main(self):
		gtk.main()

if __name__ == "__main__":
	base = messingWithFrames()
	base.main()

```

Thanks

---

