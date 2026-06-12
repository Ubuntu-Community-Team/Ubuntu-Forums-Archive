---
title: "PyGtk and Glade help"
date: 2009-06-25
forum: Programming Talk
---

### Post by jaxsrb on 2009-06-25
Hi,

I'm using Ubuntu 9.04 with Geany editor for PyGtk and Glade Interface Designer, the program so far is consisted of main window and configuration window that is called on push button to be visible. 

In configuration window I have a text entry that needs to save its entry on a button click to a file in same directory called data, couldn't find solution on google search, here is the code of what I am trying to do and failing at :
```

wc_bsave = { "on_wc_bsave_clicked" : self.wc_bsave_clicked }
self.xml.signal_autoconnect(wc_bsave)

```

```

def wc_bsave_clicked(self, widget):
	f = file('data','w')
	f.write(self.wc_txt.get_buffer().get_text)
        f.close()

```

-------------
error while compiling:
Sorry: IndentationError: ('unexpected indent', ('vov-buuter.py', 61, 2, '\t\tws_bquit = { "on_wnd_serv_delete_event" : self.wnd_serv_delete_event }\n'))

error while runing:
ws_bquit = { "on_wnd_serv_delete_event" : self.wnd_serv_delete_event }
^
unexpected indent
-------------

---

### Post by Can+~ on 2009-06-25
f.close() is being indented with spaces, the others with tabulations

---

### Post by jaxsrb on 2009-06-25
Thank you for replying Can+~ ,

Corrected the code and still geting the same error.

---

### Post by master_kernel on 2009-06-26
Well just in case, try running this on the file (subs spaces for tabs, as is now customary :))

```
expand -t8 oldfile | tee -a newfile
```

---

### Post by jaxsrb on 2009-06-26
Problem remains ,here is the full code :

```

#!/usr/bin/env python

import sys

import pygtk
pygtk.require("2.0")
	
import gtk
import gtk.glade

class vovbuuter:
	"""This is vov buuter"""
	
	def __init__(self):
		
		#glade file
		
		self.gladefile = "vov-buuter.glade"  
	        self.xml = gtk.glade.XML(self.gladefile) 
		
		
		#windows load 'em up
		self.wnd_main = self.xml.get_widget("wnd_main")
		self.wnd_conf = self.xml.get_widget("wnd_conf")
		self.wnd_serv = self.xml.get_widget("wnd_serv")
		self.wc_txt_exe = self.xml.get_widget("wc_txt_exe").get_buffer()
		
		
		
		#window main
		wm_bquit = { "on_wnd_main_destroy" : self.wnd_main_destroy }
		self.xml.signal_autoconnect(wm_bquit)

		wm_bconf = { "on_wm_bconf_clicked" : self.wm_bconf_clicked }
		self.xml.signal_autoconnect(wm_bconf)

		wm_bserv = { "on_wm_serv_clicked" : self.wm_bserv_clicked }
		self.xml.signal_autoconnect(wm_bserv)
		
		wm_bupda = { "on_wm_bupda_clicked" : self.wm_bupda_clicked }
		self.xml.signal_autoconnect(wm_bupda)
		
		wm_blaun = { "on_wm_blaun_clicked" : self.wm_blaun_clicked }
		self.xml.signal_autoconnect(wm_blaun)
		
		
		
		
		#window server
		ws_bquit = { "on_wnd_serv_delete_event" : self.wnd_serv_delete_event }
		self.xml.signal_autoconnect(ws_bquit)
		
		
		
		
		#window config
		wc_bquit = { "on_wnd_conf_delete_event" : self.wnd_conf_delete_event }
		self.xml.signal_autoconnect(wc_bquit)
		
		wc_bsave = { "on_wc_bsave_clicked" : self.wc_bsave_clicked }
        self.xml.signal_autoconnect(wc_bsave)
   
		
	
	
	#define window main	
	def wnd_main_destroy(self, widget):
		gtk.main_quit()
	
	def wm_bconf_clicked(self, widget):
		self.wnd_conf.show()
		print "CONFIG"
		return True
		
	def wm_bserv_clicked(self, widget):
		self.wnd_serv.show()
		print "SERVERS"
		return True
		
	def wm_bupda_clicked(self, widget):
		print "UPDATE"
		
	def wm_blaun_clicked(self, widget):
		print "LAUNCH"
		
		
		
	#define window serv
	def wnd_serv_delete_event(self, widget,event):
		self.wnd_serv.hide()
		return True
	
	
	#define window conf
	def wnd_conf_delete_event (self, widget,event):
		self.wnd_conf.hide()
		return True
	
	def wc_bsave_clicked(self, widget):
 		f = file('data','w')
		f.write(self.wc_txt_exe.get_data)
		f.close()
	
			
if __name__ == "__main__":
	vovbuuter()
	gtk.main()


```

