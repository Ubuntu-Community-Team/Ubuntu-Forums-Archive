---
title: "Python - Psutil and mapplotlib"
date: 2012-01-21
forum: Programming Talk
---

### Post by revollie on 2012-01-21
Hi, 

I am currently learning python and have been looking into the psutil module. 

I found some code from a book that I am looking at that plots cpu usage using psutil with matplaotlib. 

I type the code up and sorted any mistakes I found but its still not running. 
I ran it and terminal doesn't give any errors or compile problems. The cursor just flashes. It usually does that when it opens an external window - eg when I was using tkinter. 

Is there any way of finding what going on? I have a feeling that I am missing a module to run the GUI/Graph that it creates. Any ideas?
I'm using Ubuntu 11.something (latest release) - and I am a beginner so I'm not sure how I can provide a list of installed programs/modules etc - so let me know if anyone has ideas

Cheers

Code below:
 ```
import gtk
import gobject

from matplotlib.figure import Figure
from matplotlib.backends.backend_gtkagg \
	import FigureCanvasGTKAgg as FigureCanvas

import time
import psutil as p

def prepare_cpu_usage():
	t = p.cpu_times()
	if hasattr(t, "nice"):
		return[t.user, t.nice, t.system, t.idle]

	else:
		return [t.user, 0,  t.system, t.idle]

def get_cpu_usage():
	global before

	now = prepare_cpu_usage()

	delta = [now[i]-before[i] for i in range(len(now))]
	total = sum(delta)
	before = now
	return [(100.0*dt)/total for dt in delta]

def update_draw(*args):
	global i
	result = get_cpu_usage()

	user.append(result[0])
	nice.append(result[1])
	sys.append(result[2])
	idle.append(result[3])
	
	l_user.set_data(range(len(user)), user)
	l_nice.set_data(range(len(nice)), nice)
	l_sys.set_data(range(len(sys)), sys)
	l_idle.set_data(range(len(idle)), idle)

	fig.canvas.draw()

	i += 1
	if i > 30:
		return False
	else:
		time.sleep(1)
		
	return True

	i = 0
	before = prepare_cpu_usage()
	win = gtk.Window()
	win.connect("destroy", gtk.main_quit)
	win.set_default_size(600, 400)
	win.set_title("30 Seconds of CPU Usage Updated in real-time")

	fig = Figure()
	ax = fig.add_subplot(111)

	ax.set_xlim(0, 30)
	ax.set_ylim([0, 100])

	ax.set_autoscale_on(False)

	user, nice, sys, idle, = [], [], [], []

	l_user, = ax.plot ([], user, label="User %")
	l_nice, = ax.plot ([], nice, label="Nice %")
	l_sys, = ax.plot([], sys, label="Sys %")
	l_idle, = ax.plot([], idle, label="Idle %")

	ax.legend()
	canvas = FigureCanvas(fig)
	win.add(canvas)

	update_draw()

	gobject.idle_add(update_draw)
	win.show_all()

gtk.main()


```

---

### Post by MadCow108 on 2012-01-21
the code is indented wrong
```


	return True

	i = 0
...
```

move everything below the return True to the lowest indentation level and it should work

---

### Post by revollie on 2012-01-21
Ah something that simple - I didn't notice. 

I now have the following which is giving me errors: 

```
import gtk
import gobject

from matplotlib.figure import Figure
from matplotlib.backends.backend_gtkagg \
	import FigureCanvasGTKAgg as FigureCanvas

import time
import psutil as p

def prepare_cpu_usage():
	t = p.cpu_times()
	if hasattr(t, "nice"):
		return[t.user, t.nice, t.system, t.idle]
	else:
		return [t.user, 0,  t.system, t.idle]

def get_cpu_usage():
	global before

	now = prepare_cpu_usage()

	delta = [now[i]-before[i] for i in range(len(now))]
	total = sum(delta)
	before = now
	return [(100.0*dt)/total for dt in delta]

def update_draw(*args):
	global i
	result = get_cpu_usage()

	user.append(result[0])
	nice.append(result[1])
	sys.append(result[2])
	idle.append(result[3])
	
	l_user.set_data(range(len(user)), user)
	l_nice.set_data(range(len(nice)), nice)
	l_sys.set_data(range(len(sys)), sys)
	l_idle.set_data(range(len(idle)), idle)

	fig.canvas.draw()

	i += 1
	if i > 30:
		return False
	else:
		time.sleep(1)
		
	return True
	i = 0

before = prepare_cpu_usage()
win = gtk.Window()
win.connect("destroy", gtk.main_quit)
win.set_default_size(600, 400)
win.set_title("30 Seconds of CPU Usage Updated in real-time")

fig = Figure()
ax = fig.add_subplot(111)

ax.set_xlim(0, 30)
ax.set_ylim([0, 100])

ax.set_autoscale_on(False)

user, nice, sys, idle, = [], [], [], []

l_user, = ax.plot ([], user, label="User %")
l_nice, = ax.plot ([], nice, label="Nice %")
l_sys, = ax.plot([], sys, label="Sys %")
l_idle, = ax.plot([], idle, label="Idle %")

ax.legend()
canvas = FigureCanvas(fig)
win.add(canvas)

update_draw()

gobject.idle_add(update_draw)
win.show_all()

gtk.main()


```


When run I get the following from terminal:

```
oliver@Oliver-VirtualBox:~/Documents/Python$ python psutil.py
Traceback (most recent call last):
  File "psutil.py", line 9, in <module>
    import psutil as p
  File "/home/oliver/Documents/Python/psutil.py", line 53, in <module>
    before = prepare_cpu_usage()
  File "/home/oliver/Documents/Python/psutil.py", line 12, in prepare_cpu_usage
    t = p.cpu_times()
AttributeError: 'module' object has no attribute 'cpu_times'

```

Going to go through and take another look to make sure I have the rest input correctly

Thanks

---

### Post by MadCow108 on 2012-01-21
you apparently have a file named psutil.py in the folder you are running the script:
```
/home/oliver/Documents/Python/psutil.py
```

this will get prefered to the real psutil
rename the file or execute the script in a different directory.

---

### Post by revollie on 2012-01-21
Face palm right there - again didn't realise something that simple could cause problems. Renamed (to scotch.py...as they were drinking on the movie...)

anyhow - amazing!

I had to change the indentation again slightly - was getting - unsupported operand type(s) for += - but it was just I left the i = 0 indented when it needed to be lowest. 

Its now working quite nicely. 

Think after this its clear I need to pop back to the basics for a while but appreciate the help. 

Cheers!

---

