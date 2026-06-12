---
title: "Calling a os.system('command') in a loop that can be stopped in Python (Glade)"
date: 2008-12-07
forum: Programming Talk
---

### Post by uMuppet on 2008-12-07
I'm fairly new to Python but thought I had the basics down when I got hit with this and can't find a way around.

I'm using Glade for GUI and Python for code making a program that will call a script I wrote in Perl, pause for x seconds then call it again infinite times until told to stop.  Sounds easy and I had no problem doing it until I tried to stop it and ctrl-c is the only way.

I know you're thinking 'why not just write the whole thing in Python, why call a Perl script?'  The Perl script queries a Modbus device connected to the serial port and stores the result in a MySQL database.  This works well and I can't seem to do it using the pyserial library in Python so it has to stay in Perl.

Here is a cutdown sample of the code

```

from pylab import *
import sys
import datetime
import os
import time

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
import MySQLdb

###############################################################################
# End of Imports 



record = 0
view = 0

class gui:

# Not sure where to put this but I need it to be scanned all the time
	global record
	if (record ==1):
		os.system("perl modbus3c.pl")
		time.sleep(3)  



	def __init__(self):
		global record
		global view
				
               

		
                #Set the Glade file
                self.gladefile = "graph4a.glade"  
                self.wTree = gtk.glade.XML(self.gladefile) 
              
                #Create our dictionay and connect it
                dic = { "on_record_toggled" : self.record_toggle,
                        "on_window1_destroy" : gtk.main_quit }
                
		self.wTree.signal_autoconnect(dic)



		
        def record_toggle(self, widget):
		global record
		if (record == 1):
			print "Record is turned off"
			record = 0                        
						    
                else:
                        print "Record is turned on" 
			record = 1

			
		


if __name__ == "__main__":
        hwg = gui()
        gtk.main()




```

---

### Post by wmcbrine on 2008-12-07
I don't see the Perl script being called at all. There's no loop, and the one time the relevant code is executed, record is zero, so the os.system() call is not reached.

Also, you haven't really explained how you *want* it to be told to stop.

Maybe with the full Python + Perl + Glade code we could answer you better?

---

### Post by uMuppet on 2008-12-07
> **wmcbrine said:**
> I don't see the Perl script being called at all. There's no loop, and the one time the relevant code is executed, record is zero, so the os.system() call is not reached.

Also, you haven't really explained how you *want* it to be told to stop.

Maybe with the full Python + Perl + Glade code we could answer you better?

Sorry, I am new at this.

I have attached the glade/perl/python scripts

If I push 'Record' in the Glade gui I need it to execute the Perl script over and over with a pause in between until I press the 'Record' button again which will stop it.  

I have written several other programs in Python but may not have the foundation understanding correct so any help will be greatly appreciated.

---