Error wile running :
self.xml.signal_autoconnect(wc_bsave)
NameError : 'self' is not defined

---

### Post by master_kernel on 2009-06-26
Exactly. Look at your quote. See how the tabulations don't work with the spaces?

Edit: Example:

```
		#window config
		wc_bquit = { "on_wnd_conf_delete_event" : self.wnd_conf_delete_event }
		self.xml.signal_autoconnect(wc_bquit)
		
		wc_bsave = { "on_wc_bsave_clicked" : self.wc_bsave_clicked }
        self.xml.signal_autoconnect(wc_bsave)

```

Those top lines use tabs. The last one uses spaces. Use one or the other (preferably tabs), but not both.

---

### Post by master_kernel on 2009-06-26
Chances are your editor has it's "space" tabs set to 4, while normal tabs are 8 characters. AKA if you set you editor to use spaces instead of tabs, it only inserts 4 instead of 8 (which is technically correct, but only if you use SOLELY spaces in your program.).

---

### Post by jaxsrb on 2009-06-26
Ty master_kernel,

I corrected the code and fixed that part, now i get :
gtk.entry has no atribute get_buffer 

il try playing with the code if i can solve the write to file part

---

### Post by jaxsrb on 2009-06-26
Solved, ty master_kernel &Can+~ ,

Here is the full code if someone needs a example / help with PyGtk write to text file :
```

#!/usr/bin/env python

import sys

import pygtk
pygtk.require("2.0")
	
import gtk
import gtk.glade

class vovbuuter:
	"""This is vov buuter"""
	
	def __init__(self):
		
		#glade file
		
		self.gladefile = "vov-buuter.glade"  
	        self.xml = gtk.glade.XML(self.gladefile) 
		
		
		#windows load 'em up
		self.wnd_main = self.xml.get_widget("wnd_main")
		self.wnd_conf = self.xml.get_widget("wnd_conf")
		self.wnd_serv = self.xml.get_widget("wnd_serv")
		self.wc_txt_exe = self.xml.get_widget("wc_txt_exe")
		
		
		
		#window main
		wm_bquit = { "on_wnd_main_destroy" : self.wnd_main_destroy }
		self.xml.signal_autoconnect(wm_bquit)

		wm_bconf = { "on_wm_bconf_clicked" : self.wm_bconf_clicked }
		self.xml.signal_autoconnect(wm_bconf)

		wm_bserv = { "on_wm_serv_clicked" : self.wm_bserv_clicked }
		self.xml.signal_autoconnect(wm_bserv)
		
		wm_bupda = { "on_wm_bupda_clicked" : self.wm_bupda_clicked }
		self.xml.signal_autoconnect(wm_bupda)
		
		wm_blaun = { "on_wm_blaun_clicked" : self.wm_blaun_clicked }
		self.xml.signal_autoconnect(wm_blaun)
		
		
		
		
		#window server
		ws_bquit = { "on_wnd_serv_delete_event" : self.wnd_serv_delete_event }
		self.xml.signal_autoconnect(ws_bquit)
		
		
		
		
		#window config
		wc_bquit = { "on_wnd_conf_delete_event" : self.wnd_conf_delete_event }
		self.xml.signal_autoconnect(wc_bquit)
		
		wc_bsave = { "on_wc_bsave_clicked" : self.wc_bsave_clicked }
		self.xml.signal_autoconnect(wc_bsave)
   
		
	
	
	#define window main	
	def wnd_main_destroy(self, widget):
		gtk.main_quit()
	
	def wm_bconf_clicked(self, widget):
		self.wnd_conf.show()
		print "CONFIG"
		return True
		
	def wm_bserv_clicked(self, widget):
		self.wnd_serv.show()
		print "SERVERS"
		return True
		
	def wm_bupda_clicked(self, widget):
		print "UPDATE"
		
	def wm_blaun_clicked(self, widget):
		print "LAUNCH"
		
		
		
	#define window serv
	def wnd_serv_delete_event(self, widget,event):
		self.wnd_serv.hide()
		return True
	
	
	#define window conf
	def wnd_conf_delete_event (self, widget,event):
		self.wnd_conf.hide()
		return True
	
	def wc_bsave_clicked(self, widget):
 		f = file('data','w')
		f.write(self.wc_txt_exe.get_text())
		f.close()
	
			
if __name__ == "__main__":
	vovbuuter()
	gtk.main()

```

---

