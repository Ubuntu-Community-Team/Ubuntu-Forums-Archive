---
title: "[SOLVED] GTK - get changed values of spins not just initial value"
date: 2007-12-01
forum: Programming Talk
---

### Post by mevets on 2007-12-01
I am writing an alarm clock script with a GTK frontend. When the gui loads my spin widget is assigned a value. Then when I go to change the value it changes. Afterwards when I change a combobox that is connected to the spin widget the value should be passed. I never get the changed value though, I always get what it was initally set to.

Inside of __init__:
```

        # make hour spin button
        adjHour = gtk.Adjustment(7, 1, 12, 1, 0, 0)
        spinHour = gtk.SpinButton(adjHour, 0, 0)
        self.thespin  = spinHour
        hboxSetTime.pack_end(spinHour, False, False, 0)

        # make status combobox
        cmbStatus = gtk.combo_box_new_text()
        cmbStatus.append_text("OFF")
        cmbStatus.append_text("ON")
        cmbStatus.set_active(0)
        cmbStatus.connect("changed", self.statusChanged, spinHour.get_value())
        btnBox.pack_end(cmbStatus, False, False, 0)
        vbox1.pack_start(btnBox, False, False, 0)

```

My statusChanged:
```

    def statusChanged(self, widget, hour):
        print hour # this value is old!

```
How am I correctly supposed to get the value of my spin widgets?

---

### Post by llonesmiz on 2007-12-02
I think what you should do is change:

```
 cmbStatus.connect("changed", self.statusChanged, spinHour.get_value())
```to:
```
 cmbStatus.connect("changed", self.statusChanged, spinHour)
```and:
```
 def statusChanged(self, widget, hour):
        print hour # this value is old!
```to:
```
 def statusChanged(self, widget, spinwidget):
        hour=spinwidget.get_value()
        print hour # this value is old!
```

The function you were passing in "connect" doesn't get evaluated every time the "changed" signal is activated. You should simply make that call in your callback and do whatever you need with its result.

---

### Post by Quikee on 2007-12-02
```
cmbStatus.connect("changed", self.statusChanged, spinHour.get_value())

```

Of course you get the initial value if you assigned in the connect the value that spinHour had at that time.

You should do should something like that instead:

```
cmbStatus.connect("changed", self.statusChanged, spinHour)

```

```
 def statusChanged(self, widget, spinHour):
        print spinHour.get_value()

```

or maybe:

```
cmbStatus.connect("changed", self.statusChanged, spinHour.get_value)

```

```
 def statusChanged(self, widget, hourValueCallback):
        print hourValueCallback()

```

or:
```
cmbStatus.connect_object("changed", self.statusChanged, spinHour)

```

```
 def statusChanged(self, widget):
        print widget.get_value()

```

or...

---

### Post by mevets on 2007-12-02
thanks guys, I havent tried this out yet but it seems like it would work!

---

