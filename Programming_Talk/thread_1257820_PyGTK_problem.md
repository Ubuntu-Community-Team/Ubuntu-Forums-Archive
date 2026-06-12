---
title: "PyGTK problem"
date: 2009-09-04
forum: Programming Talk
---

### Post by nipunreddevil on 2009-09-04
I need from this code that var1,var2,var3,var4 should be continuosly read from file(or serial port) and there value be updated continuosly.Also i wish to use these 4 variables for plotting in pygame/matplotlib/VPython .How can i do that.Moreover for every read cycle there has to be a write cycle on to a file(or serial port) and the user must be able to set this value via an entry.have not been able to figure out all this.Moreover with my code i am able to presently display updated information on a button click(where as i wanna use button just to start things of)```

#!/usr/bin/env python

#This program will attempt to read a line from a file using a GUI

import pygtk
pygtk.require('2.0')
import gtk
import re
import time


class Nipun:

	
	f=open('/home/nipun/1.txt')
	vars = re.compile('^(\d+\.?\d*)a(\d+\.?\d*)b(\d+\.?\d*)c(\d+\.?\d*)d(.*)')
	
	def __init__(self):
		self.window=gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("File read GUI Label")
		self.window.connect("delete_event",self.delete_event)
		self.window.set_border_width(10)
		self.box2=gtk.VBox(False,0)
		self.window.add(self.box2)
		self.button=gtk.Button("Read")
		self.button.connect("clicked",self.callback)
		self.box2.pack_start(self.button,True,True,0)
		self.button.show()
		self.label1=gtk.Label()
		self.label2=gtk.Label()
		self.label3=gtk.Label()
		self.label4=gtk.Label()
		self.label5=gtk.Label("A")
		self.label6=gtk.Label("B")
		self.label7=gtk.Label("C")
		self.label8=gtk.Label("D")
		self.box2.pack_start(self.label5,True,True,0)
		self.box2.pack_start(self.label1,True,True,0)
		self.box2.pack_start(self.label6,True,True,0)
		self.box2.pack_start(self.label2,True,True,0)
		self.box2.pack_start(self.label7,True,True,0)
		self.box2.pack_start(self.label3,True,True,0)
		self.box2.pack_start(self.label8,True,True,0)
		self.box2.pack_start(self.label4,True,True,0)
		self.label1.show()
		self.label2.show()
		self.label3.show()
		self.label4.show()
		self.label5.show()
		self.label6.show()
		self.label7.show()
		self.label8.show()
		self.box2.show()
		self.window.show()
				

	def delete_event(self,widget,event,data=None):
		print "Delete event has occcured"
		gtk.main_quit()
		return False


	def callback(self,widget,data=None):
		print "alpha"
		s=hello.f.readline()
		m = re.search(hello.vars, s) # Run the regexp on the packet
		var1 = m.group(1) # take out the values
		var2 = m.group(2)
		var3 = m.group(3)
		var4 = m.group(4)
		hello.label1.set_text(var1)
		hello.label2.set_text(var2)
		hello.label3.set_text(var3)
		hello.label4.set_text(var4)
		

	def main(self):
		gtk.main()
if __name__=="__main__":
		hello=Nipun()
		hello.main()
	

		
	

```

---

### Post by nipunreddevil on 2009-09-04
I forgot to add that my text file 1.txt .It is added as an attachment

---

### Post by Hanratty on 2009-09-04
Use function "eval", for example:

data = '&#xE1'
uni = eval("u'\\%s'"%data[2:]) ## u'\xE1' or u'á'
st = uni.encode('utf-8') ## 'á'

Is there another problem?

On 7/17/09, Bertrand Kintanar <b3rxkinta...@gmail.com> wrote:
>
> On 7/17/09 7:53 PM, Chris Camacho wrote:
>>  hmmm...
>>
>>  being that
>>
>>  print '\\'
>>
>>  displays
>>
>>  '\'
>>
>>  isn't that a bug?
>>
>>
> that is one of my question that it been troubling me. why is replace
> have a special treatment in dealing with escape characters while other
> function such as print does the exact thing which escapes the character.
> if i follow it correctly replace should only see one backslash to be
> inserted in the string instead of two.

---

### Post by nipunreddevil on 2009-09-04
> **Hanratty said:**
> Use function "eval", for example:

data = '&#xE1'
uni = eval("u'\\%s'"%data[2:]) ## u'\xE1' or u'á'
st = uni.encode('utf-8') ## 'á'

Is there another problem?

On 7/17/09, Bertrand Kintanar <b3rxkinta...@gmail.com> wrote:
>
> On 7/17/09 7:53 PM, Chris Camacho wrote:
>>  hmmm...
>>
>>  being that
>>
>>  print '\\'
>>
>>  displays
>>
>>  '\'
>>
>>  isn't that a bug?
>>
>>
> that is one of my question that it been troubling me. why is replace
> have a special treatment in dealing with escape characters while other
> function such as print does the exact thing which escapes the character.
> if i follow it correctly replace should only see one backslash to be
> inserted in the string instead of two.

What is this??
Dont get you?Have you posted in a wrong thread.

---

### Post by cudjoe on 2009-09-04
If I understand, what you need is a thread that periodically sends you a signal, to which you connect your "callback" function.

