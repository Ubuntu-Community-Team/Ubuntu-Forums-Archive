---
title: "Help with basic pygtk, thread and output"
date: 2006-03-13
forum: Programming Talk
---

### Post by sapo on 2006-03-13
Hi guys, anyone could give me some guidance please, i m completely lost in this threading stuff.

What i need to do is kinda simple:

I have a gui, and i want to execute a shell command in the background (apt-get for example) and i want the output to go to a textbox in my pygtk gui.

So i need a thread for it cause if i just run the command it will lock the gui and not show any output.

I was reading about threading and stuff, but i cant understand that at all!

Anyone could help me with this? from where should i start? my gui is almost done and its working, but i cant make the output show in the textbox.

this is my textbuffer:

```
	def terminal(self):
		textview = self.principal.get_widget("terminal")
		self.textbuffer = textview.get_buffer()
```

I need to send the background task output to it.. any help is welcome, thanx! :-D

---

### Post by WelterPelter on 2006-03-13
Have you seen [this page]("http://www.async.com.br/faq/pygtk/index.py?querytype=simple&query=threading&req=search")?

It goes into how to work with these issues. Pretty straightforward, once you see how they do it. That's only if you want the code to be part of the UI, however.

If you want to run if from a separate "'model" or backend, I can show you how to do that, but I have to see the rest of your code.

---

### Post by sapo on 2006-03-13
Hum.. this page you posted seens very easy, i ll try to hack something with that :mrgreen:

My code is kinda simple you know:

```
#!/usr/bin/env python

import pygtk
import os
pygtk.require("2.0")
import gtk
import gtk.glade

	
class main:
	def __init__(self):
		self.principal = gtk.glade.XML("lazy.glade")
		dic = {"on_principal_destroy" : self.Destroy,
		"on_btn_quit_clicked" : self.Destroy}
		self.principal.signal_autoconnect(dic)
		self.list()
		self.terminal()
		gtk.main()
	def Destroy(self, *args):
		gtk.main_quit()

	def list(self):
		tree = self.principal.get_widget("list")
		self.list = gtk.ListStore(bool,str)
		options = [[1,"programa1"],[2,"programa2"],[3,"programa3"]]

		renderer1 = gtk.CellRendererToggle()
		renderer1.set_property('activatable', True)
		renderer1.connect( 'toggled', self.selection, self.list)
		tree.insert_column_with_attributes(0, "Select",renderer1, active=0)
		renderer2 = gtk.CellRendererText()
		tree.insert_column_with_attributes(1,"Install",renderer2, text=1)
		i = 0
		for option in options:
			self.list.append(option)
			self.list[i][0] = False
			i += 1
		tree.set_model(self.list)

	def terminal(self):
		textview = self.principal.get_widget("terminal")
		self.textbuffer = textview.get_buffer()

	def selection( self, cell, path, model ):
		model[path][0] = not model[path][0]
		a = testit(self.textbuffer)
		a.start()		
#		self.textbuffer.set_text(subprocess.Popen(cmd, shell=True, bufsize=1024, stdout=subprocess.PIPE).stdout)
		return

main()
```

it actually doesnt do anything, but i m trying to make the thread first, cause the rest is a piece of cake :p

---

### Post by WelterPelter on 2006-03-13
Can you post (or send me) the lazy.glade file, too?

---

### Post by sapo on 2006-03-13
I tried this too, and this didnt work, the command runs, but the gui is locked

```
#!/usr/bin/env python

import pygtk
import os, threading, locale
pygtk.require("2.0")
import gtk
import gtk.glade

encoding = locale.getpreferredencoding()
utf8conv = lambda x : unicode(x, encoding).encode('utf8')
	
class main:
	def __init__(self):
		self.principal = gtk.glade.XML("lazy.glade")
		dic = {"on_principal_destroy" : self.Destroy,
		"on_btn_apply_clicked" : self.Apply,
		"on_btn_quit_clicked" : self.Destroy}
		self.principal.signal_autoconnect(dic)
		self.list()
		self.terminal()
		gtk.main()
	def Destroy(self, *args):
		gtk.main_quit()

	def list(self):
		tree = self.principal.get_widget("list")
		self.list = gtk.ListStore(bool,str)
		options = [[1,"programa1"],[2,"programa2"],[3,"programa3"]]

		renderer1 = gtk.CellRendererToggle()
		renderer1.set_property('activatable', True)
		renderer1.connect( 'toggled', self.selection, self.list)
		tree.insert_column_with_attributes(0, "Select",renderer1, active=0)
		renderer2 = gtk.CellRendererText()
		tree.insert_column_with_attributes(1,"Install",renderer2, text=1)
		i = 0
		for option in options:
			self.list.append(option)
			self.list[i][0] = False
			i += 1
		tree.set_model(self.list)
	
	def Apply(self, obj):
		thr = threading.Thread(target= self.read_output, args=(self.textbuffer, self.command))
		thr.run()
	def terminal(self):
		self.command = "ls -R"
		textview = self.principal.get_widget("terminal")
		self.textbuffer = textview.get_buffer()
	def read_output(self, buffer, command):
		stdin, stdouterr = os.popen4(command)
		for line in stdouterr.readlines():
				buffer.insert(buffer.get_end_iter(), utf8conv(line))

	def selection( self, cell, path, model ):
		model[path][0] = not model[path][0]
		a = testit(self.textbuffer)
		a.start()		
#		self.textbuffer.set_text(subprocess.Popen(cmd, shell=True, bufsize=1024, stdout=subprocess.PIPE).stdout)
		return

main()

```

The lazy.glade and lazy.py are attached, thanx.

---

### Post by WelterPelter on 2006-03-14
That looks pretty cool. 

To make any threading stuff work in pygtk, do this:

1) First, when you initialize the app, include this line:
            ```
gtk.threads_init()
```

2) Then, surround any code you want to run in a separate thread like this:
          ```
gtk.threads_enter()
        	try:
			"""do something in a separate thread here"""
		finally:
            		gtk.threads_leave()
```

(Sorry the formatting is screwed up on that.)

---

### Post by Jadd on 2008-03-28
I found this guide helpful:
[http://aruiz.typepad.com/siliconisland/2006/04/threads_on_pygt.html](http://aruiz.typepad.com/siliconisland/2006/04/threads_on_pygt.html)
I replaced gtk.threads_init with gtk.gdk.threads_init (and enter and leave), because I got a message in the terminal saying gtk.threads_init was deprecated, and it worked great!

---

