---
title: "python class"
date: 2007-12-28
forum: Programming Talk
---

### Post by bradleyd on 2007-12-28
Hello,
I am trying to return a value from another class.
I have one class that is the application, and another class that is timer thread. The timer class is doing some stuff at intervals and populates a variable with a list. I need that list to be callable from the other class, so I can do work against it. Or If I can call a function from a different class that would work too.
Thanks for your time,
Brad

---

### Post by Martin Witte on 2007-12-28
I' not sure i get it, but if I'm correct you want to do something like:
[PHP]#!/usr/bin/env python
class Two(object):
    def __init__(self):
        self.somevar = list()

    def addstufftolist(self, stuff):
        self.somevar.append(stuff)

class One(object):
    def __init__(self):
        two = Two()
        two.addstufftolist('stuff')
        self.somevar = two.somevar

if __name__ == '__main__':
    one = One()
    print one.somevar

[/PHP]

---

### Post by bradleyd on 2007-12-28
thanks for the reply.
I already tried what you posted but I get > TypeError: __init__() takes exactly 4 arguments (1 given)
Here is the beginnig of the first class:
```
class TaskBarApp(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, -1, title, size = (1, 1),
			style=wx.FRAME_NO_TASKBAR|wx.NO_FULL_REPAINT_ON_RESIZE)
```

Here is the second class:
```
class Timer(threading.Thread):
	def __init__(self, seconds):
		
		self.runTime = seconds
		threading.Thread.__init__(self)
	def run(self):
		d = TaskBarApp()
		while True:
			time.sleep(self.runTime)
			response = urllib2.urlopen('https://www.testbox.com/um/request-message-count?partner=mnvmwitest&password=8630&subscriberID=30111')
			html = response.read()
			#print html
			ts = html.split()
			if ts[3] > '0':
				d.test()
			time.sleep(4)
```
I am basically trying to get a taskbar icon to blink any time there are messages. I am trying to have it check every ten minutes, but for the example I am doing it every 4 seconds.
Thanks again

---

### Post by Martin Witte on 2007-12-28
in method run of class Timer you create a TaskBarApp object without arguments. In the __init__ method of the TaskBarApp you require 3 arguments, hence the error

---

### Post by bradleyd on 2007-12-28
I know, I need to call it with fake args, I just need to call the function.
Thanks again,
brad

---

