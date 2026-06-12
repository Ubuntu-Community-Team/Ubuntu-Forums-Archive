---
title: "How do I run an sh script from a button"
date: 2012-06-30
forum: Programming Talk
---

### Post by TheAlliedFleet on 2012-06-30
I'm currently developing an installer for a certain game. Right now I have an sh script and I'm not sure how to activate it. I am building the GUI in glade if that helps (python)

---

### Post by ubudog on 2012-06-30
Edit:
Sorry, misread your post.

Perhaps have a look at this:
[http://stackoverflow.com/questions/89228/how-to-call-external-command-in-python](http://stackoverflow.com/questions/89228/how-to-call-external-command-in-python)

---

### Post by TheAlliedFleet on 2012-06-30
inserted code as 

> self.beginbutton = self.builder.get_object("beginbutton")

    def on_beginbutton_clicked(self, widget):
        subprocess.call(['home/mcinstaller/data/media/Minecraft_Installer_.sh'])> 



Getting this error when typing 'quickly run' into the terminal


> (mcinstaller:16747): Gtk-WARNING **: Theme parsing error: gnome-panel.css:28:11: Not using units is deprecated. Assuming 'px'.
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `Window' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwds)
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:391: Warning: g_object_set_property: construct property "type" for object `McinstallerWindow' can't be set after construction
  Gtk.Window.__init__(self, type=type, **kwds)> 



I am new to coding so any help is appreciated :)

---

### Post by ubudog on 2012-06-30
I am not too good with Python, but perhaps change: 
```
subprocess.call(['home/mcinstaller/data/media/Minecraft_Installer_.sh'])
```

to

```
subprocess.call(['sh /home/mcinstaller/data/media/Minecraft_Installer_.sh'])

```

Best,
ubudog

---

### Post by Dubslow on 2012-07-01
The error had nothing to do with the subprocess call. He constructs the Window, and then tries to change one of its attributes, which is not allowed. Put another way, you can only set the attribute Window.type as part of the function call to construct the Window. The problem is with code not posted here.

---

