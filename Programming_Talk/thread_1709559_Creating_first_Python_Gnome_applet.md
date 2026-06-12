---
title: "Creating first Python Gnome applet"
date: 2011-03-18
forum: Programming Talk
---

### Post by gamblor01 on 2011-03-18
Hi all,

I want to create a simple Gnome applet that allows me to control my Tomcat server on my machine.  NOTE: I am VERY new to Python and know almost nothing about it!!

Right now I just have gnome-terminal open and run the startup.sh (actually, I use debug.sh with jpda so I can connect via Eclipse and step through the Java code), shutdown.sh, and a restart.sh script I wrote.  Just for fun I thought it would be great to get this working as a Gnome applet.  I started with this thread:

[http://ubuntuforums.org/showthread.php?t=496185](http://ubuntuforums.org/showthread.php?t=496185)


That along with the example file in /usr/share/doc/python-gnomeappet/examples have helped me get things almost working.  The files are below but basically the startup and restart functions are not working (well actually restart is halfway working).  What does work is the shutdown command and the first half of the restart.  I think what is happening is that a process is getting spawned to perform each task, but when the script finishes, so does the child process.  So for example, when I click to start the server, it fires up bash, runs the debug script (which starts Tomcat) and then the process ends (and thus, so does Tomcat).

The shutdown command works because it basically just kills the PID (which of course stays in effect after this child process finishes).

So I have two questions:

1. How do I correct this so that the processes do not get killed after running (e.g. I need the Tomcat server to continue running!).

2. If you add this to the gnome panel, any idea why it cannot be right-clicked and removed?  I have just had to find the PID and kill it!



Here are the files that I am using (note that to run on another machine you will need to modify the values listed in [COLOR="Red"]red[/COLOR] below).  For example, you won't have the icons (and won't have them in the same path either), and my tomcat-*.sh scripts are symbolic links to debug.sh/shutdown.sh/restart.sh scripts that exist in my tomcat/bin directory.


GNOME_TomcatApplet.server
(place in /usr/lib/bonobo/servers)
```

<oaf_info>
  <oaf_server ubuntu-gettext-domain="tomcat-applet" iid="OAFIID:GNOME_TomcatApplet_Factory" type="exe"
              location="tomcatapplet.py">

    <oaf_attribute name="repo_ids" type="stringv">
      <item value="IDL:Bonobo/GenericFactory:1.0"/>
      <item value="IDL:Bonobo/Unknown:1.0"/>
    </oaf_attribute>
    <oaf_attribute name="name" type="string" value="Tomcat Applet Factory"/>
    <oaf_attribute name="description" type="string" value="Tomcat Applet Factory"/>
    <oaf_attribute name="bonobo:environment" type="stringv">
       <item value="DBUS_SESSION_BUS_ADDRESS"/>
    </oaf_attribute>
  </oaf_server>

  <oaf_server ubuntu-gettext-domain="tomcat-applet" iid="OAFIID:GNOME_TomcatApplet" type="factory"
              location="OAFIID:GNOME_TomcatApplet_Factory">

    <oaf_attribute name="repo_ids" type="stringv">
      <item value="IDL:GNOME/Vertigo/PanelAppletShell:1.0"/>
      <item value="IDL:Bonobo/Control:1.0"/>
      <item value="IDL:Bonobo/Unknown:1.0"/>
    </oaf_attribute>
    <oaf_attribute name="name" type="string" value="Tomcat Applet"/>
    <oaf_attribute name="description" type="string" value="Start and stop the Tomcat server"/>
    <oaf_attribute name="panel:icon" type="string" value="[COLOR="red"]/custom-icons/tomcat-applet.png[/COLOR]"/>
  </oaf_server>
</oaf_info>

```


