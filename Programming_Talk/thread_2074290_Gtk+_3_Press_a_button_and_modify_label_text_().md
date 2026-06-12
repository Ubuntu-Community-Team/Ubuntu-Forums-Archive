---
title: "Gtk+ 3 Press a button and modify label text (?)"
date: 2012-10-21
forum: Programming Talk
---

### Post by myromance123 on 2012-10-21
Hi there.
I have been trying to get a button in Gtk+ 3 to change the text of a Gtk.Label after being pressed but I am constantly getting this error:

```
Traceback (most recent call last):
  File "/home/ismail/Desktop/Coding/pygtk code/changelabel.py", line 20, in button_pressed
    label.set_text("Button Pressed!")
NameError: global name 'label' is not defined
```

My code is short as this is the functionality I have been trying to get working for a while today. Here is my source code:

```
#!/usr/env/python
from gi.repository import Gtk

class ChangeLabel(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title="Change Label Text")

        table = Gtk.Table(2, 3, True)
        self.add(table)

        label = Gtk.Label("Press the button")
        button = Gtk.Button("Press Me")
        button.connect("clicked", self.button_pressed)

        table.attach(label, 1, 2, 0, 1)
        table.attach(button, 1, 2, 1, 2)

    def button_pressed(self, button):
        label.set_text("Button Pressed!")

win = ChangeLabel()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()
```

I am using the Python IDLE 2.7. Basically this is Python with Gtk+ 3
Any help is very much appreciated, and if possible please make it as understandable as possible.

I have included a picture of my simple app in the attachments, and just so you know this is being done on Ubuntu 12.10 64Bit(Quantal).

---

### Post by spjackson on 2012-10-21
```

    def button_pressed(self, button):
        button.set_label("Button Pressed!")

```

---

### Post by myromance123 on 2012-10-21
I am not looking to change the button's label.
I am looking to change the label above the button.
The one that says "Press the Button"

Thanks though spjackson for the help.

---

### Post by spjackson on 2012-10-21
Sorry, I misunderstood. One way to do it is to make label a class variable.
```


#!/usr/env/python
from gi.repository import Gtk

class ChangeLabel(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title="Change Label Text")

        table = Gtk.Table(2, 3, True)
        self.add(table)

        self.label = Gtk.Label("Press the button")
        button = Gtk.Button("Press Me")
        button.connect("clicked", self.button_pressed)

        table.attach(self.label, 1, 2, 0, 1)
        table.attach(button, 1, 2, 1, 2)

    def button_pressed(self, button):
        self.label.set_text("Button Pressed!")

win = ChangeLabel()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()

```

---

### Post by oldfred on 2012-10-21
I am trying to learn python, but you need self.

```
#!/usr/env/python
from gi.repository import Gtk

class ChangeLabel(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title="Change Label Text")

        table = Gtk.Table(2, 3, True)
        self.add(table)

        self.label = Gtk.Label("Press the button")
        button = Gtk.Button("Press Me")
        button.connect("clicked", self.button_pressed)

        table.attach(self.label, 1, 2, 0, 1)
        table.attach(button, 1, 2, 1, 2)

    def button_pressed(self, button):
        self.label.set_text("Button Pressed!")

win = ChangeLabel()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()

```

---

### Post by myromance123 on 2012-10-21
Thank you so much spjackson and olfred!
It works wonderfully.

---

