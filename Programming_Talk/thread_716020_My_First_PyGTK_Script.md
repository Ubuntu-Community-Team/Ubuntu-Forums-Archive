---
title: "My First PyGTK Script"
date: 2008-03-05
forum: Programming Talk
---

### Post by bobbocanfly on 2008-03-05
I got bored today so decided to try out PyGTK. I wrote a frontend to 'bzr branch'  (graphical wget for bazaar branches). Any thoughts/corrections?

[http://bazaar.launchpad.net/~bobbo/+junk/bzr-grab/files](http://bazaar.launchpad.net/~bobbo/+junk/bzr-grab/files)

```
#!/usr/bin/env python

#TODO: Version checking etc.
import gtk, gtk.glade, os

__title__ = "bzr-grab"
__version__ = "0.1.0"
__authors__= ["David Futcher ('bobbo') <bobbocanfly@gmail.com>"]

#GUI base + Handlers
class gtkGUI:

    #Set Up The GUI
    def __init__(self):	
        #Set the Glade file
        self.gladefile = "bzr-grab.glade"  
        self.wTree = gtk.glade.XML(self.gladefile) 

        #Create our dictionay and connect it
        dic = {
  	    "on_quit_click" : gtk.main_quit,
            "on_main_destroy" : gtk.main_quit,
            "grabButton_clicked" : self.doGrab,
            "on_about_click" : self.showAbout
             }
        self.wTree.signal_autoconnect(dic)

        #Change title of main window (include Version)
        self.wTree.get_widget("mainWindow").set_title(__title__ + " | Version " + __version__)
    
    #Generate an about box on the fly
    #FIXME: About Box Wont Close
    def showAbout(self, widget):
        icon = gtk.gdk.pixbuf_new_from_file("pixmaps/bzr-grab.svg")
        about_box = gtk.AboutDialog()
        about_box.set_name(__title__)
        about_box.set_version(__version__)
        about_box.set_copyright("Copyright (C) David Futcher ('bobbo') 2008")
        about_box.set_comments("A simple GTK frontend to bzr 'branch'")
        about_box.set_authors(__authors__)
        about_box.set_logo(icon)
        about_box.show()

    #Do the actual grab
    def doGrab(self, widget):
        #Get the info from the GUI boxes
        branch_url = self.wTree.get_widget("urlBox").get_text()
        local_dir_orig = self.wTree.get_widget("fileChooser").get_filename()

        #Generate 'true' path
        true_url = branch_url.split('/')
        url_len = len(true_url)
        true_url = true_url[url_len - 1]
        local_dir = local_dir_orig + "/" + true_url

        #TODO: Add error checking
        print "Doing Grab of " + branch_url + " to " + local_dir
        os.system("bzr branch " + branch_url + " " + local_dir)

if __name__ == "__main__":
	gui = gtkGUI()
	gtk.main()

```

---

### Post by WW on 2008-03-05
I haven't actually run the program, but I noticed the "FIXME" comment about the About window not closing.  Here is one way you can fix that:

1. Create a function that handles the closing of the dialog:
```

    def closeAbout(self, widget, data=None):
        self.about_box.hide()
        return True

```

2. Move the code that creates the dialog to __init__, and save it as part of the object.  Also tell the dialog what function to call when it receives "destroy" or "delete_event" events.  E.g., in __init__:
```

        icon = gtk.gdk.pixbuf_new_from_file("pixmaps/bzr-grab.svg")
        self.about_box = gtk.AboutDialog()
        self.about_box.set_name(__title__)
        self.about_box.set_version(__version__)
        self.about_box.set_copyright("Copyright (C) David Futcher ('bobbo') 2008")
        self.about_box.set_comments("A simple GTK frontend to bzr 'branch'")
        self.about_box.set_authors(__authors__)
        self.about_box.set_logo(icon)
        
        self.about_box.connect("destroy", self.closeAbout)
        self.about_box.connect("delete_event", self.closeAbout)

```
3. Simplify showAbout to this:
```

   def showAbout(self, widget):
        self.about_box.show()

```


EDIT: I haven't used Glade, so I don't know if my suggestions will conflict with any of the Glade code.

---

### Post by bobbocanfly on 2008-03-05
Thanks WW that (mainly) fixed it. I ended up having to google the full answer but your code helped me get there. 

For future reference call 

```
self.about_box.connect("response", self.closeAbout)
```

before calling run().

---

