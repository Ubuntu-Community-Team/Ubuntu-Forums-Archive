---
title: "[SOLVED] threads in python"
date: 2008-02-18
forum: Programming Talk
---

### Post by Choad on 2008-02-18
ok decided a new thread (pun semi-intended) should be made about this coz it might get some more replies with a more appropriate name.

trying to get a threaded app working in python

here is an abbridged version of what i've got

```

#!/usr/bin/env python

# imports
import pygtk
pygtk.require("2.0")
import gtk
from md5 import md5
import sys
import MySQLdb
import threading

# base window class
class Base ():
	def __init__(self):	
		Checking_thread().start()
	
	def main(self):
		gtk.main()

class Checking_thread(threading.Thread):
	def run(self):
		gtk.gdk.threads_enter()
# do some cpu intensive stuff here
		gtk.gdk.threads_leave()

if __name__ == "__main__":
	gtk.gdk.threads_init()
	base = Base()
	gtk.gdk.threads_enter()
	base.main()
	gtk.gdk.threads_leave()

```

obviously all the code that actually does stuff has been ripped out but i can't imagine that's where the problem lies... the app loads, the gui appears, but the gui get's unresponsive while the "Checking_thread" thread is doing it's business. where have i gone wrong?

thanks

---

### Post by imdano on 2008-02-18
```
#!/usr/bin/env python

# imports
import pygtk
pygtk.require("2.0")
import gtk
from md5 import md5
import sys
import MySQLdb
import threading

# base window class
class Base ():
	def __init__(self):
                check = Checking_thread()	
		check.start()
	
	def main(self):
		gtk.main()

class Checking_thread(threading.Thread):
        def __init__(self):
                threading.Thread.__init__()
	def run(self):
		gtk.gdk.threads_enter()
# do some cpu intensive stuff here
		gtk.gdk.threads_leave()

if __name__ == "__main__":
	gtk.gdk.threads_init()
	base = Base()
	gtk.gdk.threads_enter()
	base.main()
	gtk.gdk.threads_leave()

```See if that works any better.

---

### Post by Choad on 2008-02-18
nope... same.

here's the full source

```

#!/usr/bin/env python

# imports
import pygtk
pygtk.require("2.0")
import gtk
from md5 import md5
import sys
#import MySQLdb
import threading

# base window class
class Base():
	def __init__(self):
		# create window and widgets
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_border_width(5)
		self.button = gtk.Button("whatever")
		self.window.add(self.button)
		
		self.window.show()
		self.button.show()
		
		# connect signal handlers
		self.window.connect("delete_event", self.delete_event)
		self.window.connect("destroy", self.destroy)
		self.button.connect("clicked", self.hello, None)
		
		check = Checking_thread()
		check.start()
	
	def hello(self, widget, data=None):
		print sys.argv[1]
	
	def delete_event(self, widget, event, data=None):
		print "Delete event..."
		return False
	
	def destroy(self, widget, data=None):
		gtk.main_quit()
	
	def main(self):
		gtk.main()

class Checking_thread(threading.Thread):
	def __init__(self):
		threading.Thread.__init__(self)

	def run(self):
		# get hash of program to check
		gtk.gdk.threads_enter()
		try:
			fname = sys.argv[1]
		except:
			print "No argument passed as filename"
			sys.exit(1)
		print "Creating md5..."
		self.program_md5 = self.md5_check(fname)
		print "Done!" 
#		bla = self.search_db(self.program_md5, "000193")
#		print bla
		gtk.gdk.threads_leave()
		
	# md5 function
	def md5_check(self, fname):
		try:
			s = md5(open(fname, "rb").read()).hexdigest()
			return s
		except:
			print """Error creating md5 hash for file "%s" """ % fname
			return 0
			
	# db lookup	
#	def search_db(self, md5, wine_ver):
#		db = MySQLdb.connect(host="localhost", user="root", passwd="", db="test")
#		cursor = db.cursor()
#		cursor.execute("""SELECT * FROM appdb WHERE hash="%s" AND wine_version="%s" """, (md5, wine_ver))
#		result = cursor.fetchall()
#		return result

if __name__ == "__main__":
	gtk.gdk.threads_init()
	base = Base()
	gtk.gdk.threads_enter()
	base.main()
	gtk.gdk.threads_leave()

```

i commented out the sql stuff coz that would just give you an error. give it a file as an argument. you should be able to click on the button while it's working out the md5 hash but you can't (the button doesn't even appear any more). obviously the larger the file you give it the longer it'll take to work. i'd suggest not giving it a file larger than 50 mb otherwise it's just annoyingly long

---

### Post by Choad on 2008-02-19
ok the theads_enter and threads_leave around the md5 stuff was causing it to lock that thread... so removing them made it work :D

---

### Post by imdano on 2008-02-19
Yeah, removing those was going to be my next suggestion.

---

