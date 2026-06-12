---
title: "[SOLVED] Pygtk Threads Problem"
date: 2008-12-08
forum: Programming Talk
---

### Post by flyguy97 on 2008-12-08
I have the following code dealing with pygtk threads [http://pastebin.com/f416ceb0c]("http://pastebin.com/f416ceb0c"), if line 46 is commented out it works as expected but with line 46 the gui blocks until the time is expired and than it pulses my progress bar, I'm new to thread programming in Python and would appreciate any help.

---

### Post by jworr on 2008-12-08
Hi,

The main issue that you are having revolves around the nature of the gtk.  The gtk runs in one thread so updates to the gui and callback functions happen serially.  All calls that update a gui object are actually queued and executed by the gtk thread when it is able.  Thus, the time.sleep call causes the gtk to sleep and not update the gui.  Does my explanation make sense?

---

### Post by flyguy97 on 2008-12-08
It does, but how can I perform a long task while pulsing progress bar so that the user knows something is happening? Both tasks can't be in the same thread??

---

### Post by jworr on 2008-12-08
The long task needs to be in a separate thread.  Create another thread in the callback to do the task.  Once that thread concludes have it notify the other thread that the task is finished.  Alternatively, use one thread to perform the task and update the progress bar as it goes.

---

### Post by jworr on 2008-12-08
also, the following code will allow for gtk events to be processed:

while gtk.events_pending():
    gtk.main_iteration(False)


Although, that strategy has been hit or miss for me.  I found that bit of code on the pygtk faq page, it might have some helpful [insights]("http://faq.pygtk.org/index.py?req=index") for you.

---

### Post by flyguy97 on 2008-12-08
Is there any standard way of notifying the main thread that the child thread has completed or do I need to brew my own solution?

---

### Post by jworr on 2008-12-08
I'm not sure there is a standard way - I'm fairly new to python threading myself.  I think you'll just have to invent that wheel yourself.

---

### Post by flyguy97 on 2008-12-08
This is what I came up with, maybe not the most elegant, but it works.

```
import gobject
import threading
import random, time
import gtk
 
class FractionSetter(threading.Thread):
	def __init__ (self, parent):
		threading.Thread.__init__(self)
		self.parent = parent
 
	def run(self):
		time.sleep(5)
		self.parent.quit_updating()
 
	def stop(self):
		self = None
 
class ThreadTest:
	def __init__(self):
		gtk.gdk.threads_init()
		self.fs = None
		self.worker_processing = False
 
	def quit_updating(self):
		self.worker_processing = False
 
	def main_quit(self, obj):
		if not self.fs == None:
			self.fs.stop()
 
		gtk.main_quit()
 
	def pulse(self):
		self.progressbar.pulse()
 
		return self.worker_processing
 
	def start_new_thread (self, button, data=None):
		if self.fs == None:
			self.fs = FractionSetter(self)
 
		self.fs.start()
 
		self.worker_processing = True
		gobject.timeout_add(100, self.pulse)
 
	def main(self):
		window = gtk.Window()
		vbox = gtk.VBox()
		self.progressbar = gtk.ProgressBar()
		button = gtk.Button("Start")
		vbox.pack_start(button, True, True)
		vbox.pack_start(self.progressbar, True, True)
		window.add(vbox)
		window.show_all()
		button.connect("clicked", self.start_new_thread)
		window.connect('destroy', self.main_quit)
 
		gtk.gdk.threads_enter()
		gtk.main()
		gtk.gdk.threads_leave()
 
if __name__ == '__main__':
	tt = ThreadTest()
	tt.main()
```

---

### Post by flyguy97 on 2008-12-08
Does anyone know how to kill a child process before it is completed?

---

### Post by listener on 2008-12-08
I hope this is not an intrusion, but this thread applies pretty directly to a problem I have.  I have put together a simple nautilus python extension to show the total disk space used per folder, recursively, in the Nautilus listview.  It works and it helps me a great deal, but the first time I click on a large folder (like root!) it blocks nautilus for 2-3 seconds, long enough for it to turn dark, then updates the display.

I suspect there is no good way for a nautilus extension to handle this?  Or is there?  I have some python and pygtk knowledge, but none on threading.

It uses os.walk.

Incidentally, it helped me find 50gigs of usable disk space on an NTFS drive - System Volume Information!  Leftover from vista days.

Thanks a lot!

Bob

---

### Post by jworr on 2008-12-08
_Thread__stop() will do the trick.  However, that is an undocumented private method and using it is a bit reckless.  Though, I don't know of any other way to kill a thread.

---

### Post by jworr on 2008-12-08
Bob, I would try using Python's threading module to start a new thread to do the recursive summation.  Have the thread update the gui once it has determined the total.  I've found this [tutorial]("http://www.devshed.com/c/a/Python/Basic-Threading-in-Python/") helpful for learning python threading.

---

### Post by jworr on 2008-12-08
Also... 50 gigs?!  I wonder what vista was doing...

---

### Post by listener on 2008-12-08
Thank you! I'll check it out.

Bob

(large partition, restore points, etc. I guess.  Vista keeps daily hidden copies - shadow copies - of files)

---

### Post by Flimm on 2008-12-08
If you're going to use threading in your PyGTK app, you should include this early on:
[php]import gobject
gobject.threads_init()[/php]
Also, any code which accesses any GTK widgets in a thread should be called using gobject.idle_add, for example:
[php]class ExampleThread(threading.Thread):
    def run(self):
        function do_something_with_gtk():
             pass # insert code here
        gobject.idle_add(do_something_with_gtk)
[/php]
Otherwise, you're going to get hard-to-debug crashes in your application.

---

### Post by flyguy97 on 2009-01-10
This proved to be what I needed. Thank your for your guidance, sorry for the delayed post but needed to make sure this would do, and it did.

Jason

> **Flimm said:**
> If you're going to use threading in your PyGTK app, you should include this early on:
[php]import gobject
gobject.threads_init()[/php]
Also, any code which accesses any GTK widgets in a thread should be called using gobject.idle_add, for example:
[php]class ExampleThread(threading.Thread):
    def run(self):
        function do_something_with_gtk():
             pass # insert code here
        gobject.idle_add(do_something_with_gtk)
[/php]
Otherwise, you're going to get hard-to-debug crashes in your application.

---

### Post by probono on 2009-02-18
Here is a version of #8 that is a bit more compatible with my brain. 

It displays a pulsing progress bar while executing some lengthy function (here: sleep 2 seconds).

```

import gobject
import threading
import random, time
import gtk
 

class MainThread:

	def __init__(self):
		gtk.gdk.threads_init()
		self.fs = None
 
	def main_quit(self, obj):
		if not self.fs == None: self.fs.stop()
		gtk.main_quit()
 
	def pulse(self):
		self.progressbar.pulse()
		return self.still_working # 1 = repeat, 0 = stop

	def work(self): ###### This would be the actual time-consuming workload
		time.sleep(2) 

	def main(self):
		window = gtk.Window()
		vbox = gtk.VBox()
		self.progressbar = gtk.ProgressBar()
		vbox.pack_start(self.progressbar, True, True)
		window.add(vbox)
		window.show_all()
		window.connect('destroy', self.main_quit)

		WT = WorkerThread(self.work, self)
		WT.start()
		gobject.timeout_add(100, self.pulse)

		gtk.main()


class WorkerThread(threading.Thread):

	def __init__ (self, function, parent):
		threading.Thread.__init__(self)
		self.function = function
		self.parent = parent
 
	def run(self): # when does "run" get executed?
		self.parent.still_working = True
		self.function()
		self.parent.still_working = False
 
	def stop(self):
		self = None
  

if __name__ == '__main__':
	MT = MainThread()
	MT.main()

```

---

