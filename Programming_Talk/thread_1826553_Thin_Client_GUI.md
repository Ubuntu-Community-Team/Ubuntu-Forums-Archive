---
title: "Thin Client GUI?"
date: 2011-08-16
forum: Programming Talk
---

### Post by kevin11951 on 2011-08-16
Environment:

* Python 2.6.5
* (Ubuntu 10.04) Linux only
* Tk preferred

I have been writing scripts for my sysadmin job for a while now, but I have no experience with Python GUI development.

Having said that, here is what I need to make:


**Mockup:**

[IMG]https://lh3.googleusercontent.com/-QjHycO4jD6s/TkraWQ8_f6I/AAAAAAAAAVc/GodsShlDK28/s800/thinclientgui.png[/IMG]

It also needs to run in full screen...  (I already figured out how to do that in "Tk")

Specs:

When someone presses login, do the following:

```
/usr/local/bin/rdesktop -u <username field> -p <password field> [other rdesktop options] [server IP]
```

When someone presses "Restart Thin Client":

```
/sbin/reboot
```

When someone presses "Shutdown Thin Client":

```
/sbin/halt
```

It would be nice if it had very few dependencies (Use of "Tk" preferred).


**Where do I even begin?**

---

### Post by DangerOnTheRanger on 2011-08-16
I personally think the Python Wiki page on Tkinter is the best place to start: [http://wiki.python.org/moin/TkInter](http://wiki.python.org/moin/TkInter)

---

### Post by cgroza on 2011-08-16
Your GUI does not seem to complex. A quick tutorial, about 10 minutes of designing and you should be ready to lay some code.
In this case, the minimum of Tk you must know is widgets you want to use, layout managing and events (or commands, whatever they are called in Tk)

---

### Post by Smart Viking on 2011-08-16
[LEFT]Should not be very hard, seems like Tkinter is awesomely documented, python.org said [this]("http://www.pythonware.com/library/tkinter/introduction/whats-tkinter.htm") is a good place to start. I read the first couple of pages, seems like a great introduction.

(Now I really felt like looking into Tkinter myself :P)
[/LEFT]

---

### Post by kevin11951 on 2011-08-16
Here is what I have so far:

(See Attached Screenshot)

So far, so good...

The only problem is that the widgets are all stuffed in the upper left corner...  How do I get them to look like the mockup?

```
#!/usr/bin/env python
#
#       Copyright 2011 Kevin Soviero <ksoviero@enactpc-workstation>

from subprocess import Popen
from Tkinter import *

class ThinGUI:
	def __init__(self, master):
		frame = Frame(master)
		frame.grid()
		
		sw = master.winfo_screenwidth()
		sh = master.winfo_screenheight()

		master.geometry("%dx%d+0+0" % (sw, sh))
		
		self.user = Label(master, text='Username:')
		self.user.grid(row=0, column=0)
		
		self.userText = Entry(master)
		self.userText.grid(row=0, column=1)
		
		self.passwd = Label(master, text='Password:')
		self.passwd.grid(row=1, column=0)
		
		self.passwdText = Entry(master, show='*')
		self.passwdText.grid(row=1, column=1)
		
		self.login = Button(master, text='Login', command=self.login)
		self.login.grid(row=3, columnspan=2)
		
		self.halt = Button(master, text='Shutdown Thin Client', command=self.halt)
		self.halt.grid(row=4, column=0)
		
		self.reboot = Button(master, text='Restart Thin Client', command=self.reboot)
		self.reboot.grid(row=4, column=1)
	
	def server(self):
		return '10.0.0.203'
		
	def login(self):
		Popen(['/usr/bin/rdesktop', 		# Absolute path to rdesktop
		'-u', self.userText.get(), 			# The "username" entered in the GUI
		'-p', self.passwdText.get(), 			# The "password" entered in the GUI
		'-x', 'm', 							# Disables graphical effects in Windows
		'-z', 								# Compresses the stream
		'-P', 								# Enables bitmap caching
		'-a', '16', 						# Sets color depth to "16"
		'-r', 'sound:local', 				# Enables sound
		'-r', 'disk:Drives=/media/root', 	# Enables local USB drives
		self.server() 						# Server IP address
		])
	
	def halt(self):
		Popen(['/sbin/halt'])
	
	def reboot(self):
		Popen(['/sbin/reboot'])

root = Tk()

app = ThinGUI(root)

root.mainloop()

```

---

### Post by juancarlospaco on 2011-08-16
Check the padding widget setting. like :

self.thing.grid(row=1, column=1, fill=BOTH, expand=1,** pady=50, padx=100**)

if you are interested into colors:

frame = Frame(master, **bg="white", fg="grey"**)

Feel free to contact me if you need help...

---

### Post by cgroza on 2011-08-16
> **juancarlospaco said:**
> Check the padding widget setting. like :

self.thing.grid(row=1, column=1, fill=BOTH, expand=1,** pady=50, padx=100**)


Does Tkinter have the concept of sizers? That would allow the program to keep the same layout indifferently of window size....

---

### Post by kevin11951 on 2011-08-17
So I take it that there is no easy way to make it look just like the mockup?

---

### Post by juancarlospaco on 2011-08-17
> **cgroza said:**
> Does Tkinter have the concept of sizers? That would allow the program to keep the same layout indifferently of window size....

Yes, it have all the widgets and sizers.
 But i dunno if he want to use Sizers...

---

### Post by Smart Viking on 2011-08-17
I ended up making that program with pyGTK, just to practice doing interfaces, take it or leave it, it was fun making for a newb like me. :)

