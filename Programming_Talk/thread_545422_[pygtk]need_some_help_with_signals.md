---
title: "[pygtk]need some help with signals"
date: 2007-09-07
forum: Programming Talk
---

### Post by Max_Might on 2007-09-07
Hello. I am learning PyGTK and I am writing a simple program, just to understand the basics.
I have main window and the when you click the "about" button new window pops up with some text and close buton. I cant get this close buton to close the new window.
The only workaround I can think of, is that every window is created as a new object, not as method.
Which one is the better option/practice?

Here is the code:

```
import pygtk
pygtk.require("2.0")
import gtk

class Main_Window:
	def __init__(self):
		self.in_info = False
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("Test")
		
		self.window.set_border_width(3)
		self.window.set_icon(None)
		self.window.set_resizable(False)
		self.window.set_size_request(170, 250)
		self.window.connect("delete_event", self.delete_event)
		
		
		frame = gtk.Frame("Menu")
		self.window.add(frame)
		vbox=gtk.VBox(False, 0)
		frame.add(vbox)
		
		image=gtk.Image()
		image.set_from_file("logo.png")
		vbox.pack_start(image, False, False, 0)
		
		
		button_browse=gtk.Button("browse", gtk.STOCK_OPEN)
		vbox.pack_start(button_browse, False, False, 5)
		
		button_add=gtk.Button("add", gtk.STOCK_ADD)
		vbox.pack_start(button_add, False, False, 0)
		
		button_about = gtk.Button("about", gtk.STOCK_ABOUT)
		button_about.connect("clicked", self.information)
		vbox.pack_start(button_about, False, False, 5)
		
		button_quit = gtk.Button("quit", gtk.STOCK_QUIT)
		button_quit.connect("clicked", self.delete_event, button_quit)
		vbox.pack_start(button_quit, False, False, 0)
		
		image.show()
		button_browse.show()
		button_add.show()
		button_about.show()
		button_quit.show()
		frame.show()
		vbox.show()
		self.window.show()
		
	def information(self, widget):
		if self.in_info == False:
			self.info_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
			self.info_window.set_border_width(3)
			self.info_window.connect("delete_event", self.delete_info_window)
			
			vbox=gtk.VBox(False, 0)
			frame = gtk.Frame("About")
			frame.add(vbox)
			
		
			label=gtk.Label("asda\nfgdfghsdlkjgghksgkdgnasda")
			vbox.pack_start(label, False, False, 0)
			
			close_button=gtk.Button("close", gtk.STOCK_CLOSE)
			close_button.connect("clicked", self.delete_info_window, close_button)
			vbox.pack_start(close_button, False, False, 5)
		
			close_button.show()
			frame.show()
			vbox.show()
			label.show()
			self.info_window.add(frame)
			self.info_window.show()
			self.in_info = True
		
	def delete_event(self, widget, event):
		gtk.main_quit()
		return False
		
	def delete_info_window(self, widget, event):
		self.in_info = False
		return False
		
if __name__ == "__main__":
	a=Main_Window()
	gtk.main()
```

---

### Post by blackmh on 2007-09-07
I'm starting with pygtk myself although I'm using Glade for GUI design. 
I  started with about dialog myself and couldn't do anything with it. Seems that about dialogs are special in gtk enviroment ,I can't explain why, I'm not "there" yet.

If you want see glade in action, there are couple of nice tutorials on [http://www.learningpython.com/](http://www.learningpython.com/) that will help you start

---

### Post by bashologist on 2007-09-07
Soemthing like this?
```
#!/usr/bin/env python
import gtk

def information(widget):
	window2 = gtk.Window(gtk.WINDOW_TOPLEVEL)
	button2 = gtk.Button("close", gtk.STOCK_CLOSE)
	window2.connect("delete_event", lambda w, x: window2.destroy())
	button2.connect("clicked", lambda x: window2.destroy())
	window2.add(button2)
	window2.show_all()

window1 = gtk.Window(gtk.WINDOW_TOPLEVEL)
button1 = gtk.Button("about", gtk.STOCK_ABOUT)
window1.connect("delete_event", lambda w, x: gtk.main_quit())
button1.connect("clicked", information)
window1.add(button1)
window1.show_all()
gtk.main()
```

---

### Post by Max_Might on 2007-09-13
Thank you very much bashologist, that was exactly what i was looking for :)
didnt know about the show_all() method ;]

i have one more question: what is this lambda keyword used for?

---

### Post by bashologist on 2007-09-13
> **Max_Might said:**
> Thank you very much bashologist, that was exactly what i was looking for :)
didnt know about the show_all() method ;]

i have one more question: what is this lambda keyword used for?

I would describe them as inline functions.
[http://www.secnetix.de/~olli/Python/lambda_functions.hawk](http://www.secnetix.de/~olli/Python/lambda_functions.hawk)
[http://www.diveintopython.org/power_of_introspection/lambda_functions.html](http://www.diveintopython.org/power_of_introspection/lambda_functions.html)

```
window1.connect("delete_event", lambda w, x: gtk.main_quit())
```
Is like writing:
```
def destroy(w, x):
	gtk.main_quit()

window1.connect("delete_event", destory)

```It doesn't matter which you choose. I would use lambda since it's easier to write.

---

### Post by Awalton on 2007-09-13
> **bashologist said:**
> 
```
window1.connect("delete_event", lambda w, x: gtk.main_quit())
```
Is like writing:
```
def **destroy**(w, x):
	gtk.main_quit()

window1.connect("delete_event", **destory**)

```It doesn't matter which you choose. I would use lambda since it's easier to write.

And because there's less of a chance of typo ;) *sigh*, shame C doesn't have lambda functions.

---

### Post by Max_Might on 2007-09-14
then why we have 2 parameters here:
> window2.connect("delete_event", lambda w, x: window2.destroy())
and one here
> button2.connect("clicked", lambda x: window2.destroy())

---

### Post by pmasiar on 2007-09-14
> **Max_Might said:**
> i have one more question: what is this lambda keyword used for?

lambda allows you to define anonymous function (with no name, just the body). Advanced programming trick.

---

### Post by bashologist on 2007-09-14
> **Max_Might said:**
> then why we have 2 parameters here:

and one here

When you connect the delete_event signal it automatically passes two parameters to the function. For the clicked signal it does the same except it passes only one parameter. The first parameter that gets passed when you connect is usually the widget that you connected with.

Passing the widget as a parameter automatically is very useful. Here's an example of using the parameter.
```
#!/usr/bin/env python

import gtk, random

window1 = gtk.Window(gtk.WINDOW_TOPLEVEL)
vbox1 = gtk.VBox(True, 0)

def button_clicked(widget):
	label = "%f" % random.random()
	widget.set_label(label)

for int in range(0, 10):
	button1 = gtk.Button("click %d" % int)
	button1.connect("clicked", button_clicked)
	vbox1.pack_start(button1, True, True, 0)

window1.set_title("playing with references")
window1.set_position("center")
window1.set_default_size(500, 100)

window1.connect("delete_event", lambda w, x: gtk.main_quit())
window1.add(vbox1)
window1.show_all()
gtk.main()
```

---

