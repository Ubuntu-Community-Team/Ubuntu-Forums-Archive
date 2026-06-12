---
title: "Python + Glade"
date: 2005-08-21
forum: Programming Talk
---

### Post by paulfox on 2005-08-21
Hi all,
I'm trying to learn glade with python. Does anyone have any good links for helping me learn a bit more? something starting off with simple examples.
Ive done a couple, where I have a label, and entry and button widgets. enter text into the entry box and click the button and it sends the text to the label.
something that can help be build on that slowly, would be great.


A problem i'm having at the moment is when i have a glade project, i can run it fine. add a 2nd window the project, but when i launch it, both windows show up at the same time. which isn't what i want. i imagine it's something to do with the design.

any hints, ideas etc very welcome!
thanks

---

### Post by gheorghe_pop on 2005-08-21
[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/)
This is what i'm using right now.

---

### Post by paulfox on 2005-08-21
yeah thats one that i've also seen. but it doesn't give enough of an explanation for me. for example:
```

from SimpleGladeApp import SimpleGladeApp
from SimpleGladeApp import bindtextdomain

```
what is SimpleGladeApp, and what does bindtextdomain do?
there's no explanation of what path, root and domain variables do, and where they're used. what is gladedir and localedir etc etc. 

I'd like to know what these things are doing, rather than blindly use them

---

### Post by psychicdragon on 2005-08-23
SimpleGladeApp is the library you're using to simplifiy development. Basically, what it does is opens your glade file and activates all your widgets for you and connects all your signals. You can do all this yourself with the gtk.glade module but it will result in more lines of code (but one less dependency).

If you have no idea what you're doing you should probably start by writing your app without SimpleGladeApp. That's the best way to figure out what's going on. You can also look at the source of SimpleGladeApp.py, it's well commented. The pygtk language reference is [here](http://www.pygtk.org/pygtk2reference/index.html), I suggest you take a look at it too.

Here's a what a very simple pygtk app that uses gtk.glade looks like:```
#!/usr/bin/env python

import gtk
import gtk.glade

class myApp:
	def __init__(self):
		gladefile = "foo.glade"
		mywindow = "window1"
		self.widgets = gtk.glade.XML(gladefile, mywindow)
		dic = {"on_button1_clicked" : self.on_button1_clicked}
		self.widgets.signal_autoconnect(dic)
		self.entry1 = self.widgets.get_widget("entry1")
		
	def on_button1_clicked(self, widget):
		print "You said: %s" % self.entry1.get_text()

app = myApp()
gtk.main()
```This app (if you had the appropriate glade file) prints the contents of a text entry to the terminal when you click the button. 

SimpleGladeApp does all the stuff in the __init__() function for you. The more widgets and signals your glade file contains the more lines of code this saves you.

bindtextdomain and the localdir variable are used for translations, I wouldn't worry about them. At least not for now.

---

### Post by gheorghe_pop on 2005-08-24
I was wondering how can i implement a message box using SimpleAppGlade.py. Have I to just design my msg_box or there is a specific command for creating msg_box?

---

### Post by psychicdragon on 2005-08-24
The [gtk.MessageDialog](http://www.pygtk.org/pygtk2reference/class-gtkmessagedialog.html)  class is what you're looking for.

Here's some advice:
Drop SimpleGladeApp for now and start making your way through the [pygtk tutorial](http://www.pygtk.org/pygtk2tutorial/index.html) (the [class reference](http://www.pygtk.org/pygtk2reference/gtk-class-reference.html) is also essential) . Later, once you have a better understanding of what your code is actually doing, you can pick it back up.

---

