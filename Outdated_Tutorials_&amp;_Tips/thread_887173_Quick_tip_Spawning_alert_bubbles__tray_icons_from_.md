---
title: "Quick tip: Spawning alert bubbles / tray icons from a command"
date: 2008-08-11
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2008-08-11
Sometimes when leaving large jobs running in a terminal or setting simple sleep alerts, it's useful to be able to have a command for spawning alerts to the GNOME desktop rather than just displaying something in a particular terminal that you may not see immediately.


Some of you might be jumping up and down screaming **notify-send** at this point. That's what I would usually do. This command is in the **libnotify-bin** package. It spawns a libnotify popup in the lower right corner of the screen, which can be configured to either self-dismiss or stay there for a specified duration. This is pretty nice, except that it is easy to click out accidentally, or be missed if you are away from the screen for more than the typical 10-20 second timeout. Furthermore, when the screen is locked, the bubble is not displayed altogether! This is primarily due to the libnotify system being designed to display quick "by the way" notifications that don't interfere with the user's workflow, not important alerts that demand more persistence.


So, I wrote a quick Python script, notify-bubble that uses similar code to the Restricted Drivers Manager or Update Notifier. It displays a tray icon and also pops up a bubble from it that dismisses itself in a bit, but the tray icons stays. The tooltip for the tray icon displays the alert message again on hover.


Attached are screenshots comparing notify-send and notify-bubble. The script is written in Python and provided below:

```

#!/usr/bin/python
# notify-bubble: Alert bubble + systray icon notification system
#
# Author: John Dong <jdong@ubuntu.com>
#
# Feel free to use/tweak/modify to your free will.

import gtk
import gobject
import pynotify

icon=None
notify=None

def create_icon(title, text=""):
        global icon
        pynotify.init("pynotify")
        icon=gtk.status_icon_new_from_icon_name("important")
        icon.set_visible(False)
        icon.connect('activate', quit)
        icon.set_tooltip("%s\n(%s)" % (title, text))
        icon.set_visible(True)
	ui_idle()
	gobject.timeout_add (500, show_notification,
	(title, text, icon))

def show_notification(data):
	global notify
	(title, text, icon) = data
	notify = pynotify.Notification(title,text,"pynotify")
	notify.set_urgency(pynotify.URGENCY_NORMAL)
	notify.attach_to_status_icon(icon)
	notify.set_timeout(20000)
	notify.show()


def ui_idle():
	while gtk.events_pending():
		gtk.main_iteration(False)


def quit(data):
	gtk.main_quit()

import sys
name="pynotify alert"
detail="Click the yellow triangle icon to dismiss"
try:
   name=sys.argv[1]
   detail=sys.argv[2]
except IndexError:
   pass
create_icon(name, detail)
print "Pynotify alert spawned. Clicking the alert tray icon will exit this script too..."
gtk.main()

```

---

### Post by scrawl on 2008-08-12
Nice one, thanks :)

---

### Post by n.durgesh on 2008-11-11
hi guys 
i'm verry new to Python. and i was searchin for this "pynotify" module but could not find it anywhere.
it would b great if someone can help me with a link for this
thanks in advance

---

### Post by mlissner on 2009-04-07
Will this port directly to the new notification system?

---

### Post by mlissner on 2009-04-18
> **mlissner said:**
> Will this port directly to the new notification system?

In fact it will. I just tested it in Jaunty.

---

