---
title: "Gedit like file opening with python"
date: 2011-08-16
forum: Programming Talk
---

### Post by OpenFish on 2011-08-16
i have been working on a little python program for a few days now and it is starting to take shape and is starting to be useful, i have just implemented save and open with the nice pygtk dialogs

i would like to be able to open files (command line or double click) and display the relivent data in my programs  tabs in the same way that gedit would do but with text.

i would like to be able to run the program 
[PHP]$myprogram --some_option filename[/PHP]
while another instance of the program is already running and have the existing window add a tab with the display for the new file, as gedit dose.

eventually i would like it to be smart enough to have a separate window per desktop, (like gedit) but this is low on my priorities at the moment.

i have had a good look at the threads and multiprocessing modules and i have been wondering if a manager would manage this.

i asume gedit connects to gnome and uses some sort of clever gnome manager. i assume this is what i should use but i cant find the relevant docs

any help/program lay out advice would be very welcome

thank you all in advance

---

### Post by OpenFish on 2011-08-22
Firstly I would like to say that I think there is a all in one way possibly?
In the absence of this the multiprocessing module can be combined with a very modified version of []("http://old.nabble.com/Wnck:-Switching-to-and-reporting-current-workspace-(desktop)-number.-td27806488.html")
I haven't studied the post in detail but it didn't seem to work? a heavily reduced version of mine is hear 
[PHP]import gtk
import wnck
import time

def flush_events():
    while gtk.events_pending():
        gtk.main_iteration()

if __name__ == '__main__':
	# Get screen
	screen = wnck.screen_get_default()

	flush_events()

	ws  = screen.get_active_workspace()
	ws_num = ws.get_number()

	print "current workspace num=", ws_num[/PHP]
despite my modifications i would like to thank the author for pointing me in the right direction. and saving lots of time!
I was working on this project quite intensively but i am not currently but hope to be soon. i hope to post the out line of my loading system once glued together.

---

### Post by hakermania on 2011-08-23
Because I had the same issue with you once, in C++ though, I sent a DBUS message of the path of the file to the already running instance :)
The application you see on my signature can take 'wallch albums'. If you open one and the process is already running then it will import the albums at once!
I have the program listening to a dbus chanell so as to communicate well with the other instances that send it DBUS messages.
I am pretty sure that python can support dbus.

---

### Post by OpenFish on 2011-08-23
Thank you very much. This sounds good i will go have a look at python docs and your code once i have a little time. Do you address the issue of the different work spaces? In you program. Although wnck and dbus would be a way to achieve this.

---

### Post by hakermania on 2011-08-23
> **OpenFish said:**
> Thank you very much. This sounds good i will go have a look at python docs and your code once i have a little time. Do you address the issue of the different work spaces? In you program. Although wnck and dbus would be a way to achieve this.
No, my program is so made that you cannot have any more than one instances globally, not per desktop :/

But I think this can be solved, provided that you can somehow take the number of the desktop your process is on.

Ok, so, let's say you have an instance of the program on desktop No2.
So, you run another instance from desktop No1, you detect another instance is running and you send message to it, saying that you are going to run to Desktop No1, the already running process checks on which desktop it runs, and because it is No2, it sends signal 'OK' to the process which is going to run to Desktop No1, so the process starts normally to desktop no1.
Otherwise, if there's a process at the desktop No2, and the user runs another instance in the same desktop, there will be the same communication between the programs as described above, with the difference that the already running process will send signal 'NO OK' (or similar, hehe) to the process that is going to start, and, as a result, if the process that was going to start had arguments (a file to open), these will be sent to the already running process for opening, otherwise, if there aren't any arguments, just focus to the already running process opening a New-Tab, ready for writing something.

The only problem you have to solve is 'how to take current desktop number'

EDIT: oh, have you managed to take the current workspace? Nice! No problem then, just learn how to communicate through DBUS in python !

---

### Post by OpenFish on 2011-09-03
I've written a little proof of concept
for gnome I doubt it will work with Compiz
The program dose not do any thing but shows how terminals in different workspaces can find windows and connect to them.
it actually checks if the app is already running then connects to the app or starts off. if the app is already running then the new program asks it to find windows in the active work space and then changes them.

It needs a lot of work but I think it is nearly good enough to be merged in to my existing program before this fine tuning is done. As I have not found any thing like this in python so fare I am setting it free so hopefully someone will find it use full.

this is very useful and just other ppls stuff glued together so please use it if u want it.

any feed back will be very gratefully received

[PHP]import gtk
import gobject
import sys, os
import wnck
import dbus
import dbus.service
from dbus.mainloop.glib import DBusGMainLoop
DBusGMainLoop(set_as_default=True)

def flush_events():
	while gtk.events_pending():
		gtk.main_iteration()
def curtscren():
	screen = wnck.screen_get_default()
	flush_events()
	ws  = screen.get_active_workspace()
	ws_num = ws.get_number()
	return ws_num
def winscren(win):
	screen = wnck.screen_get_default()
	flush_events()
	ws  = screen.get_active_workspace()
	window = wnck.window_get(int('windows.py'))
	return window.is_visible_on_workspace(ws)
	ws_num = ws.get_number()
	return ws_num
class MyDBusService(dbus.service.Object):
	def __init__(self):
		self.wins = {}
		bus_name = dbus.service.BusName('org.Tester.openup', bus=dbus.SessionBus())
		dbus.service.Object.__init__(self, bus_name, '/org/Tester/openup')

	@dbus.service.method('org.Tester.openup')
	def Connect(self):
		screen = wnck.screen_get_default()
		flush_events()
		cr=curtscren()
		ws  = screen.get_active_workspace()
		pid = os.getpid()
		for window in screen.get_windows():
			if window.get_workspace() == ws:
				if window.get_pid() == pid:
					self.wins[window.get_name()].lab.set_text('Changed')
					return True
		# add new window: return True
		return False        
	def addWindow(self,win):
		self.wins[win.get_title()]=win

class Window():
	def __init__(self):
		windowDis = gtk.Window(gtk.WINDOW_TOPLEVEL)
		windowDis.connect("destroy", gtk.main_quit)
		self.lab = gtk.Label('Not Set')
		self.opfile=None
		windowDis.add(self.lab)
		windowDis.set_default_size(400, 400)
		self._GuiRefresh = windowDis.show_all
		self.get_title = windowDis.get_title
		self.set_title = windowDis.set_title
		self._GuiRefresh()
	def open_file(self,opfile):
		self.lab.set_text(opfile)
		self.opfile=opfile

	
def Args():
	#just a little bit massivly crued
	args = sys.argv
	nwfile=''
	for arg in args:
		if arg[:1] == '/':
			return arg
	return None
	
	
def main():
	opfile=Args()
	Dbush= MyDBusService()

	Win1 = Window()
	Win2 = Window()
	if opfile :
		Win1.open_file(opfile)
	print 'opened: ' , opfile
	Win1.set_title('GitTest1')
	Win2.set_title('GitTest2')
	Dbush.addWindow(Win1)
	Dbush.addWindow(Win2)
	
if __name__ == "__main__":
	try:
		bus = dbus.SessionBus()
		helloservice = bus.get_object('org.Tester.openup', '/org/Tester/openup')
		con = helloservice.get_dbus_method('Connect', 'org.Tester.openup')
		print con()
	except Exception:
		main()
		gtk.main()[/PHP]

---

