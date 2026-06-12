---
title: "[python] PyGTK threading gkr_operation_block: assertion failed error"
date: 2010-10-01
forum: Programming Talk
---

### Post by Oleq on 2010-10-01
According to the [http://faq.pygtk.org/index.py?file=faq20.006.htp&req=show](http://faq.pygtk.org/index.py?file=faq20.006.htp&req=show) faq page, I've just written the following code (just an excerpt below):

```
class pyGmail2:
	def __init__(self):
		self.icon_state = 'refresh'
		self.icon_markup = self.localize.get_text_string('refreshing')
		threading.Thread(target=self.do_check, args=[]).start()

	def do_check(self, *args):
		while True:
	    	    self.icon_state = 'refresh'
		    self.icon_markup = 'refreshing'
		    self.synchro_gui()
		    time.sleep(5)

	def set_status_icon_state(self, status, *args):
                self.statusIcon.set_from_file(self.icon_state+'.svg')

	def set_status_icon_markup(self, markup):
		self.statusIcon.set_tooltip_markup(self.localize.get_text_string(markup))

	def synchro_gui(self, *args):
		gobject.idle_add(self.set_status_icon_state, self.icon_state)
		gobject.idle_add(self.set_status_icon_markup, self.icon_markup)

if __name__=="__main__":
	application = pyGmail2()
	gtk.main()

```

The problem is that sometimes (~3 min. period, even without `touching` the GUI!) program aborts with following error:

```
**
ERROR:gkr-operation.c:383:gkr_operation_block: assertion failed: (op->pending != pending)
Aborted
```

It's really hard to find any solution for this. I'm confused. Does anyone has an idea what's wrong with my code?

--------------------

**[SOLVED]**

**Thou shalt never access gnome-keyring from your threads (outside the main GTK thread) with pyGtk!**

---

