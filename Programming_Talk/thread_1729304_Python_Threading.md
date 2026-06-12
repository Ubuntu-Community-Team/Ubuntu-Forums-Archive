---
title: "Python Threading"
date: 2011-04-14
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-04-14
Hello there,

i am working on an applet for Cairo-Dock (working with the provided API). The applet must perform a repetitive task every minute while being available for callbacks. So i looked into threading for python and found [this nice tutorial]("http://en.wikibooks.org/wiki/Python_Programming/Threading").
Now my applet is OO programming. This means the thread (which should count down before running processes of the applet) should be initialised from a process of the applet. I tried that and made the function to be run as a thread a process of applet, or a global function or another object, but in each case it failed.
I think i am doing something wrong, can anyone guide me?

*To sum up:*
> [LIST]
[*]The applet should run and perform some tasks
[*]A loop should start (say every minute)
[*]Meanwhile the applet should be able to perform some more tasks
[*]When the loop ends the applet should perform special tasks and the loop should start again.
[*]... and so on ect.
[/LIST]

Thanks
Benjamin

---

### Post by wmcbrine on 2011-04-14
Post your code...

---

### Post by jesuisbenjamin on 2011-04-15
[Full Edit: Found better code, but not perfect]

I made some test first, using threading.Timer() and it worked fine:

[PHP]#!/usr/bin/python

import time
import threading

def timer(sometime, obj):
print "...beginning timer"
t = threading.Timer(sometime, timer, [sometime, obj])
t.start()
obj.poke()

class thing(object):
def __init__(self):
self.time = 5

def run_timer(self):
timer(self.time, self)

def poke(self):
print "ouch!"

if __name__ == '__main__':
    o = thing()
    o.run_timer()[/PHP]