Look at this working example :
```

import threading
import gobject
import time
gobject.threads_init()


class GtkThread(threading.Thread, gobject.GObject):
	__gsignals__ =  { 
			"my-own-signal": (
				gobject.SIGNAL_RUN_LAST, gobject.TYPE_NONE, []),
			}
	
	def __init__(self):
		threading.Thread.__init__(self)
		gobject.GObject.__init__(self)
		self.stopped = False

	def stop(self):
		self.stopped = True

	def run(self):
		while not self.stopped:
			self.emit("my-own-signal")
			time.sleep(2)

def received(self):
	print "hey man, got it!"

thread = GtkThread()
thread.connect("my-own-signal", received)
thread.start()



```

---

### Post by nvteighen on 2009-09-04
Heck... Use a gtk.Entry... use a callback on modification and tell it to write the file... Read the docs, research the widgets and modify them if necessary! (In Python that's trivial to do)

But the best is to load the file into a buffer, modify the buffer and only when done rewrite the file... Not only because of efficiency (I/O is slow... in all languages), but also because of data safety.

---

### Post by nipunreddevil on 2009-09-04
> **cudjoe said:**
> If I understand, what you need is a thread that periodically sends you a signal, to which you connect your "callback" function.

Look at this working example :
```

import threading
import gobject
import time
gobject.threads_init()


class GtkThread(threading.Thread, gobject.GObject):
	__gsignals__ =  { 
			"my-own-signal": (
				gobject.SIGNAL_RUN_LAST, gobject.TYPE_NONE, []),
			}
	
	def __init__(self):
		threading.Thread.__init__(self)
		gobject.GObject.__init__(self)
		self.stopped = False

	def stop(self):
		self.stopped = True

	def run(self):
		while not self.stopped:
			self.emit("my-own-signal")
			time.sleep(2)

def received(self):
	print "hey man, got it!"

thread = GtkThread()
thread.connect("my-own-signal", received)
thread.start()



```

Thanks but could some one provide the pygtk code.

---

### Post by nipunreddevil on 2009-09-04
> **nvteighen said:**
> Heck... Use a gtk.Entry... use a callback on modification and tell it to write the file... Read the docs, research the widgets and modify them if necessary! (In Python that's trivial to do)

But the best is to load the file into a buffer, modify the buffer and only when done rewrite the file... Not only because of efficiency (I/O is slow... in all languages), but also because of data safety.

Had tried out that as well,not much of a difference.How can i know if a varible's value is changed and the label/entry text needs to be updated.Threading approach seems a nice way.What do you say?

---

### Post by nipunreddevil on 2009-09-04
Well thanks to replies i have been able to adavnce a bit in my code.Now i use two threads and run them under while True.Now basically i wish that if all values/lines in 1.txt have been read and there is no change in it for say a fixed time ,then it must report to user and break out of while true loop.Now with this program it's not changing labels though executing bith threads.```

#!/usr/bin/env python

#This program will attempt to read a line from a file using a GUI

import pygtk
pygtk.require('2.0')
import gtk
import re
import time
from threading import Thread
gtk.gdk.threads_init()


class Nipun:

	
	f=open('/home/nipun/1.txt')
	vars = re.compile('^(\d+\.?\d*)a(\d+\.?\d*)b(\d+\.?\d*)c(\d+\.?\d*)d(.*)')
	
	def __init__(self):
		self.window=gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_title("File read GUI Label")
		self.window.connect("delete_event",self.delete_event)
		self.window.set_border_width(10)
		self.box2=gtk.VBox(False,0)
		self.window.add(self.box2)
		self.button=gtk.Button("Read")
		self.button.connect("clicked",self.callback)
		self.box2.pack_start(self.button,True,True,0)
		self.button.show()
		self.label1=gtk.Label()
		self.label2=gtk.Label()
		self.label3=gtk.Label()
		self.label4=gtk.Label()
		self.label5=gtk.Label("A")
		self.label6=gtk.Label("B")
		self.label7=gtk.Label("C")
		self.label8=gtk.Label("D")
		self.box2.pack_start(self.label5,True,True,0)
		self.box2.pack_start(self.label1,True,True,0)
		self.box2.pack_start(self.label6,True,True,0)
		self.box2.pack_start(self.label2,True,True,0)
		self.box2.pack_start(self.label7,True,True,0)
		self.box2.pack_start(self.label3,True,True,0)
		self.box2.pack_start(self.label8,True,True,0)
		self.box2.pack_start(self.label4,True,True,0)
		self.label1.show()
		self.label2.show()
		self.label3.show()
		self.label4.show()
		self.label5.show()
		self.label6.show()
		self.label7.show()
		self.label8.show()
		self.box2.show()
		self.window.show()
				

	def delete_event(self,widget,event,data=None):
		print "Delete event has occcured"
		gtk.main_quit()
		return False


	def callback(self,button):
		while True:
			self.thread_1()
			self.thread_2()
	def thread_1(self):
		 Thread(target=self.display).start()
	def thread_2(self):
		Thread(target=self.print_val).start()
	def print_val(self):
		print"nipun"
	def display(self):
		print"/n nipun batra"
		s=hello.f.readline()
		m = re.search(hello.vars, s) # Run the regexp on the packet
		var1 = m.group(1) # take out the values
		var2 = m.group(2)
		var3 = m.group(3)
		var4 = m.group(4)
		self.label1.set_text(var1)
		self.label2.set_text(var2)
		self.label3.set_text(var3)
		self.label4.set_text(var4)
		

	def main(self):
		gtk.main()
if __name__=="__main__":
		hello=Nipun()
		hello.main()
	

		
	

```

---

### Post by nipunreddevil on 2009-09-05
Well is there any way to dynamically update label/text entry.My program seems to get blocked and text entry displays only after exception is raised.Will stopping a thread work ,seems like a probable solution to me.

---

