---
title: "PyGTK window with multiple spinbuttons"
date: 2009-07-05
forum: Programming Talk
---

### Post by Nevon on 2009-07-05
I need to create a simple window with three spinbuttons (with a label each), an OK button and a cancel button. However, I have very little experience with PyGTK. 

Creating stuff like AboutDialogs, StatusIcons and stuff like that is fairly easy. But I have no idea where to start with making a whole window - even if it is a simple one. 

I attached a Glade mockup of what I'm looking for, only it'd be great if I could somehow set a limit on the minutes and seconds spinbuttons, so they can't go over 60. Not completely necessary, just neat.

If anyone has any examples that they could point me to that I can adapt to match what it is I'm looking for, I'd be very happy.

---

### Post by unutbu on 2009-07-05
You can sometimes find examples what you are looking for by using locate and grep:
```

locate .py | xargs grep -i 'spinbutton' 
```

You can also find pygtk examples by installing the

python-gtk2-doc
python-gtk2-tutorial 

packages.


For instance, /usr/share/doc/python-gtk2-tutorial/html/examples/spinbutton.py

---

### Post by Nevon on 2009-07-05
> **unutbu said:**
> For instance, /usr/share/doc/python-gtk2-tutorial/html/examples/spinbutton.py

Thank you. I have with the help of that example gotten almost exactly what it is I want. However, how can I send the values from each of the spinbuttons to another function when the user presses the OK button? And how can I destroy only that single window when the user pressed cancel, instead of stopping the entire program? (in the example that window is the only one, but I'm planning to integrate it into another program once I've got it working)

```
#!/usr/bin/env python

# example spinbutton.py

import pygtk
pygtk.require('2.0')
import gtk

class DurationSettings:

    def __init__(self):
        window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        window.connect("destroy", lambda w: gtk.main_quit())
        window.set_title("Caffeine")

        main_vbox = gtk.VBox(False, 5)
        main_vbox.set_border_width(10)
        window.add(main_vbox)

        frame = gtk.Frame("Duration")
        main_vbox.pack_start(frame, True, True, 0)
  
        vbox = gtk.VBox(False, 0)
        vbox.set_border_width(5)
        frame.add(vbox)
        hbox = gtk.HBox(False, 0)
        vbox.pack_start(hbox, True, True, 5)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)

        label = gtk.Label("Hours:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)
  
        adj = gtk.Adjustment(0.0, 0.0, 99.0, 1.0, 5.0, 0.0)
        spinner = gtk.SpinButton(adj, 0, 0)
        spinner.set_wrap(True)
        vbox2.pack_start(spinner, False, True, 0)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)
  
        label = gtk.Label("Minutes:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)

        adj = gtk.Adjustment(0.0, 0.0, 60.0, 1.0, 5.0, 0.0)
        spinner = gtk.SpinButton(adj, 0, 0)
        spinner.set_wrap(True)
        vbox2.pack_start(spinner, False, True, 0)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)
  
        label = gtk.Label("Seconds:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)
  
        adj = gtk.Adjustment(0.0, 0.0, 60.0, 1.0, 100.0, 0.0)
        spinner = gtk.SpinButton(adj, 0, 0)
        spinner.set_wrap(True)
        spinner.set_size_request(55, -1)
        vbox2.pack_start(spinner, False, True, 0)
  
        hbox = gtk.HBox(False, 0)
        main_vbox.pack_start(hbox, False, True, 0)

        button = gtk.Button(stock="OK")
        button.connect("clicked", lambda w: gtk.main_quit())
        hbox.pack_start(button, True, True, 5)
        button = gtk.Button(stock="Cancel")
        button.connect("clicked", lambda w: gtk.main_quit())
        hbox.pack_start(button, True, True, 5)
        window.show_all()

def main():
    gtk.main()
    return 0

if __name__ == "__main__":
    DurationSettings()
    main()

```

---

### Post by unutbu on 2009-07-05
Well, I don't know if this is the best way to do it, but this is how I would do it:

[list]
[*] Change window --> self.window so you can access it from other methods.
[*] Similarly, change spinner to self.spinner_hour, self.spinner_minute, self.spinner_second. This allows you to talk to these widgets. Otherwise, you lose the ability to access them easily. 
[*] Change the "Ok" and "Cancel" connectors so they do not call gtk.main_quit.
Rather, connect them to new methods "ok_cb" and "cancel_cb". (cb stands for callback.)
[*] Create class instance attributes self.hour, self.minute, self.second to hold the values taken from the spinners
[*] When the ok_cb callback is called, self.hour, self.minute, self.second should get the values from the spinners, and hide the DurationSettings window.
[*] When cancel_cb is called, (maybe?) set self.hour, self.minute, self.second back to 0 and hide the DurationSettings window.
[*] Modify DurationSettings so that window.show_all() is taken out of __init__.
[*] The max value of the minute and second gtk.Adjustments should be 59 rather than 60 I think. 
[*] When you create a separate gtk.Window, in its __init__ you can create a 
```

self.ds=DurationSettings() 
```

