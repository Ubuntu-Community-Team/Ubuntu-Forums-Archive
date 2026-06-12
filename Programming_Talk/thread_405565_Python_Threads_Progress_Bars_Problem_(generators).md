---
title: "Python Threads Progress Bars Problem (generators?)"
date: 2007-04-09
forum: Programming Talk
---

### Post by crichell on 2007-04-09
I'm developing a python app that restores portions of the OS depending on the specific computer model.  I've never really rapped my head around progress bars so they're always a pain.  Nonetheless, I'm using one thread to pulse the progress bar and another to run base_system.app_install().  Something isn't stopping correctly so the program freezes once it completes.

BTW, reading around it looks like I should be using generators to do this but I'm not sure how to implement them.  I'm open to any better way.

Thanks

```
#!/usr/bin/env python

import os
import sys
import time
import model
import base_system
import gobject
import threading

try:
     import pygtk
     pygtk.require("2.0")
except:
      pass
try:
    import gtk
    import gtk.glade
except:
    sys.exit(1)

#Initializing the gtk's thread engine
gtk.gdk.threads_init()

class pulseSetter(threading.Thread):
    """This class sets the fraction of the progressbar"""
    
    #Thread event, stops the thread if it is set.
    stopthread = threading.Event()
    
    def run(self):
        """Run method, this is the code that runs while thread is alive."""
        
        #Importing the progressbar widget from the global scope
        global progress_bar 
        
        #While the stopthread event isn't setted, the thread keeps going on
        while not self.stopthread.isSet() :
            # Acquiring the gtk global mutex
            gtk.gdk.threads_enter()
            #Setting pulse
            progress_bar.pulse()
            # Releasing the gtk global mutex
            gtk.gdk.threads_leave()
            #Delaying 100ms until the next iteration
            time.sleep(0.1)
            
    def stop(self):
        """Stop method, sets the event to terminate the thread's main loop"""
        self.stopthread.set()

class progressWindow:
    def __init__(self):
        #setup the glade file
        self.gladefile = "system76driver.glade"
    
    def run(self):
        
        #load the dialog from the glade file      
        self.wTree = gtk.glade.XML(self.gladefile, "restoreDialog") 
        #Get the actual dialog widget
        self.dlg = self.wTree.get_widget("restoreDialog")
        #Get the progress bar widget
        self.progress_bar = self.wTree.get_widget("restoreProgress")

        #Set Global Variables
        global restoreDialog
        restoreDialog = self.dlg
        
        global progress_bar
        progress_bar = self.progress_bar
        
        #run the dialog      
        self.dlg.run()
        
        #we are done with the dialog, destroy it
        self.dlg.destroy()

class restore(threading.Thread):
    """This class restores the system"""
    
    #ps starts and stops the progress bar thread
    global ps
    #Thread event, stops the thread if it is set.
    stopthread = threading.Event()
    
    def run(self):
        """Thread install base system."""
        
        #While the stopthread event isn't set, the thread keeps going
        while not self.stopthread.isSet() :
            base_system.app_install()
            ps.stop()
            self.stop()
            
    def stop(self):
        """Stop method, sets the event to terminate the thread's main loop"""
        self.stopthread.set()
        ps.stop()
        restoreDialog.destroy()
        complete = restoreComplete()
        complete.run()
        
class restoreComplete:
    def __init__(self):
        #setup the glade file
        self.gladefile = "system76driver.glade"
    
    def run(self):
        
        #load the dialog from the glade file      
        self.wTree = gtk.glade.XML(self.gladefile, "restoreComplete") 
        #Get the actual dialog widget
        self.dlg = self.wTree.get_widget("restoreComplete")

        #run the dialog
        self.dlg.run()
        
        #we are done with the dialog, destroy it
        self.dlg.destroy()
       
def start():
    global ps
    ps = pulseSetter()
    ps.start()
    global r
    r = restore()
    r.start()
    startRestore = progressWindow()
    startRestore.run()

if __name__ == "__main__":
    go = start()
    gtk.main()
```

---

