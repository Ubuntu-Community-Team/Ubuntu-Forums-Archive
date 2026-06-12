---
title: "Python: Command Line Commands that Block the Command Line"
date: 2007-10-06
forum: Programming Talk
---

### Post by moephan on 2007-10-06
Hello,

I am trying to write a script to make it easier for me to manage some RoR programming. 

I'd like to use popen4 to issue the command to start the default development web server. The way you do this on the command line is to simply type:
```

$:ruby script./server

```

So I'd like write in my python script:
```

put, get = os.popen4('ruby script/server')
mesg = get.readline()

```

This starts the server, but the server blocks the command line until you hit cntrl-c to stop it. As a result get.readline() never returns and the script hangs. While the processes is running it is writing useful information to the terminal that I would like to read, 

I hope I explained myself clearly enough. I'm guessing there is a standard pattern that I can apply to work around this, but I can't find a reference to it anywhere on the web. I've tried stuff like using the spawn methods, and such, but encountered various difficulties. 

Thanks.

Cheers, Rick

---

### Post by Acglaphotis on 2007-10-06
try this:

```

put, get = os.popen4('ruby script/server &')
mesg = get.readline()

```

---

### Post by moephan on 2007-10-06
Thanks for the tip, but that didn't seem to work. The program still blocks on the readline() call.

What does the ampersand do?

Any other tips? Should I be using one of the spawn methods?

Thanks.

Cheers, Rick

---

### Post by slavik on 2007-10-06
ampersand puts the task into the background (dies as soon as the shell/terminal is killed)

it blocks on getline because getline uses buffered input and is in the blocking I/O class/type. you probably want to do non-blocking I/O ...

---

### Post by moephan on 2007-10-06
Could anyone suggest where I could find some sample code to learn how to do this in a non-blocking manner? I'm having no luck with Google, and I'm not understanding how to do this from the python docs.

Thanks.

Cheers, Rick

---

### Post by Unterseeboot_234 on 2007-10-07
Hello, python noobie here, but I'm totally in awe of the language. Check out O'Reilly -- "Programming Python, ed. 3", pp. 116-120. You do have access to the running of the Shell.  Unix-flavor python waits for the python script to finish execution before considering the Shell's next move.

The pages mentioned from that book illustrate short scripts to evaluate environmental and shell vars. Just my $.02 worth.

---

### Post by cwaldbieser on 2007-10-07
```

#!/usr/bin/python

from subprocess import Popen, PIPE
import Queue
import threading
import time

run_flag = True
q = Queue.Queue(100)

def read_q():
    p = Popen("ruby script/server", shell=True, stdout=PIPE)
    while run_flag:
        data = p.stdout.readline()
        q.put(data)
        if p.returncode != None:
            break

t = threading.Thread(target=read_q)
t.start()

for n in range(30):
    try:
        data = q.get_nowait()
    except Queue.Empty:
        print "No data"
        time.sleep(1)
        continue
    print data,
    if not t.isAlive():
        break
run_flag = False
t.join()

```

This is just a basic idea.  The worker thread keeps trying to read lines from your process, and it may block if no data is available.  When it can grab a line, it will add it to the global queue.
The main thread tries to read data from the queue, but if it doesn't find any, it could do something else in the meantime.

---

### Post by moephan on 2007-10-07
Nice! I've gotten this working using this pattern. Thanks so much.

Cheers, Rick

---

### Post by Tuna-Fish on 2007-10-07
I got just a small gripe about the solution: the queue is way too short. On any demanding input (think find . on a ramdrive), the queue will fill up pretty much instantaneously and the pipe will soon follow. The program is a lot more future proof if the queue is either infinitely long, or has a length in the order of 10 000.

---

### Post by moephan on 2007-10-07
How would I extend this pattern to create a GUI for this using Glade?

I've been hammering at this all day, but I just can't figure out how to get the threads set up so they communicate properly with the main thread. Either I end up blocking the UI, or the threads that read from the queue never communicate with the main thread. 

Hope that made sense. Again, I'm guessing  their is a canonical way to do this, but I can't seem to find it anywhere.