Note that I just put "self" in front of everything, because honestly I don't really understand OOP.

The buttons aren't mapped as you want it, "Restart Thin Client" toggles fullscreen, and the shutdown button calls gtk.main_quit()

```
#!/usr/bin/env python
import gtk, pygtk

class app:

  def __init__(self):
    self.fullscreen = 0

    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    self.window.set_size_request(400, 300)
    self.window.connect("destroy", lambda x: gtk.main_quit())

    self.align = gtk.Alignment()
    self.align.set(0.5,0.5,0,0)
    self.align2 = gtk.Alignment()
    self.align2.set(0.5,0.5,0,0)

    self.mainvbox = gtk.VBox()
    self.vbox = gtk.VBox()
    self.hbox = gtk.HBox()
    self.hbox2 = gtk.HBox()
    self.loginhbox = gtk.HBox()
    self.bottomhbox = gtk.HBox()

    self.label1 = gtk.Label("Username:")
    self.label2 = gtk.Label("Password:")

    self.entry1 = gtk.Entry()
    self.entry2 = gtk.Entry()
 
    self.loginbutton = gtk.Button("Login")
    self.restartbutton = gtk.Button("Restart Thin Client")
    self.shutdownbutton = gtk.Button("Shutdown Thin Client")
    self.restartbutton.connect("clicked", lambda x: self.setfullscreen())
    self.shutdownbutton.connect("clicked", lambda x: gtk.main_quit())
    self.loginbutton.connect("clicked", lambda x: self.login())

    self.hbox.pack_start(self.label1, True,False)
    self.hbox.pack_start(self.entry1, True,False)
    self.hbox2.pack_start(self.label2, True,False)
    self.hbox2.pack_start(self.entry2, True,False)
    self.loginhbox.pack_start(self.loginbutton,True,False)
    self.bottomhbox.pack_start(self.restartbutton,True,False)
    self.bottomhbox.pack_start(self.shutdownbutton,True,False)

    self.hbox.set_border_width(10)
    self.hbox2.set_border_width(10)
    self.label1.set_padding(10,0)
    self.label2.set_padding(10,0)
    self.bottomhbox.set_spacing(30)

    self.vbox.pack_start(self.hbox,True,False)
    self.vbox.pack_start(self.hbox2,True,False)
    self.vbox.pack_start(self.loginhbox,True,False)

    self.align2.add(self.bottomhbox)
    self.align.add(self.vbox)
    self.mainvbox.pack_start(self.align,True,True)
    self.mainvbox.pack_start(self.align2,False,True)
    self.window.add(self.mainvbox)
    self.window.show_all()

  def login(self):
    print "Logging in with the username \""+ self.entry1.get_text()+"\" and the password \""+self.entry2.get_text()+"\"."

  def setfullscreen(self):
    if self.fullscreen:
      self.window.fullscreen()
      self.fullscreen = 0
    else:
      self.window.unfullscreen()      
      self.fullscreen = 1

if __name__ == "__main__":
  application = app()
  gtk.main()
```

