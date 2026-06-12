---
title: "[SOLVED] python - pop statusbar last message after several seconds?"
date: 2008-10-13
forum: Programming Talk
---

### Post by forger on 2008-10-13
Does anyone know how to set the statusbar to remove/pop the last message after several seconds?
I'm using python, gtk and glade

statusbar and statusbarCID from init
[PHP]
  self.statusbar = self.wTree.get_widget("statusbar")
  self.statusbarCID = self.statusbar.get_context_id('timekpr status bar')[/PHP]

When a button is pressed it calls:
[PHP]self.statusmessage(self,"Applied reward of " + str(arg) + " minute(s) to "+self.user)[/PHP]

The statusmessage def:
[PHP]def statusmessage(self, widget, message):
  self.statusbar.push(self.statusbarCID, message)[/PHP]

I've connected the signal text-pushed to self.statusrefresh:
[PHP]"on_statusbar_text_pushed": self.statusrefresh[/PHP]

the statusrefresh def:
[PHP]def statusrefresh(self, widget, *args):
  self.statusbar.pop(self.statusbarCID)[/PHP]

Now.. how can I call statusrefresh after 5 seconds?
I tried time.sleep(5) but it "keeps the button pressed" if you understand what I mean..

What I want can be seen in gedit, when you save a text file it shows in the statusbar "Saving file" and removes that message after 4-5 seconds. Is that possible with python and gtk?

---

### Post by gomputor on 2008-10-13
Put this just before your time.sleep() function and see if it works:
```
while gtk.events_pending():
    gtk.main_iteration()
```

---

### Post by .nedberg on 2008-10-13
Hi forger!

Have a look at threads. Run a function as a separate thread.

```

import thread
thread.start_new_thread(my_func,(i,))

```

I had a look at this once because I thought we might make a new way to log out a user without giving everyone else a GRACEPERIOD extra.

---

### Post by forger on 2008-10-13
lol, hi nedberg :D
thanks hehe

---

### Post by forger on 2008-10-14
I was advised to use gobject.timeout_add instead:

[PHP]	def statusrefresh(self, widget, msgid):
		self.statusbar.remove(self.statusbarCID,msgid)
	
	def statusmessage(self, widget, message):
		msgid = self.statusbar.push(self.statusbarCID, strftime("%Y-%m-%d %H:%M:%S") + ' ' + message)
		timeoutid = gobject.timeout_add(3000, self.statusrefresh, self, msgid)[/PHP]

Solved! :)

---

