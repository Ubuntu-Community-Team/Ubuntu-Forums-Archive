---
title: "pygtk: show dialog after main window has displayed"
date: 2010-04-17
forum: Programming Talk
---

### Post by spillz on 2010-04-17
I have an app with a gtk Box in my main window and a modal dialog that I want to display after the box has fully rendered.

I thought of doing something along these lines

```

class MainBox(gtk.HBox):
  def __init__(self):
     gtk.HBox.__init__(self)
     self.pack_start(widget1)
     self.pack_start(widget2)
     ...
     self.show_all()
     self.run_dialog()
  def run_dialog(self):
     d=Dialog()
     d.run()
     ##do stuff with result

class Dialog():
  def __init__(self):
     #add a bunch of widgets etc

```

But the problem is the dialog will run before MainBox displays and because the dialog is modal it blocks the display of the mainbox until it is destroyed.

Short of running a timer with callback is there a to guarantee that the MainBox has rendered correctly before the dialog runs? I couldn't see an obvious signal in gtk.Widget, but maybe I'm missing something...

---

### Post by SledgeHammer_999 on 2010-04-17
How about you connect to the "show" signal of gtk widget?

---

### Post by spillz on 2010-04-20
> **SledgeHammer_999 said:**
> How about you connect to the "show" signal of gtk widget?

Unfortunately "show" only signals a request to dsplay the item, which may happen well before the widget actually displays.

In the end, this hack using the "realize" signal was the best I could come up with:

```

class MainBox(gtk.HBox):
  def __init__(self):
     gtk.HBox.__init__(self)
     self.pack_start(widget1)
     self.pack_start(widget2)
     ...
     self.show_all()
     self.run_dialog()
     self.realize_id=last_widget_added.connect_after("realize",realize_cb)
  def realize_cb(self,widget):
     widget.disconnect(self.realize_id)
     self.run_dialog()
  def run_dialog(self):
     d=Dialog()
     d.run()
     ##do stuff with result

class Dialog():
  def __init__(self):
     #add a bunch of widgets etc

```

---

### Post by hongquan1987 on 2012-10-09
Thanks

---

