---
title: "Python gtkmozembed - new-window signal"
date: 2011-11-25
forum: Programming Talk
---

### Post by Yuzem on 2011-11-25
Hi, I have a very simple browser coded in python and gtkmozembed. I want to open a new window when the user clicks on a link that opens a new window. I can catch the new-window signal and open the window but I don't know how to get the url from the clicked link:

Relevant code:
```
def new_window(self,retval,chromemask):
	gtk_new_window()

browser.connect("new-window", new_window)
```

Full code:
```
#!/usr/bin/env python

import os
import gtk
import gtkmozembed as moz

env = os.environ
winWidth = int(env['winWidth'])
winHeight = int(env['winHeight'])
url = env['url']

profileFolder = '/tmp'
profileName = 'figuritas.moz.'+env['USER']

#~ import sys
#~ sys.exit()

class FullscreenToggler(object):

    def __init__(self, window, keysym=gtk.keysyms.F11):
        self.window = window
        self.keysym = keysym
        self.window_is_fullscreen = False
        self.window.connect_object('window-state-event',
                                   FullscreenToggler.on_window_state_change,
                                   self)

    def on_window_state_change(self, event):
        self.window_is_fullscreen = bool(
            gtk.gdk.WINDOW_STATE_FULLSCREEN & event.new_window_state)

    def toggle(self, event):
        if event.keyval == self.keysym:
            if self.window_is_fullscreen:
                self.window.unfullscreen()
            else:
                self.window.fullscreen()


def get_size(widget, event):
	global Width
	global Height
	Width = event.width
	Height = event.height

def CloseWindow(widget):
    """Close the window and exit the app"""
#    gtk.destroy()
    gtk.main_quit() # Close the app fully

#~ def on_net_stop(self):
	 #~ print("got on_net_stop")

def new_window(self,retval,chromemask):
	gtk_new_window()

def gtk_new_window():
	# Set-up the main window which we're going to embed the widget into
	win = gtk.Window() # Create a new GTK window called 'win'

	win.set_title("Figuritas")
	win.set_icon_from_file('/usr/share/pixmaps/figuritas.png')
	win.set_position(gtk.WIN_POS_CENTER)

	win.connect("configure-event", get_size)
	win.connect("destroy", CloseWindow) # Connect the 'destroy' event to the 'CloseWindow' function, so that the app will quit properly when we press the close button

	# Create the browser widget
	moz.set_profile_path(profileFolder, profileName) # Set a temporary Mozilla profile (works around some bug)
	browser = moz.MozEmbed() # Create the browser widget

	#browser.connect("net-stop", on_net_stop)
	browser.connect("new-window", new_window)


	# Set-up the browser widget before we display it
	win.add(browser)
	browser.load_url(url)
	browser.show() # Try to show the browser widget before we show the window, so that the window appears at the correct size (600x400)

	win.set_default_size(winWidth,winHeight)
	toggler = FullscreenToggler(win)
	win.connect_object('key-press-event', FullscreenToggler.toggle, toggler)

	win.show() # Show the window

gtk_new_window()

gtk.main() # Enter the 'GTK mainloop', so that the GTK app starts to run
print('Width='+str(Width)+' Height='+str(Height))

```

Thanks in advance!

---

### Post by crdlb on 2011-11-25
Have you considered WebkitGtk? It is used by Epiphany and Midori, and is replacing other HTML engines throughout GNOME.

It can be used from python with the static python-webkit bindings for GTK2, or with the gobject-introspection bindings for GTK3 (from gi.repository import WebKit)

There's probably a way to do what you want with GtkMozEmbed, but I don't know how, and it's basically abandoned by Mozilla at this point.

---

### Post by Yuzem on 2011-11-25
> **crdlb said:**
> Have you considered WebkitGtk?
Yes I have, the only reason I can remember for not using Webkit is the lack of support for [css system colors]("http://www.iangraham.org/books/xhtml1/appd/update-23feb2000.html"). I really need that since I am coding an application that should look like gtk and it isn't easy to figure out how to emulate the gtk functions like shade() or darker() used in gtk themes. I get similar colors but not the same.

---