tomcatapplet.py
(place in any directory in $PATH):
```

#!/usr/bin/env python
import pygtk
import sys
import os
pygtk.require('2.0')

import gtk
import gnomeapplet
import gobject

def factory(applet, iid):
	image = gtk.Image()
	image.set_from_file("[COLOR="red"]/custom-icons/tomcat-applet24.png[/COLOR]")
	button = gtk.Button()
	button.set_relief(gtk.RELIEF_NONE)
	button.set_image(image)
	button.connect("button_press_event", showMenu, applet)
	applet.add(button)
	applet.show_all()
	return True

def createAndShowMenu(event, menuItems): 
    menu = gtk.Menu() 
    for menuItem in menuItems: 
        item = gtk.MenuItem(menuItem[0], True) 
        item.show() 
        item.connect( "activate", *menuItem[1:]) 
        menu.add(item) 
    menu.popup( None, None, None, event.button, event.time ) 

def doFirst(widget, additionalParameter): 
	print "Starting Tomcat"
	os.system("[COLOR="red"]tomcat-debug.sh[/COLOR]") 
def doSecond(widget): 
	print "Stopping Tomcat"
	os.system("[COLOR="red"]tomcat-shutdown.sh[/COLOR]") 
def doThird(widget): 
	print "Retarting Tomcat"
	os.system("[COLOR="red"]tomcat-restart.sh[/COLOR]") 

def showMenu(widget, event, applet): 
    if event.button == 1: 
        menu = [ 
            ["Start Tomcat", doFirst], 
            ["Stop Tomcat", doSecond], 
            ["Restart Tomcat", doThird]] 
        createAndShowMenu(event, menu) 
        widget.emit_stop_by_name("button_press_event") 

def showAboutDialog(*arguments, **keywords):
	pass

if len(sys.argv) == 2:
	if sys.argv[1] == "run-in-window":
		mainWindow = gtk.Window(gtk.WINDOW_TOPLEVEL)
		mainWindow.set_title("Tomcat applet")
		mainWindow.connect("destroy", gtk.main_quit)
		applet = gnomeapplet.Applet()
		factory(applet, None)
		applet.reparent(mainWindow)
		mainWindow.show_all()
		gtk.main()
		sys.exit()

if __name__ == '__main__':
	print "Starting factory"
	gnomeapplet.bonobo_factory("OAFIID:GNOME_TomcatApplet_Factory", gnomeapplet.Applet.__gtype__, "Tomcat server applet", "1.0", factory)

```




Edit:  I forgot to mention...you can actually add this to your panel or just run it from a terminal using

```

./tomcatapplet.py run-in-window

```

The run-in-window option is easier since it's impossible to remove the applet without finding the PID and killing it.

---

### Post by LemursDontExist on 2011-03-18
Check out the [subprocess]("http://docs.python.org/library/subprocess.html") module.  os.system is pretty basic, and prone to problems.  subprocess.Popen should allow you to spawn a process which won't terminate when the python process terminates (assuming that was your goal).

As for the right click, I really don't know much about about gnome panel applets, but I would guess that by default panel applets don't have a right click menu by default, so maybe you need to define that yourself?

---

### Post by gamblor01 on 2011-03-21
> **LemursDontExist said:**
> Check out the [subprocess]("http://docs.python.org/library/subprocess.html") module.  os.system is pretty basic, and prone to problems.  subprocess.Popen should allow you to spawn a process which won't terminate when the python process terminates (assuming that was your goal).

As for the right click, I really don't know much about about gnome panel applets, but I would guess that by default panel applets don't have a right click menu by default, so maybe you need to define that yourself?

Awesome thank you!!!  I basically just added a blank right-click menu and now I have the option to move the applet, lock it, or remove it!  The subprocess stuff works perfectly as well.  In fact, here is the newly updated script (complete with icon changes when you stop or start the server):