EDIT: I changed the code, added some functionality. :)
```

#!/usr/bin/env python
import gtk, pygtk, gobject

class app:

  def __init__(self):
    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    self.window.set_size_request(400, 300)
    self.window.connect("destroy", lambda x: gtk.main_quit())
    self.fullscreen = 1
    self.window.fullscreen()

    align = gtk.Alignment()
    align.set(0.5,0.5,0,0)
    align2 = gtk.Alignment()
    align2.set(0.5,0.5,0,0)

    mainvbox = gtk.VBox()
    vbox = gtk.VBox()
    hbox = gtk.HBox()
    hbox2 = gtk.HBox()
    loginhbox = gtk.HBox()
    bottomhbox = gtk.HBox()
    tophbox = gtk.HBox()

    label1 = gtk.Label("Username:")
    label2 = gtk.Label("Password:")
    self.feedlabel = gtk.Label("Login failed")

    self.entry1 = gtk.Entry()
    self.entry2 = gtk.Entry()
    self.entry2.set_visibility(False)

    self.loginbutton = gtk.Button("Login")
    restartbutton = gtk.Button("Restart Thin Client")
    shutdownbutton = gtk.Button("Shutdown Thin Client")
    restartbutton.connect("clicked", lambda x: self.setfullscreen())
    shutdownbutton.connect("clicked", lambda x: gtk.main_quit())
    self.loginbutton.connect("clicked", lambda x: self.login())

    tophbox.pack_start(self.feedlabel,True,False)
    hbox.pack_start(label1, True,False)
    hbox.pack_start(self.entry1, True,False)
    hbox2.pack_start(label2, True,False)
    hbox2.pack_start(self.entry2, True,False)
    loginhbox.pack_start(self.loginbutton,True,False)
    bottomhbox.pack_start(restartbutton,True,False)
    bottomhbox.pack_start(shutdownbutton,True,False)

    hbox.set_border_width(10)
    hbox2.set_border_width(10)
    label1.set_padding(10,0)
    label2.set_padding(10,0)
    bottomhbox.set_spacing(30)

    vbox.pack_start(tophbox,True,False)
    vbox.pack_start(hbox,True,False)
    vbox.pack_start(hbox2,True,False)
    vbox.pack_start(loginhbox,True,False)

    align.add(vbox)
    align2.add(bottomhbox)
    mainvbox.pack_start(align,True,True)
    mainvbox.pack_start(align2,False,True)
    self.window.add(mainvbox)
    self.window.show_all()
    self.feedlabel.hide()

  def login(self):
    usern = self.entry1.get_text()
    passw = self.entry2.get_text()
    self.entry1.set_text("")
    self.entry2.set_text("")
    self.loginbutton.set_sensitive(False)
    self.feedlabel.show()
    gobject.timeout_add(1500, self.loggingin)
    if usern == "" or passw == "":
      self.feedlabel.set_text("Login Failed")
      self.feedlabel.modify_fg(gtk.STATE_NORMAL,gtk.gdk.color_parse("red"))
    else:
      self.feedlabel.set_text("Login Successful")
      self.feedlabel.modify_fg(gtk.STATE_NORMAL,gtk.gdk.color_parse("darkgreen"))
      print "Logging in with the username \""+ usern +"\" and the password \""+ passw +"\"."

  def loggingin(self):
      self.feedlabel.set_text("")
      self.feedlabel.hide()
      self.loginbutton.set_sensitive(True)

  def setfullscreen(self):
    if self.fullscreen:
      self.window.unfullscreen()
      self.fullscreen = 0
    else:
      self.window.fullscreen()      
      self.fullscreen = 1

if __name__ == "__main__":
  application = app()
  gtk.main()

```

---

### Post by cgroza on 2011-08-17
You can remove the self for variables that are not used outside __init__.
You should learn about OOP. It's not that complex and it is a feature that you really can't avoid when coding user interfaces.

---

