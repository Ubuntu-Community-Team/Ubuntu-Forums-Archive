---
title: "RealTime update for GTK TreeView  ???"
date: 2009-10-26
forum: Programming Talk
---

### Post by baskar007 on 2009-10-26
i am new to PyGtk. i don't know how to get realtime update on gtk.
such as downloadmanagers show's every time the speed changes. 

here is my. in this code the "f='/home/tree.txt'" is a log file .this file regularly updated by another thread. i want to add the file contents to TreeView with regular update.
is this need any loop, if yes where i can loop.

```

import codecs,gtk

def redraw():
	f='/home/tree.txt'  #this is realtime log file
	log=codecs.open(f,'r','utf-8')
	d=log.read()
	log.close
	return d


DATA = [
	[0, redraw()],
	[1, "one"],
	[2, "two"],
	[3, "three"],
	[4, "four"],
	[5, "five"],
	[6, "six"],
	[7, "seven"],
	[8, "eight"],
	]

class t_treeview_sort(gtk.Window):
	def __init__(self):
		gtk.Window.__init__(self)

		self.set_title("Treeview")
		self.set_geometry_hints(min_width=200)
		self.connect("destroy", gtk.main_quit)

		self.list = gtk.ListStore(int, str)
		self.sort_order = gtk.SORT_ASCENDING
		while gtk.events_pending():
			gtk.main_iteration()
		for data in DATA:
			iter = self.list.append( data )
			self.list.set(iter)

		self.treeview = gtk.TreeView()
		model = self.treeview.get_selection()
		model.set_mode(gtk.SELECTION_SINGLE)
		r = gtk.CellRendererText()

		tc = gtk.TreeViewColumn("Id", r, text=0)
		self.treeview.insert_column(tc, -1)

		tc = gtk.TreeViewColumn("Text", r, text=1)
		self.treeview.insert_column(tc, -1)

		self.treeview.set_model(self.list)
		self.treeview.set_headers_clickable(True)
		

		self.treeview.show()
		self.add(self.treeview)

t = t_treeview_sort()
t.show()
gtk.main()

```

Thanks in advance. :)

---

### Post by giuspen on 2009-10-26
probably what you need is a timer, you can find a good example [here]("http://www.pygtk.org/pygtk2tutorial/sec-ProgressBars.html#progressbarfig")

---

### Post by baskar007 on 2009-10-27
Thank you.
i have added timer on mainloop.but still i can't get realtime update.
here is the code this will show a time on window.
```

#!/usr/bin/env python
import pygtk,time
pygtk.require('2.0')
import gtk, gobject

def timeout(instan):
    instan.data=str(time.time())  #Here the s.data will change
    print instan.data
    instan.pr()
    return 1


class ui:    
    def butt(s):
        s.w=gtk.Window()
        s.data=str(time.time())
        s.b=gtk.Label()
        s.b.set_label(s.data)
        s.w.set_title="baskar"
        s.w.set_size_request(250, 200)
        s.w.connect("destroy",s.destroy,None)
        s.b.show()
        s.w.add(s.b)
        s.timer=gobject.timeout_add (1000, timeout, s)
        s.w.show()
        
    def refresher(s):
        s.w.queue_draw()
        print s.data,"$$$$$$$$$$$$$$$$$$$$$$$$$$$$"
        while gtk.events_pending():
            print "refreshing"
            #gtk.main_iteration_do(True)
            gtk.main_iteration_do(False)
    
    def destroy(s, widget, data=None):
        gobject.source_remove(s.timer)
        s.timer = 0
        gtk.main_quit()

def loop():
    gtk.main()
    return 0
UI=ui()
UI.butt()
loop()

```


any ideas?

---

### Post by baskar007 on 2009-10-27
> **baskar007 said:**
> Thank you.
i have added timer on mainloop.but still i can't get realtime update.
here is the code this will show a time on window.
```

#!/usr/bin/env python
import pygtk,time
pygtk.require('2.0')
import gtk, gobject

def timeout(instan):
    instan.data=str(time.time())  #Here the s.data will change
    print instan.data
    instan.pr()
    return 1


class ui:    
    def butt(s):
        s.w=gtk.Window()
        s.data=str(time.time())
        s.b=gtk.Label()
        s.b.set_label(s.data)
        s.w.set_title="baskar"
        s.w.set_size_request(250, 200)
        s.w.connect("destroy",s.destroy,None)
        s.b.show()
        s.w.add(s.b)
        s.timer=gobject.timeout_add (1000, timeout, s)
        s.w.show()
        
    def refresher(s):
        s.w.queue_draw()
        print s.data,"$$$$$$$$$$$$$$$$$$$$$$$$$$$$"
        while gtk.events_pending():
            print "refreshing"
            #gtk.main_iteration_do(True)
            gtk.main_iteration_do(False)
    
    def destroy(s, widget, data=None):
        gobject.source_remove(s.timer)
        s.timer = 0
        gtk.main_quit()

def loop():
    gtk.main()
    return 0
UI=ui()
UI.butt()
loop()

```


any ideas?
I got the answer. place all data changes in UI class.
```

#!/usr/bin/env python
import pygtk,time
pygtk.require('2.0')
import gtk, gobject

#This function only for calling refresh in UI
def timeout(j):
    j.refresh()
    return 1


class ui:    
    def butt(s):
        s.w=gtk.Window()
        s.data=str(time.time())
        s.b=gtk.Label()
        s.b.set_label('baskassssss')
        s.w.set_size_request(250, 200)
        s.w.connect("destroy",s.destroy,None)
        s.b.show()
        s.w.add(s.b)
        s.timer=gobject.timeout_add (700, timeout, s)
        s.w.show()
        
    def refresh(s):
        s.b.set_label(time.strftime("%s"))       #----DATA change here
        #time.sleep(0.3)
        #s.b.queue_draw()
        print s.data,"$$$$$$$$$$$$$$$$$$$$$$$$$$$$"
        while gtk.events_pending():
            print "refreshing"
            gtk.main_iteration_do(True)
            
    def destroy(s, widget, data=None):
        gobject.source_remove(s.timer)
        s.timer = 0
        gtk.main_quit()

def loop():
    gtk.main()
    return 0
UI=ui()
UI.butt()
loop()

```

---

### Post by giuspen on 2009-10-27
the pygtk faq are always useful, in this case you can look [here]("http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp")

---

### Post by baskar007 on 2009-10-27
i have readed the faq.

row_changed() emits the "row-changed" signal. Call this when there are changes in the content of a row (node) in your model.

row_changed() require "path" for the row.
what is this path??

---

### Post by giuspen on 2009-10-27
in a treestore, a path is a tuple identifying the row (take a look to the [pygtk tutorial]("http://www.moeraki.com/pygtktutorial/pygtk2tutorial/sec-TreeModelInterface.html#sec-ReferringToTreeModelRows"))

---