```

#!/usr/bin/env python
import pygtk
import sys
import os
import subprocess
pygtk.require('2.0')

import gtk
import gnomeapplet
import gobject

my_button = 0
my_size = 0

def factory(applet, iid):

	# get the icon and show the button
	size = applet.get_size() - 2
	pixbuf = gtk.gdk.pixbuf_new_from_file_at_size("/custom-icons/tomcat-applet24.png", size, size)
	image = gtk.Image()
	image.set_from_pixbuf(pixbuf)
	button = gtk.Button()
	button.set_relief(gtk.RELIEF_NONE)
	button.set_image(image)
	button.connect("button_press_event", showMenu, applet)

	# save the button and size away for later image manipulation
	global my_button
	global my_size
	my_button = button
	my_size = size

	applet.add(button)
	applet.show_all()
	return True

def createAndShowMenu(event, menuItems): 
    menu = gtk.Menu() 
    for menuItem in menuItems: 
        item = gtk.MenuItem(menuItem[0], True) 
        item.show() 
        item.connect( "activate", *menuItem[1:]) 
        menu.add(item) 
    menu.popup( None, None, None, event.button, event.time )

def right_menu(applet):
	propxml="""
			<popup name="button3">
			</popup>"""
	verbs = [("About", showAboutDialog)]
	applet.setup_menu(propxml, verbs, None)

def doFirst(widget): 
	print "Starting Tomcat"
	subprocess.Popen("tomcat-debug.sh") 

	# change the icon to the started icon
	pixbuf = gtk.gdk.pixbuf_new_from_file_at_size("/custom-icons/tomcat-applet-start.png", my_size, my_size)
	image = gtk.Image()
	image.set_from_pixbuf(pixbuf)
	my_button.set_image(image)
def doSecond(widget): 
	print "Stopping Tomcat"
	subprocess.Popen("tomcat-shutdown.sh") 

	# change the icon to the stopped icon
	pixbuf = gtk.gdk.pixbuf_new_from_file_at_size("/custom-icons/tomcat-applet24.png", my_size, my_size)
	image = gtk.Image()
	image.set_from_pixbuf(pixbuf)
	my_button.set_image(image)
def doThird(widget): 
	print "Retarting Tomcat"
	subprocess.Popen("tomcat-restart.sh") 

	# change the icon to the started icon
	pixbuf = gtk.gdk.pixbuf_new_from_file_at_size("/custom-icons/tomcat-applet-start.png", my_size, my_size)
	image = gtk.Image()
	image.set_from_pixbuf(pixbuf)
	my_button.set_image(image)

def showMenu(widget, event, applet): 
    if event.button == 1: 
        menu = [ 
            ["Start Tomcat", doFirst], 
            ["Stop Tomcat", doSecond], 
            ["Restart Tomcat", doThird]] 
        createAndShowMenu(event, menu) 
        widget.emit_stop_by_name("button_press_event") 
    elif event.type == gtk.gdk.BUTTON_PRESS and event.button == 3:
	widget.emit_stop_by_name("button_press_event")
	right_menu(applet)

def showAboutDialog(*arguments, **keywords):
	pass

if len(sys.argv) == 2:
	if sys.argv[1] == "run-in-window":
		mainWindow = gtk.Window(gtk.WINDOW_TOPLEVEL)
		mainWindow.set_title("Tomcat applet")
		mainWindow.connect("destroy", gtk.main_quit)
		applet = gnomeapplet.Applet()
		factory(applet, None)
		applet.reparent(mainWindow)
		mainWindow.show_all()
		gtk.main()
		sys.exit()

if __name__ == '__main__':
	print "Starting factory"
	gnomeapplet.bonobo_factory("OAFIID:GNOME_TomcatApplet_Factory", gnomeapplet.Applet.__gtype__, "Tomcat server applet", "1.0", factory)

```


Again, since I'm a python novice and this code is just for my own personal use I didn't write it very elegantly.  I realize I probably shouldn't hard-code things, and variable/function names aren't very good.  Oh well -- it works!

My last question now is why my icon shows up with highlighting underneath it.  None of the other applet icons do that.  I thought that perhaps it was because the icon was too large so I added in the pixbuf stuff to resize it but that didn't change anything.  See the attached picture -- it shows my applet running next to some of the default applets and illustrates the point.

---