Here's my broken code so far:
```

#!/usr/bin/env python

try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
  	from subprocess import Popen, PIPE
	import Queue
	import threading
	import time

except:
	sys.exit(1)

class window1:
	def read_q(self):
    		p = Popen("ruby /home/rick/nutrition/script/server", shell=True, stdout=PIPE)
    		while self.run_flag:
        		data = p.stdout.readline()
        		self.q.put(data)
        		if p.returncode != None:
            			break

	def __init__(self):
		self.run_flag = True
	        widgetTree = gtk.glade.XML("rails_admin.glade") 
		widgetTree.get_widget("window1").connect("destroy", gtk.main_quit)
		widgetTree.get_widget("run_button").connect("clicked", self.start_rails)
		widgetTree.get_widget("window1").show()
		self.text_buff = widgetTree.get_widget("textview1").get_buffer()
		self.text_buff.insert_at_cursor("starting up")
		self.q = Queue.Queue(100)
		self.t = threading.Thread(target=self.read_q)

	
	def start_rails(self, widget, data=None):
		self.text_buff.insert_at_cursor("starting rails")
		self.t.start()
		while True:
			try:
        			data = self.q.get_nowait()
			except Queue.Empty:
        			print "no data"
        			self.text_buff.insert_at_cursor("no data")
        			gtk.main_iteration(block=True)
        			time.sleep(1)
        			continue
    			print data
    			self.text_buff.insert_at_cursor(data)
    			if not self.t.isAlive():
        			break
		self.run_flag = False
		self.t.join()
		
if __name__ == "__main__":
	window1()
	gtk.main()

```

When I run this, the start button stays depressed, and the output prints out on the command line, but doesn't get added to the textview.

TIA

Cheers, Rick

---

### Post by cwaldbieser on 2007-10-07
> **Tuna-Fish said:**
> I got just a small gripe about the solution: the queue is way too short. On any demanding input (think find . on a ramdrive), the queue will fill up pretty much instantaneously and the pipe will soon follow. The program is a lot more future proof if the queue is either infinitely long, or has a length in the order of 10 000.
It was just a sample to give a basic idea.  However, I am not entirely sure that the size of the queue makes much difference.  If the queue fills up, the put(...)  method will block until a slot frees up.  So as soon as the main program consumes a line, the thread should be able to put the next line.  I think you would have to probably experiment with different queue sizes to know if the overall performance would be affected.

One thing that I would probably do would be to subclass threading.Thread rather than use so many global variables, though.

---

### Post by cwaldbieser on 2007-10-07
I am not really familiar with glade/GTK programming, so I can't give you a sample.  I am guessing that the method, "start_rails(...)" is an event handler for your button?  The reason that the button would stay depressed is that your event handler is in an infinite loop.

With some GUI toolkits, there is sometimes a method like "DoEvents(...)" that suspends the even handler at that point and lets the GUI process events.  With other toolkits, you might have to have your event handler activate a thread, not to fill a queue, but instead to write to the end of the log window.  

Some GUI toolkits aren't too happy about letting you access widgets from threads other than the main event loop.  In Tkinter, for example, the after(...) method is provided to allow asynchronous tasks to be handled during the normal event loop.  A contrived example would be something like:

```

class MyWidget(Frame):
    def __init__(self, master):
        Frame.__init__(self, master)
        self.create_widgets() #Not defined in example; creates buttons, etc.
        self.run_flag = False
    #Event handler
    def start_animation(self):
        self.run_flag = True
        self.after(1000, self.update_animation) #Run in 1 second.
    def update_animation(self):
        if not self.run_flag:
            return
        #Code to update the animation here.
        self.after(1000, self.update_animation) #Run again in 1 second
    #Event handler
    def stop_animation(self):
        self.run_flag = False

```
When the start_animation(...) event handler is triggered, it calls MyWidget's after(...) method (inherited from Frame-- all Tk widgets have this method).  The after(...) method schedules the bound method, self.update_animation(...), to be run 1 second in the future during the main Tk event loop.  When the code is run, it reschedules to run again a second in the future, unless the run_flag has been set to False.  In this fashion, all the interaction with Tk widgets is happening on the main thread.

I am guessing Glade/GTK falls into one of these patterns.

---

### Post by moephan on 2007-10-08
Ouch. Turns out I was wrong, and that my original problem was not solved. My program is still not getting any of the info from the server script. The output is printing out into the shell that I am using to invoke the script, but my app never gets a chance to process the output. 

I tested it with a few other apps. Apps like "ls" that return immediately to the command line, work. Interactive apps, like "ftp" don't work. I studied the code in the subprocess module, but I'm still not grocking it. What am I missing?

TIA

Cheers, Rick

---

### Post by moephan on 2007-10-08
> **cwaldbieser said:**
> I am guessing Glade/GTK falls into one of these patterns.

Thanks for the info. Based on this I was able to track down this pattern:

```

     while gtk.events_pending():
          gtk.main_iteration(block=True)

```

Cheers, Rick

---

### Post by cwaldbieser on 2007-10-08
I found the following link that may help you:
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52296]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52296")

---

