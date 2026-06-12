---
title: "Something wrong with PyGTK notebook"
date: 2010-06-14
forum: Programming Talk
---

### Post by NoBugs! on 2010-06-14
I noticed a problem with a PyGTK notebook sometimes not selecting the right tab when I use .set_current_page(num). I made a small test to see if this always happens, and this not only doesn't work right, it also causes segfault sometimes! When a tab is clicked, it goes into infinite loop, or sometimes segfaults, if you use the arrow keys it lets you change the tab sometimes, but it still doesn't work as expected. Is there something seriously gone wrong with my pygtk installation or is it a bug in pygtk? or something wrong with this code? Sometimes I start it and it goes into infinite loop, other times it starts fine, then after changing selected tab it goes into infinite loop, it's unpredictable.

```
#!/usr/bin/env python

# based on example notebook.py

import pygtk
pygtk.require('2.0')
import gtk

class NotebookExample:

	def delete(self, widget, event=None):
		gtk.main_quit()
		return False

	def tabChange(self,obj1,obj2,i):
		if self.canupdate:
			self.canupdate = False
			self.newtabs(i) #update it.
			print i
		
	def newtabs(self,i):
		#remove all tabs
		while self.notebook.get_n_pages():
			self.notebook.remove_page(0)
		#updated tabs:
		for n in range(3):
			label = gtk.Label(n)
			if i==n:
				label.set_markup("<b>selected</b>")
			self.notebook.append_page(gtk.Label(i),label)
			print "added one"
			if i==n:
				self.notebook.set_current_page(-1) #select this last one.
		self.notebook.show_all()
		self.canupdate = True

	def __init__(self):
		window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.connect("delete_event", self.delete)
		self.notebook = gtk.Notebook()
		window.add(self.notebook)
		self.notebook.connect("switch-page",self.tabChange)
		window.show_all()
		self.canupdate = False #only one update going.
		self.newtabs(0)

def main():
	gtk.main()
	return 0

if __name__ == "__main__":
    NotebookExample()
    main()

```

---

### Post by NoBugs! on 2010-06-14
Tried reinstalling python gtk with synaptic, restarting, it didn't help...
I tried debugging with winpdb, but it keeps freezing when this script freezes :(
How can I see where it crashes with segfault?

---

### Post by diesch on 2010-06-15
When the *set_current_page()* call in *newtabs()* generates a* switch-page* signal, that isn't handled immediately but inserted into the event queue to be handled after* newtabs() *finished - at which point *canupdate* is *True* again.

Also the *self.notebook.show_all()* selects the first page so that *set_current_page()* doesn't do much except generating a signal.

You can fix this by removing the *if i==n:* block and inserting

```

self.notebook.set_current_page(i)
while gtk.events_pending():
    gtk.main_iteration ()

``` right after *self.notebook.show_all()*

---

### Post by NoBugs! on 2010-06-15
Thank you very much - I fixed it so the selected tab has the bold, it seems to work but it still has a couple problems:

When I select a tab and press the right arrow key, it usually selects the next tab and makes it bold text, but sometimes another tab gets selected(This gets worse with more tabs, if you change range(3) to range(30) on line 26). Also, when I hold down the right arrow key, it causes a segfault after about 10s. I had this problem earlier with too much tab switching crashing python, though it isn't as bad now:

```
#!/usr/bin/env python

# based on example notebook.py

import pygtk
pygtk.require('2.0')
import gtk

class NotebookExample:

	def delete(self, widget, event=None):
		gtk.main_quit()
		return False

	def tabChange(self,obj1,obj2,i):
		if self.canupdate:
			self.canupdate = False
			self.newtabs(i) #update it.
			print i
		
	def newtabs(self,i):
		#remove all tabs
		while self.notebook.get_n_pages():
			self.notebook.remove_page(0)
		#updated tabs:
		for n in range(3):
			label = gtk.Label(n)
			if i==n:
				label.set_markup("<b>selected</b>")
			self.notebook.append_page(gtk.Label(i),label)
			print "added one"
			#if i==n:
			#	self.notebook.set_current_page(-1) #select this last one.
		self.notebook.show_all()
		self.notebook.set_current_page(i)
		while gtk.events_pending():
				gtk.main_iteration()
		self.canupdate = True

	def __init__(self):
		window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.connect("delete_event", self.delete)
		self.notebook = gtk.Notebook()
		window.add(self.notebook)
		self.notebook.connect("switch-page",self.tabChange)
		window.show_all()
		self.canupdate = False #only one update going.
		self.newtabs(0)
		window.show_all()

def main():
	gtk.main()
	return 0

if __name__ == "__main__":
    NotebookExample()
    main()
```

---

### Post by StephenF on 2010-06-15
I got this stable by using gtk.Notebook.connect_after instead of connect which then runs your callback for replacing the notebook pages *after* GTK+ has done updating the widget.

Seriously though, I don't understand why you are recreating the notebook pages each time a new page is selected. Consider using gtk.Notebook.set_tab_label_text to change the notebook page title.

---

### Post by NoBugs! on 2010-06-15
Thanks for the tip! Changing it to connect_after("switch-page",self.tabChange) works, it no longer causes segfault after many tab changes, *and* it selects the correct tab (though it selects a nearby tab sometimes, when I hold down arrow key). No more random tab selection :)

---

### Post by StephenF on 2010-06-15
> **NoBugs! said:**
> It selects a nearby tab sometimes, when I hold down arrow key.
What about this? I'm guessing it will behave itself.
```

#! /usr/bin/env python

"""Numerated selector using a GTK Notebook widget - example."""

import pygtk
pygtk.require('2.0')
import gtk

class NotebookSelector(gtk.Notebook):
    orig = None
    
    def cb_switch_page(self, nb, page, page_num):
        if self.orig:
            self.set_tab_label(*self.orig)
        child = self.get_nth_page(page_num)
        self.orig = (child, self.get_tab_label(child))
        self.set_tab_label(child, self.selected)
    
    def __init__(self, labels=("0",), select_text="<b>selected</b>"):
        gtk.Notebook.__init__(self)
        for lt in labels:
            tab_label = gtk.Label(lt)
            internal_label = gtk.Label(lt)
            self.append_page(internal_label, tab_label)
            tab_label.show()
            internal_label.show()
            
        self.connect("switch-page", self.cb_switch_page)
        self.selected = gtk.Label()
        self.selected.set_markup(select_text)
        self.selected.show()


class App(object):
    def __init__(self):
        window = gtk.Window()
        window.connect("destroy", lambda w: gtk.main_quit())
        ns = NotebookSelector(("0", "1", "2"))
        window.add(ns)
        ns.show()
        window.show()

if __name__ == "__main__":
    app = App()
    gtk.main()

```

---