But when i apply that to my Applet the threading.Timer() seems to run only once... :(

[PHP]#!/usr/bin/python

# This is a part of the external applets for Cairo-Dock
# Copyright : (C) 2011 by Benjamin
# E-mail : jesuisbenjamin@...
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# http://www.gnu.org/licenses/licenses.html#GPL
#
# This program depends on fbcmd, a command line interface (CLI) for facebook.
# http://fbcmd.dtompkins.com/

####################
### dependancies ###
####################

from CDApplet import CDApplet
import os
import threading
import time

####################
### Thread Class ###
####################

def countdown(sometime, app):
    print "...countdown started"
    t = threading.Timer(sometime, countdown, [sometime, app])
    t.start()
    app.read_fb()

####################
### Applet class ###
####################
class Applet(CDApplet):
    def __init__(self):
        # define internal variables:
        # counter to display
        self.counter = 1
        # data retrieved from faceBook with fbcmd
        self.fb = {}
        # timer before refreshing data
        self.timer = 1
        # call high-level init
        CDApplet.__init__(self)
        
    ##### private methods #####
    def read_fb(self):
        print "...reading data from faceBook"
        # run the "fbcmd NOTIFY" command and return and parse result in "fblist" list
        fblist = os.popen("fbcmd NOTIFY").readlines()
        # omit friend request details and feed result into a the "self.fb" dictionary
        for i in fblist:
            ii = i.split()
            try:
                number = int(ii[-1])
                self.fb[ii[0]] = number
            except:
                pass
        print self.fb
        
    def get_config(self,keyfile):
        print "...getting user-configuration"
        # get user configuration:
        ## which notifications should be added to counter?
        self.config['MESSAGES_UNREAD']     = keyfile.getboolean('Configuration', 'MESSAGES_UNREAD')
        self.config['POKES']         = keyfile.getboolean('Configuration', 'POKES')
        self.config['SHARES_UNREAD']         = keyfile.getboolean('Configuration', 'SHARES_UNREAD')
        self.config['FRIEND_REQUESTS']         = keyfile.getboolean('Configuration', 'FRIEND_REQUESTS')
        self.config['GROUP_INVITES']         = keyfile.getboolean('Configuration', 'GROUP_INVITES')
        self.config['EVENT_INVITES']         = keyfile.getboolean('Configuration', 'EVENT_INVITES')
        ## how often should notifications be checked?
        self.config['REFRESH']                 = keyfile.getint('Configuration', 'REFRESH')
        self.timer = self.config['REFRESH'] * 6
        ## when should user be notified?
        self.config['ATTENTION_WHEN']            = keyfile.get('Configuration', 'ATTENTION_WHEN')
        print self.config
            
    def begin(self):
        # retrieve data from faceBook
        self.read_fb()
        self.set_counter()
        print "...summoning countdown"
        countdown(5, self)
            
    def set_counter(self):
        print "...setting counter"
        # counting the current value for counter
        new_counter = 0
        for i in self.config:
            # omitting non-boolean values from the config
            if self.config[i].__class__ != bool:
                pass
            # omitting disabled notifications
            elif self.config[i] == False:
                pass
            # remains enabled notifications
            # adding their value to current value of counter
            else:
                new_counter += self.fb[i]
        # record difference between current and prior counter
        diff = self.counter - new_counter
        # set counter to current value if != 0
        self.counter = new_counter
        if self.counter != 0:
            self.icon.SetQuickInfo(format(self.counter))
        else:
            pass
        # check if attention is needed
        att = self.config["ATTENTION_WHEN"]
        if att == "always" and self.counter != 0:
            self.icon.DemandsAttention(True,"bounce")
            time.sleep(2)
            self.icon.DemandsAttention(False,"bounce")
        elif att == "different" and diff != 0:
            self.icon.Animate("bounce",4)
        elif att == "superior" and diff > 0:
            self.icon.Animate("bounce",4)
        else:
            pass
        ##### callbacks #####
    def on_click(self, iState):
        print "You have", self.counter, "unread message(s) on your faceBook account."
############
### main ###
############
if __name__ == '__main__':
    Applet().run()[/PHP]

I don't know what the issue is here :confused:

Cheers,
Benjamin

---

### Post by jesuisbenjamin on 2011-04-16
I worked on it and looked into documentation, invariably, as I make a test application it works fine, but when I apply it to the Applet it doesn't... :(
I have changed the code to adding a "t" attribute, which is an instance of threading.Timer() this way i'll be able to t.start() or t.stop() anytime.
Also i made the loop between three functions. The countdown() function goes past the t.start() and prints "...thread initiated". Then i am not sure whether t really is running, but the target function reached() is not initiated, so that would mean t.start() fails: but why don't i get an error message then? Any help is welcome :) Cheers!

Here is the [PHP]
#!/usr/bin/python

# This is a part of the external applets for Cairo-Dock
# Copyright : (C) 2011 by Benjamin
# E-mail : jesuisbenjamin@...
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# http://www.gnu.org/licenses/licenses.html#GPL
#
# This program depends on fbcmd, a command line interface (CLI) for facebook.
# http://fbcmd.dtompkins.com/ 

####################
### dependancies ###
####################

from CDApplet import CDApplet
import os
import threading
import time


####################
### Applet class ###
####################
class Applet(CDApplet):
	def __init__(self):
		# define internal variables:
		# counter to display
		self.counter = 1
		# data retrieved from faceBook with fbcmd
		self.fb = {}
		# timer before refreshing data
		self.timer = 5
		# Timer thread
		self.t = threading.Timer(self.timer, self.reached, [])
		# call high-level init
		CDApplet.__init__(self)
		
	##### private methods #####
	def read_fb(self):
		print "...reading data from faceBook"
		# run the "fbcmd NOTIFY" command and return and parse result in "fblist" list
		fblist = os.popen("fbcmd NOTIFY").readlines()
		# omit friend request details and feed result into a the "self.fb" dictionary
		for i in fblist:
			ii = i.split()
			try:
				number = int(ii[-1])
				self.fb[ii[0]] = number
			except:
				pass
		print self.fb
		 
	def get_config(self,keyfile):
		print "...getting user-configuration"
		# get user configuration:
		## which notifications should be added to counter?
		self.config['MESSAGES_UNREAD'] 	= keyfile.getboolean('Configuration', 'MESSAGES_UNREAD')
		self.config['POKES'] 		= keyfile.getboolean('Configuration', 'POKES')
		self.config['SHARES_UNREAD'] 		= keyfile.getboolean('Configuration', 'SHARES_UNREAD')
		self.config['FRIEND_REQUESTS'] 		= keyfile.getboolean('Configuration', 'FRIEND_REQUESTS')
		self.config['GROUP_INVITES'] 		= keyfile.getboolean('Configuration', 'GROUP_INVITES')
		self.config['EVENT_INVITES'] 		= keyfile.getboolean('Configuration', 'EVENT_INVITES')
		## how often should notifications be checked?
		self.config['REFRESH'] 				= keyfile.getint('Configuration', 'REFRESH')
		self.timer = self.config['REFRESH'] * 6
		## when should user be notified?
		self.config['ATTENTION_WHEN']			= keyfile.get('Configuration', 'ATTENTION_WHEN')
		print self.config
		
	def countdown(self):
		self.t.start()
		print "...initiating thread"
		
	def reached(self):
		print "...thread achieved"
		self.countdown()
		
	def begin(self):
		# retrieve data from faceBook 
		self.read_fb()
		self.set_counter()
		print "...summoning countdown"
		self.countdown()
			
	def set_counter(self):
		print "...setting counter"
		# counting the current value for counter
		new_counter = 0
		for i in self.config:
			# omitting non-boolean values from the config
			if self.config[i].__class__ != bool:
				pass
			# omitting disabled notifications
			elif self.config[i] == False:
				pass
			# remains enabled notifications
			# adding their value to current value of counter
			else:
				new_counter += self.fb[i]
		# record difference between current and prior counter
		diff = self.counter - new_counter
		# set counter to current value if != 0
		self.counter = new_counter
		if self.counter != 0:
			self.icon.SetQuickInfo(format(self.counter))
		else:
			pass
		# check if attention is needed
		att = self.config["ATTENTION_WHEN"]
		if att == "always" and self.counter != 0:
			self.icon.DemandsAttention(True,"bounce")
			time.sleep(2)
			self.icon.DemandsAttention(False,"bounce") 
		elif att == "different" and diff != 0:
			self.icon.Animate("bounce",4)
		elif att == "superior" and diff > 0:
			self.icon.Animate("bounce",4)
		else:
			pass
		##### callbacks #####
	def on_click(self, iState):
		print "You have", self.counter, "unread message(s) on your faceBook account."
############
### main ###
############
if __name__ == '__main__':
	Applet().run()
[/PHP]

---

### Post by jesuisbenjamin on 2011-04-17
OK imma post another time with another update. I've tried to turn it in every way possible, but i didn't find a way to make it work. However i've been able to trace the event when the difficulty occurs: it seems that loading the Applet() instance freezes running threads, which finish only when killing the Applet.
For those who are interested to look into this i've made a dummy Cairo Applet showing this behaviour (start up Cairo with terminal). [You can download this applet from here]("http://dl.free.fr/pxkNEZ5SF").

Here is a copy of the Dummy script:
[PHP]#!/usr/bin/python



####################
### dependancies ###
####################

from CDApplet import CDApplet
import threading
import time


class MakeApplet(threading.Thread):
	def run(self):
		print "...thread 04 making applet!"
		facebook = Applet()
		facebook.run()
		time.sleep(3)
		print "...facebook applet should be initiated!"
		
class MyThread(threading.Thread):
    def run(self):
        print("%s started!" % self.getName())
        time.sleep(3)
        print("%s finished!" % self.getName())

class Applet(CDApplet):
	def __init__(self):
		CDApplet.__init__(self)
	##### private methods #####
		
	def begin(self):
		print "...It's alive!"
		

if __name__ == '__main__':
	thread01 = MyThread(name= "Thread 01")
	thread01.start()
	time.sleep(1)
	thread02 = MyThread(name= "Thread 02")
	thread02.start()
	time.sleep(1)
	thread03 = MyThread(name= "Thread 03")
	thread03.start()
	time.sleep(1)
	thread04 = MakeApplet()
	thread04.start()
[/PHP]

---

### Post by jesuisbenjamin on 2011-04-17
Yes i found my solution! Thanks to [this blog]("http://www.jejik.com/articles/2007/01/python-gstreamer_threading_and_the_main_loop/") and [that documentation]("http://wiki.python.org/moin/DbusExamples").

In short Gobject must allow threading with gobject.threads_init()

---

### Post by cgroza on 2011-04-17
Bravo...

---