instance. Since the show_all() command was left out, the self.ds window will not appear until you call self.ds.show().
[*] Since the other window has access to ds, it can show it, hide it, and access the spinner_hour, spinner_minute, and spinner_second attributes however it pleases.
[/list]

Here is some example code:


[PHP]
#!/usr/bin/env python

# example spinbutton.py

import pygtk
pygtk.require('2.0')
import gtk

class DurationSettings:
    def ok_cb(self,widget,data=None):
        self.hour=int(self.spinner_hour.get_value())
        self.minute=int(self.spinner_minute.get_value())
        self.second=int(self.spinner_second.get_value())
        self.window.hide()

    def initialize(self):
        self.hour=0
        self.minute=0
        self.second=0

    def cancel_cb(self,widget,data=None):
        self.initialize()
        self.window.hide()

    def show(self):
        self.window.show_all()

    def __init__(self):
        self.initialize()
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("destroy", lambda w: gtk.main_quit())
        self.window.set_title("Caffeine")

        main_vbox = gtk.VBox(False, 5)
        main_vbox.set_border_width(10)
        self.window.add(main_vbox)

        frame = gtk.Frame("Duration")
        main_vbox.pack_start(frame, True, True, 0)
  
        vbox = gtk.VBox(False, 0)
        vbox.set_border_width(5)
        frame.add(vbox)
        hbox = gtk.HBox(False, 0)
        vbox.pack_start(hbox, True, True, 5)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)

        label = gtk.Label("Hours:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)
  
        adj = gtk.Adjustment(0.0, 0.0, 99.0, 1.0, 5.0, 0.0)
        self.spinner_hour = gtk.SpinButton(adj, 0, 0)
        self.spinner_hour.set_wrap(True)
        vbox2.pack_start(self.spinner_hour, False, True, 0)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)
  
        label = gtk.Label("Minutes:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)

        adj = gtk.Adjustment(0.0, 0.0, 59.0, 1.0, 5.0, 0.0)
        self.spinner_minute = gtk.SpinButton(adj, 0, 0)
        self.spinner_minute.set_wrap(True)
        vbox2.pack_start(self.spinner_minute, False, True, 0)
  
        vbox2 = gtk.VBox(False, 0)
        hbox.pack_start(vbox2, True, True, 5)
  
        label = gtk.Label("Seconds:")
        label.set_alignment(0, 0.5)
        vbox2.pack_start(label, False, True, 0)
  
        adj = gtk.Adjustment(0.0, 0.0, 59.0, 1.0, 100.0, 0.0)
        self.spinner_second = gtk.SpinButton(adj, 0, 0)
        self.spinner_second.set_wrap(True)
        self.spinner_second.set_size_request(55, -1)
        vbox2.pack_start(self.spinner_second, False, True, 0)
  
        hbox = gtk.HBox(False, 0)
        main_vbox.pack_start(hbox, False, True, 0)

        button = gtk.Button(stock="OK")
        button.connect("clicked", self.ok_cb)
        hbox.pack_start(button, True, True, 5)
        button = gtk.Button(stock="Cancel")
        button.connect("clicked", self.cancel_cb)
        hbox.pack_start(button, True, True, 5)


class MainWin:

    def destroy(self, widget, data=None):
        print "destroy signal occurred"
        gtk.main_quit()

    def duration_cb(self, widget, data=None):
        self.ds.show()

    def report_cb(self,widget,data=None):
        print('%02i:%02i:%02i'%(self.ds.hour,self.ds.minute,self.ds.second))

    def __init__(self):
        self.ds=DurationSettings()      
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(10)
        self.hbox=gtk.HBox(homogeneous=False,spacing=0)
        self.window.add(self.hbox)
        self.button_duration=gtk.Button('Set Duration')
        self.button_duration.connect('clicked', self.duration_cb)
        self.button_report=gtk.Button('Report')
        self.button_report.connect('clicked', self.report_cb)
        self.hbox.pack_end(self.button_duration)
        self.hbox.pack_end(self.button_report)
        self.button_duration.show()
        self.button_report.show()
        self.hbox.show()
        self.window.show()

    def main(self):
        gtk.main()

if __name__ == "__main__":
    MainWin().main()

[/PHP]

---

### Post by Nevon on 2009-07-06
> **unutbu said:**
> Well, I don't know if this is the best way to do it, but this is how I would do it:

Thank you very much for that excellent answer! With some fiddling I managed to adjust that example code to fit my needs perfectly.

---

