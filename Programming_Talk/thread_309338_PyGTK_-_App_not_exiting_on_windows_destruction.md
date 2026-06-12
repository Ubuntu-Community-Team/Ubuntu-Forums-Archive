---
title: "PyGTK - App not exiting on windows destruction"
date: 2006-11-29
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-29
Hey all

I have taken the plunge into GTK programming with Python. It looks incredibly complex and I am hoping I take to it as I did with Python Console programming. My first problem is this. I am trying to simplest thing. I use Glade to create one window with a label in the middle. I have that working fine but I can't get the window to destroy correctly. Reading a tutorial I have to set the event in the properties window but mine seems different one from the version in the tute. Anyway I set the handle for the GTKWidget > destroy-event. I link this handle to call gtk.main_quit. When closing the window this just leaves the program running just with no window. However if I call the exact same function from a button it works fine. What exactly am I doing wrong?

Any help would be great 

Thanks

Ironfistchamp

---

### Post by bradleyd on 2006-11-29
without seeing your code, you could try 
def destroy(widget, data=None):
      print "destroy signal occurred"
      gtk.main_quit()

---

### Post by ironfistchamp on 2006-11-29
Thanks I am not sure where to put that. I have included my code. I tried putting it in the Class and outside but I kept getting called outside of mainloop error.


```

#!/usr/bin/env python

import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
	sys.exit(1)



class mainGTK:
	

	def __init__(self):

		#Set the Glade file
		self.gladefile = "test.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile)

		dic = {"on_mainwin_destroy_event": destroy(self)}

		self.wTree.signal_autoconnect(dic)
		self.main_win = self.wTree.get_widget("mainwin")

	
if __name__ == "__main__":
	hwg = mainGTK()
	gtk.main()

```

Thanks

Ironfistchamp

---

### Post by ohgod on 2006-11-29
Here's how I do it:

Change this line:
```

dic = {"on_mainwin_destroy_event": destroy(self)}

```
to this:
```

dic = {"on_mainwin_destroy_event": gtk.main_quit}

```

---

### Post by ironfistchamp on 2006-11-29
@ohgod

That is what I had before and it didn't work. What you have put is my actual code. 

Any ideas?

Thanks

Ironfistchamp

---

### Post by Flimm on 2008-06-17
Here's some code that does work and that doesn't require you to define the signals in the glade file.

[php]#!/usr/bin/env python

import sys
try:
    import pygtk
    pygtk.require("2.0")
except:
    pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)



class mainGTK:
    
    def now_quit(self, widget, data=None):
        gtk.main_quit()
        return False
    
    def __init__(self):
        #Set the Glade file
        gladefile = "test.glade"  
        self.wTree = gtk.glade.XML(gladefile)
        
        self.main_win = self.wTree.get_widget("mainwin")
        self.main_win.connect("destroy", self.now_quit)
        
        self.main_win.show_all()

	
if __name__ == "__main__":
    hwg = mainGTK()
    gtk.main()[/php]

Notice I connected to destroy, not destroy-event, I displayed the window manually, and I didn't need to change the glade file.

---

