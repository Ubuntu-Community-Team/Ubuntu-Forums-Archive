---
title: "pygtk threading and webkit/gtkmozembed"
date: 2008-07-16
forum: Programming Talk
---

### Post by cxl on 2008-07-16
I want to embed a browser inside of a gui in order to play flash video clips (essentially, youtube videos) using python. I'm using pygtk to create the window and adding the browser inside, connecting appropriate listeners, etc. This works fine with a basic program, but when I add gtk threading, even though the clip will load and I can see the initial frame, it won't play. Also, the delete-signal will no longer emit when I try to close the window using the corner 'x'.

```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

import webkit

class player:
    def __init__(self):
        self.win=gtk.Window()
        self.win.connect("delete-event", self.delete_event)
        browser=webkit.WebView()
        browser.open("http://youtube.com/v/lUjDq67nBCA&autoplay=1")
#        browser=gtkmozembed.MozEmbed()
#        browser.load_url("http://youtube.com/v/RSsJ19sy3JI&autoplay=1")
        self.win.add(browser)
        browser.show()
        self.win.show()

    def delete_event(self, widget, data=None):
        print "delete signal"
        gtk.main_quit()

if __name__=="__main__":
    p=player()
    gtk.gdk.threads_init()
    gtk.main()

```

If you could give me some pointers, I'd really appreciate it.

(Also. If you comment out the gtk.gdk.threads_init(), why does closing the window emit an invalid unclassed pointer warning?)

---

### Post by moberry on 2008-07-16
Although I have not done this in python.. In C using GTK and thread enabled programs, you have to: 

a. run all gtk code from the same thread gtk.main was launched in
b. surround all your GTK code with gdk_threads_enter()/leave()

try that approach. Im assumming python gtk bindings are objects in python with C bindings considering how well python and C integrate.

I dont know if python has that same stipulation as it does in C

---

### Post by delcio_gomes on 2008-12-09
I have this exact problem... did you find the solution?
Thanks in advance.

---

### Post by moberry on 2008-12-09
Do what my previous post says, either have ALL your gui code in the thread gtk_main is in. Or surround any blocks of gtk calls with gdk_threads_enter() and gdk_threads_leave().

---

### Post by delcio_gomes on 2008-12-09
I am sorry, part of this issue is between the monitor and the chair and I am missing something obvious in your tip due to my lack of experience in sw development. ;)

I tried this but the problem is still here (I am going to start studying C/C++, it seem that my life will be simpler):

import pygtk
pygtk.require('2.0')
import gtk

import gtkmozembed
import gobject

gtk.gdk.threads_enter()
win=gtk.Window()
gtk.gdk.threads_leave()
browser=gtkmozembed.MozEmbed()
gobject.idle_add(browser.load_url,"http://youtube.com/v/Mue__7EgbtE&autoplay=1")
gtk.gdk.threads_enter()
win.add(browser)
browser.show()
win.show()

gobject.threads_init()
gtk.gdk.threads_init()
gtk.main()

---

### Post by moberry on 2008-12-09
You don't seem to be running any threads, What happens when your app runs?

---

### Post by delcio_gomes on 2008-12-09
It just freezes the application, showing only until the first frame of the flash player buffering from youtube.
My goal is to play several flash files with a different sleep interval between each other to load a new one.

I started looking at several possibilities.
This way I can see the flash animation:
-------------------------------------------------------------------
import pygtk
pygtk.require('2.0')
import gtk
import gtkmozembed
import gobject
import threading
import time

class video(threading.Thread):
	
	def __init__(self, url):
		threading.Thread.__init__(self)
		self.url_to_load = url
		self.win=gtk.Window()
		self.browser=gtkmozembed.MozEmbed()
		self.browser.load_url(self.url_to_load)
		self.win.add(self.browser)
		self.browser.show()
		self.win.show()
		gtk.main()
		
	def run(self):
		pass
		

play = video("http://youtube.com/v/Mue__7EgbtE&autoplay=1")
play.start()
print "Wait 5 seconds!"
#time.sleep(5.00)
print "Ok, go ahead."
-------------------------------------------------------------------
The problem is that won't use the thread, to use it I will not to use run().


Other possibility is:
-------------------------------------------------------------------
import pygtk
pygtk.require('2.0')
import gtk
import gtkmozembed
import gobject
import threading
import time

