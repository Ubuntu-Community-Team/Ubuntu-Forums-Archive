---
title: "Glade and GTK Builder"
date: 2011-07-01
forum: Programming Talk
---

### Post by KoolPenguin on 2011-07-01
I maybe an idiot but I cannot seem to figure out how to add color to containers, buttons, etc.  Is this possible to do with the Glade interface using the gtk.builder?

Also, what version of GTK+ should I use when creating a GUI? There are lots of options, 2.24 is the default and it has 2.8.

Thanks
--
Chris

---

### Post by KoolPenguin on 2011-07-01
Still looking for an answer for the above question...

However, I do have another question.  I created an interface with Glade and gtk.Builder, coded some Python and for some reason I cannot get the window to even display.  When I execute it from terminal it just hangs until I hit control-c.
```

#!/usr/bin/python

import sys
try:  
    import pygtk  
    pygtk.require("2.0")  
except:  
    pass  
try:  
    import gtk  
except:  
    print("GTK+ not availible...")
    sys.exit(1)
        
class craftyGui:

    def __init__( self ):
        self.builder = gtk.Builder()
        self.builder.add_from_file("shrewds-crafty-gui.ui")
        
        dic = { 
            "on_buttonExit_clicked" : self.quit,
            "on_windowMain_destroy" : self.quit,
        }
        
        self.builder.connect_signals( dic )

    def quit(self, widget):
        sys.exit(0)
        
craftyGui = craftyGui()
gtk.main()

```

I know I have GTK+ 2.24 and Python 2.7 installed.  My .ui is coded for gtk.Builder. I do however have other buttons that I have not coded into Python yet but, I did not connect any signals. Just left them blank, so I don't think that should be the problem.

Thanks
--
Chris

EDIT:

@@@ OMG @@@ I feel like an idiot, the main window was set to not be visible.  Learned something new about Glade/GTK...

Thanks anyways...

Chris

---

