---
title: "libglade-WARNING **: unknown widget class 'GnomeApp' problem with Python 2.6"
date: 2010-05-16
forum: Programming Talk
---

### Post by DangerOnTheRanger on 2010-05-16
I try to run the following in the Terminal:

```

class Application:
    
    def __init__(self):
        # Set up some stuff
        
        print "Creating the window.."
        
        self.glade_file = "glam.glade"
        self.widget_tree = gtk.glade.XML(self.glade_file, "application")
        
        # Show the window
        
        print "The window's up!"
    
    def destroy(self, widget, data=None):
        print "Quitting.."
        
        gtk.main_quit()
        
    def main(self):
        gtk.main()
        
    def get_window(self):
        return self.window

```

But it spits out:

```

Creating the window..

(glam:25797): libglade-WARNING **: unknown widget class 'GnomeApp'
The window's up!

```

No window shows up. What's going on?? :confused:

---