class video(threading.Thread):
	
	def __init__(self, url):
		threading.Thread.__init__(self)
		self.url_to_load = url
		
		
	def run(self):
		self.win=gtk.Window()
		self.browser=gtkmozembed.MozEmbed()
		self.browser.load_url(self.url_to_load)
		self.win.add(self.browser)
		self.browser.show()
		self.win.show()
		gtk.main()		

play = video("http://youtube.com/v/Mue__7EgbtE&autoplay=1")
play.start()
print "Wait 10 seconds!"
time.sleep(10.00)
print "Ok, go ahead."
-------------------------------------------------------------------
It works if I use a sleep time for 5 seconds. But if I increase to 10 it will show me the flash animation but won't print "Ok, go ahead". It feels that as soon as it enters in the gtk.main() it will stay there.
The behavior is the same for this using gtk.gdk.threads_enter()/leave():
-------------------------------------------------------------------
import pygtk
pygtk.require('2.0')
import gtk
import gtkmozembed
import gobject
import threading
import time

class video(threading.Thread):
	
	def __init__(self, url):
		threading.Thread.__init__(self)
		self.url_to_load = url
		
		
	def run(self):
		gtk.gdk.threads_enter()
		self.win=gtk.Window()
		gtk.gdk.threads_leave()
		self.browser=gtkmozembed.MozEmbed()
		self.browser.load_url(self.url_to_load)
		self.win.add(self.browser)
		self.browser.show()
		self.win.show()
		gtk.gdk.threads_enter()
		gtk.main()		
		gtk.gdk.threads_leave()

play = video("http://youtube.com/v/Mue__7EgbtE&autoplay=1")
play.start()
print "Wait 10 seconds!"
time.sleep(10.00)
print "Ok, go ahead."
-------------------------------------------------------------------

Yet another possibility is adding gtk.gdk.threads_enter():

-------------------------------------------------------------------
import pygtk
pygtk.require('2.0')
import gtk
import gtkmozembed
import gobject
import threading
import time

class video(threading.Thread):
	
	def __init__(self, url):
		threading.Thread.__init__(self)
		self.url_to_load = url
		
		
	def run(self):
		gtk.gdk.threads_enter()
		self.win=gtk.Window()
		gtk.gdk.threads_leave()
		self.browser=gtkmozembed.MozEmbed()
		self.browser.load_url(self.url_to_load)
		self.win.add(self.browser)
		self.browser.show()
		self.win.show()
		gtk.gdk.threads_enter()
		gtk.gdk.threads_init()
		gtk.main()		
		gtk.gdk.threads_leave()

play = video("http://youtube.com/v/Mue__7EgbtE&autoplay=1")
play.start()
print "Wait 10 seconds!"
time.sleep(10.00)
print "Ok, go ahead."
-------------------------------------------------------------------

The result is:
1) Window appears with white background
2) Prints output messages:
    location: /usr/lib/xulrunner-1.9.0.4/libxpcom.so 
    before 3
    Wait 10 seconds!
    Ok, go ahead.
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
    ** Message: GetValue variable 1 (1)
    ** Message: GetValue variable 2 (2)
3) Then finally opens he URL, where I can see the the first frame of the flash player buffering from youtube, than it freezes the flash content.

Note: if I ask for a page without flash content it will work just fine. I open Google, search for YouTube and then as soon as I click the link it will load all the standard content of the first page from YouTube as as soon as it starts loading flash content it will freeze all the navigation and mouse icon.

I ran out of ideas...

---

### Post by moberry on 2008-12-09
It smells like a thread problem, they can be tricky to solve because you don't know the order in which things are running. I would try this though; make sure calls to the browser are enclosed in gtk.gdk.threads_enter/leave. I do know know thread safe that library is or isn't. But it's worth a shot.

---

### Post by moberry on 2008-12-09
Also, just spotted this as well. Try running your gtk main loop outside of the class. Or rather, in the "main" thread. Same place your are setting up your instances of Video. I'm betting that mozilla needs gtk_main to be running for it to works its magic.

---

### Post by delcio_gomes on 2008-12-09
Dear friend moberry, I removed my previous flash player, installed Gnash ([http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)), cleaned all temporary files and closed all intances of firefox and all my code is working beeautifully with threading, flash and happiness! Life is good again. :D
Once again thank you a lot for your help and fast replies.

---

