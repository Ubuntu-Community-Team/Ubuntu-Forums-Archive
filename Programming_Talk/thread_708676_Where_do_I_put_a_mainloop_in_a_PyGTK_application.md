---
title: "Where do I put a mainloop in a PyGTK application?"
date: 2008-02-26
forum: Programming Talk
---

### Post by solarwind on 2008-02-26
Hey all, I'm making a simple application which uses PyGTK and sits in the system tray and keeps checking for emails. However, I don't know where to put the check loop in where it keeps checking for emails. Can anyone help?

---

### Post by Jussi Kukkonen on 2008-02-26
Normally you don't write the loop yourself. You use gtk or glib mainloop and set a timeout that starts your check_email function every X minutes.

pseudo_code (I'm not familiar with pygtk so this is the best you'll get):
```

function check_email ()
{
    /*do important stuff here*/
}

main ()
{
    time_out_add (600 seconds, check_email)
    main_loop_run ()
}
```

---

### Post by nick_h on 2008-02-26
Yes, that's the way to do it.  In Python it will look something like:
```
gobject.timeout_add(self.timeout_interval, self.timeout_callback, self)
```
Then the callback must return True if you want it to continue:
```
def timeout_callback(self, event):
...
return True
```

---

### Post by solarwind on 2008-02-26
> **nick_h said:**
> Yes, that's the way to do it.  In Python it will look something like:
```
gobject.timeout_add(self.timeout_interval, self.timeout_callback, self)
```
Then the callback must return True if you want it to continue:
```
def timeout_callback(self, event):
...
return True
```

Wow, thanks a lot guys! This really helped!

---

### Post by solarwind on 2008-02-26
Hmmm, I can't find the docs for this on the PyGTK website, can someone point me in the right direction? I need to see if the timeout function takes an argument in seconds or milliseconds...

---

### Post by solarwind on 2008-02-26
Also, the timeout function seems to be calling my function only once... Here's my code:

```
import pygtk
pygtk.require('2.0')
import gtk
import time
import os
import pytrayicon
import sys
import warnings
import gobject

class ggmail:
	def __init__(self):
		# Creates the main window
		self.window = gtk.Window(gtk.WINDOW_POPUP)
		self.window.set_title("ggmail")
		self.window.set_resizable(1)
		self.window.set_decorated(0)
		self.window.set_keep_above(1)
		self.window.stick()
		self.window.hide()
		# Create the tray icon object
		self.tray = pytrayicon.TrayIcon("ggmail");
		self.eventbox = gtk.EventBox()
		self.tray.add(self.eventbox)
		self.eventbox.connect("button_press_event", self.ButtonPress)
		
		# Set the image for the tray icon
		self.imageicon = gtk.Image()
		self.imageicon.set_from_file("/home/vg/Projects/ggmail/icon.png")

		self.eventbox.add(self.imageicon)
		# Show the tray icon
		self.tray.show_all()

		self.maintimer = gobject.timeout_add(1000, self.Test)	

	def ButtonPress(self, signal, event):
		if event.type == gtk.gdk.BUTTON_PRESS and event.button == 1:
			self.CheckMail()		

		if event.type == gtk.gdk.BUTTON_PRESS and event.button == 3:
			self.LaunchBrowser()

	def Test(self):
		print "Test"


	def CheckMail(self):
		self.imageicon.set_from_file("/home/vg/Projects/ggmail/icon3.png")
		time.sleep(1)
		self.imageicon.set_from_file("/home/vg/Projects/ggmail/icon2.png")
		time.sleep(1)

	def LaunchBrowser(self):
		pass


	def main(self):
		gtk.main()

if __name__ == "__main__":
	warnings.filterwarnings(action = "ignore", category = DeprecationWarning)
	gmailnotifier = ggmail()
	gmailnotifier.main()
```

---

### Post by nick_h on 2008-02-26
The interval is in milliseconds.

You need to return True for the callback to continue.  If you return False it will not be called again.  I suggest you actually include the statement "return True".

---

### Post by solarwind on 2008-02-26
> **nick_h said:**
> The interval is in milliseconds.

You need to return True for the callback to continue.  If you return False it will not be called again.  I suggest you actually include the statement "return True".

Thanks! It works perfectly now! The thing is, this whole GTK/GOBJECT thing is new to me. Are there any tutorials or good references for PyGTK so I don't have to bother you guys?

---

### Post by nick_h on 2008-02-26
The [PyGTK](http://www.pygtk.org/) site has a good tutorial and reference.
Also have a look at [Gnome applets with Python](http://www.pygtk.org/articles/applets_arturogf/).

For the timeout functionality read [here](http://www.pygtk.org/docs/pygobject/gobject-functions.html#function-gobject--timeout-add).

---

### Post by solarwind on 2008-02-26
> **nick_h said:**
> The [PyGTK](http://www.pygtk.org/) site has a good tutorial and reference.
Also have a look at [Gnome applets with Python](http://www.pygtk.org/articles/applets_arturogf/).

For the timeout functionality read [here](http://www.pygtk.org/docs/pygobject/gobject-functions.html#function-gobject--timeout-add).

Thanks. I was looking at the PyGTK reference earlier but was unable to find out why my program wasn't working. It's those little things like "return True" that cause a lot of trouble. Where do you learn this stuff?

As for the second link, it's very old and was one of the first things I was looking at. That's why I'm specifically not making it a Gnome applet. It's just a PyGTK application that can minimize to the tray (I've already got that part handled).

Thanks again!

---

### Post by nick_h on 2008-02-26
> Where do you learn this stuff?
Just by reading the available documentation and more importantly actually writing an application.

> As for the second link, it's very old and was one of the first things I was looking at. That's why I'm specifically not making it a Gnome applet. It's just a PyGTK application that can minimize to the tray
I just thought it might be the sort of thing that would be good as an applet.  I've written a small test applet following the guide in the link.  Although the guide is old it still works.

---

