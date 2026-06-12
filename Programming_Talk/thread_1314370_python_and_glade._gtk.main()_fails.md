---
title: "python and glade. gtk.main() fails"
date: 2009-11-04
forum: Programming Talk
---

### Post by Kruptein on 2009-11-04
I tried to make a python file which handles a glade file,
but it just ends in an infinite loop when it reaches the gtk.main()

gl is not printed because it is after the gtk.main

can anybody tell me what is wrong?

```

#!/usr/bin/python
# -*- coding: utf-8 -*-

import sys
import pygtk
pygtk.require('2.0')
import gtk
import gtk.glade

class GUI:

	wTree = None

	def __init__( self ):
		self.wTree = gtk.glade.XML( "dcryptgui2.glade" )
		
		dic = { 
			"dcrypt" : self.test,
			"on_windowMain_destroy" : self.quit,
		}
		
		self.wTree.signal_autoconnect( dic )

	def test( self ):
		self.wTree.get_widget("entry1").set_text("Entry1")
		self.wTree.get_widget("entry2").set_text("Entry2")
	
	def quit(self, widget):
		sys.exit(0)

def main():
	gtk.main()
	print "gl"
	return 0

if __name__ == "__main__":
	GUI()
	main()
```

---

### Post by Brandon Williams on 2009-11-04
First, it is supposed to enter an infinite loop when you call gtk.main. The loop in gtk.main would break when self.quit is called.

Second, I would expect the the function names for autoconnect to be defined in the glade file, and that your init code would look something like this:
```

        def __init__( self ):
                self.wTree = gtk.glade.XML("dcryptgui2.glade")
                self.wTree.autoconnect(self)
```

Is the problem that you aren't seeing the window? Or that nothing happens when you click the close button on the title bar? If it's the later, then the above should put on the right path. If it's the former, then you will also need to call show on your app's main window. Something like this:
```

                mainWindow = self.wTree.get_widget("MainWindow")
                mainWindow.show()
```

---

### Post by Kruptein on 2009-11-04
Thank you, a combination of both did it!
I didn't use a show function because an examle I downloaded works without it...

---

