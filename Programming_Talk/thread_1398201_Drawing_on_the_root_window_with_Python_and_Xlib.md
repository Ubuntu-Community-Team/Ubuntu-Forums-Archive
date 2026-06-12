---
title: "Drawing on the root_window with Python and Xlib"
date: 2010-02-04
forum: Programming Talk
---

### Post by moma on 2010-02-04
Hello, 

Got a grazy idea to port my [screenshot utility...]("http://code.google.com/p/gscreendump/") from C to Python. So I started to experiment with Python + Xlib. The [original code...]("http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_capture_area.c") is written in C and Xlib + GTK/GDK libraries. 

A simple start.
The following Python+Xlib code should draw a line on the root window (on the desktop surface), but it does not work. 

1)Can you help me?  If you know how to do this with pure GTK/GDK, that's OK too.

2) What is you favourite Python editor? I have started to use Eclipse with Pydev-plugin but its auto-completion (code completion feature) is not very good.

Being new to Python + PyGTK, am totally dependent on a good editor and auto-completion.


[PHP]#!/usr/bin/python

import sys
import os

# http://python-xlib.sourceforge.net/doc/html/index.html

sys.path.insert(1, os.path.join(sys.path[0], '..'))

from Xlib import X, display, Xutil

class DrawTest:
    def __init__(self, display):
    	# X display
		self.d = display

        # Screen
		self.screen = self.d.screen()

		# Draw on the root window (desktop surface)
		self.window = self.screen.root


		self.window.grab_pointer(1, X.PointerMotionMask|X.ButtonReleaseMask|X.ButtonPressMask, 
                X.GrabModeAsync, X.GrabModeAsync, X.NONE, X.NONE, X.CurrentTime)		

		# != GrabSuccess))
		self.window.grab_keyboard(1, X.GrabModeAsync, X.GrabModeAsync, X.CurrentTime)

		self.gc = self.window.create_gc(
			foreground = self.screen.black_pixel,
			background = self.screen.white_pixel,
			line_width = 2,
			line_style = X.LineSolid,
			fill_style = X.FillOpaqueStippled,
			fill_rule  = X.WindingRule,
			cap_style  = X.CapButt,
			join_style = X.JoinMiter,
			function = X.GXor,
			)

		# self.window.map()

		print "Press any key or right-mouse button to terminate."

		done = False
		while done == False:
			e = self.d.next_event()
			
			# Window has been destroyed, quit
			if e.type == X.DestroyNotify:
			    sys.exit(0)
			
			elif e.type == X.Expose:
				pass

			# Mouse button press  
			elif e.type == X.ButtonPress:
				# Left mouse button?
				if e.detail == 1:
					# Draw a line from (0,0) to (e.root_x, e.root_y)
					self.window.line(self.gc, 0, 0, e.root_x, e.root_y)
					print e.root_x, e.root_y
			
				# Right mouse button?
				elif e.detail == 3:					
					done = True
			
						
			# Mouse button release  
			elif e.type == X.ButtonRelease:
				pass
			
			# Mouse movement
			elif e.type == X.MotionNotify:
				# print e.root_x, e.root_y
			   	pass
			
			# Keyboard key
			elif e.type == X.KeyPress:
				done = True
			
	# end...

if __name__ == '__main__':
    DrawTest(display.Display())[/PHP]

I need this to draw a GXor'ed rubber line (rectangle) on the screen.

---

### Post by moma on 2010-02-05
Re-hello,

I got an answer from Python-xlib-users' news group.
[http://sourceforge.net/mailarchive/message.php?msg_name=383f32ef1002041307y140ec2eco559e055ae6c96e59@mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_name=383f32ef1002041307y140ec2eco559e055ae6c96e59@mail.gmail.com)

It works if I set the foreground color and drawing function right.
The function should be X.GXxor (X.GXor is something different).

This is right:[PHP]
		colormap = self.screen.default_colormap

		# (r,g,b) blue = (0,0,65535)
		color = colormap.alloc_color(0, 0, 65535)
		# Xor it because we'll draw with X.GXxor function 
		xor_color = color.pixel ^ 0xffffff 

		print hex(color.pixel), hex(xor_color) 

		self.gc = self.window.create_gc(
			line_width = 4,
			line_style = X.LineSolid,
			fill_style = X.FillOpaqueStippled,
			fill_rule  = X.WindingRule,
			cap_style  = X.CapButt,
			join_style = X.JoinMiter,
			foreground = xor_color,
			background = self.screen.black_pixel,
			function = X.GXxor, 
			graphics_exposures = False,
			subwindow_mode = X.IncludeInferiors,
			)[/PHP]

---

