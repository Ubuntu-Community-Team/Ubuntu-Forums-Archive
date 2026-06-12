---
title: "pygtk and glade problems/questions?"
date: 2010-01-05
forum: Programming Talk
---

### Post by Mach1723 on 2010-01-05
trying to run a glade file with pygtk and i have this code

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys


import pygtk

pygtk.require("2.0")

import gtk
import gtk.glade

class appgui:
    def __init__(self):
        gladefile = "bzr.glade"
        wname = "topwindow"
        self.wTree = gtk.glade.XML(gladefile,wname)

        self.window = self.wTree.get_widget("MainWindow")
        if (self.window):
            self.window.connect("destroy", gtk.main_quit)
        


    def button1_clicked(self, widget):
        print "BUTTON1 Clicked"







if __name__ == '__main__':
    gui = appgui()
    gtk.main()

```i run it and i have no errors but it doesnt show anything.. so that would be the problem.

SOLVED:
the code i had was based off an glade2 tutorial here is the working code
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
#
#       untitled.py
#       
#       Copyright 2010 zr <mach1723@mach1723-desktop>
#       
#       This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
#       MA 02110-1301, USA.
import sys


import pygtk

pygtk.require("2.0")

import gtk
import gtk.glade

class appgui:
    


        
    def __init__(self):

        
        
        gladefile = "bzr.glade"
        wname = "topwindow"
        self.wTree = gtk.glade.XML(gladefile,None,"",{})
        
        def button1_clicked(widget):
            print "BUTTON1 Clicked"
        def button2_clicked(widget):
            print "BUTTON2 Clicked"
            filebrowser = self.wTree.get_widget("filechooserdialog1")
            filebrowser.show()
        
        widg = self.wTree.get_widget("topwindow")
        
        widg.show_all()
        
        button1 = {"on_button1_clicked":button1_clicked}
        
        self.wTree.signal_autoconnect(button1)









if __name__ == '__main__':
    gui = appgui()
    gtk.main()

```

---

