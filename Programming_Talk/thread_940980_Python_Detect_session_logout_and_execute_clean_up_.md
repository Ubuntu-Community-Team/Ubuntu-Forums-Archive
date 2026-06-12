---
title: "Python: Detect session logout and execute clean up code"
date: 2008-10-07
forum: Programming Talk
---

### Post by Sam on 2008-10-07
I have written a small pygtk app that stays resident as a status icon. When the application exits it must clean up some things. It works well when I exit the app, send SIGTERM, send Ctrl-C, but if I logout from Gnome having the app open, it gets killed without clean up. I suspect a SIGKILL being sent to the application, but shouldn't it be a SIGTERM??

Here is an example of what I try to explain. A log file is created in ~/test.log. The correct behaviour on shutdown is to get through the "# do cleanup here" section (ie. writing "Exiting application" to the log file).

```
#!/usr/bin/env python
# -*- coding: UTF-8 -*-

import pygtk
pygtk.require('2.0')
import gtk
import os
import sys
import time
import signal

def write_log(message):
	f = open(os.path.expanduser("~") + "/test.log", 'a')
	f.write(message+"\n")
	f.close()

# SIGTERM handler
def exittermhandler(signum, frame):
	print "SIGTERM detected!"
	write_log("SIGTERM detected!")
	sys.exit(1)
signal.signal(signal.SIGTERM, exittermhandler)

class TestApp:
	def __init__(self):
		print "Opening application"
		write_log("Opening application")

	def destroy(self, widget, data=None):
		print "Destroy signal occurred"
		write_log("Destroy signal occurred")
		gtk.main_quit()

	def main(self):
		self.icon = gtk.status_icon_new_from_stock(gtk.STOCK_HOME)
		self.icon.set_tooltip("Test Application")
		self.icon.connect('activate', self.destroy)

		try:
			gtk.main()

		except (KeyboardInterrupt):
			print "Terminated by user"
			write_log("Terminated by user")

		except (SystemExit):
			print "System Exit"
			write_log("System Exit")

		except:
			raise

		finally:
			print "Exiting application"
			write_log("Exiting application")
			# do cleanup here
			# ...

if __name__ == "__main__":
	test_app = TestApp()
	test_app.main()

```Anybody has a hint ?? This gives me headaches. Thank you in advance.

---

### Post by Sam on 2008-10-09
Bump


Please help me... Googled a lot and found nothing.....

---

### Post by Sam on 2008-10-12
Bump++

---

### Post by Jacks0n on 2008-10-13
Hm you've got me interested now.

I have no idea, but I'll take a guess and say you're likely to detect gnome logging out using [_dbus_]("http://google.com/codesearch?hl=en&lr=&q=lang%3Apython+dbus+logout&sbtn=Search"). An awful hack would be making a script execute when logging out to do the cleanup (in /etc/gdm/PostSession/Default), and delete itself. Gedit's the only application that I know of that's [_capable_]("http://google.com/codesearch?hl=en&q=gedit+logout_mode+show:4F_LK2MoqkM:WAj6wIwwUnE:65A5CxuvL04&sa=N&cd=1&ct=rc&cs_p=http://mirror.arcticnetwork.ca/pub/gentoo/distfiles/gedit-2.14.4.tar.bz2&cs_f=gedit-2.14.4/gedit/dialogs/gedit-close-confirmation-dialog.c") of detecting a session logout.

From what it seems, there's no pythonic way to do it, but if you do find a suitable way I'd love to know.

- Jackson

---

### Post by SeanHodges on 2008-10-13
What comes back in your log when you log out with the program open?

Also, it would be nice to dump the error trace to the log as well...

---

### Post by Sam on 2008-10-19
Sorry for responding late. Thanks for the replies !

> **Jacks0n said:**
> Hm you've got me interested now.

I have no idea, but I'll take a guess and say you're likely to detect gnome logging out using [_dbus_]("http://google.com/codesearch?hl=en&lr=&q=lang%3Apython+dbus+logout&sbtn=Search"). An awful hack would be making a script execute when logging out to do the cleanup (in /etc/gdm/PostSession/Default), and delete itself. Gedit's the only application that I know of that's [_capable_]("http://google.com/codesearch?hl=en&q=gedit+logout_mode+show:4F_LK2MoqkM:WAj6wIwwUnE:65A5CxuvL04&sa=N&cd=1&ct=rc&cs_p=http://mirror.arcticnetwork.ca/pub/gentoo/distfiles/gedit-2.14.4.tar.bz2&cs_f=gedit-2.14.4/gedit/dialogs/gedit-close-confirmation-dialog.c") of detecting a session logout.

From what it seems, there's no pythonic way to do it, but if you do find a suitable way I'd love to know.

- Jackson
Great, I'm going to dig gedit source code... I'll let you know if I find something.

> **SeanHodges said:**
> What comes back in your log when you log out with the program open?

Also, it would be nice to dump the error trace to the log as well...

There is nothing on the error log, it seems that the application is killed without it can do anything.

---

