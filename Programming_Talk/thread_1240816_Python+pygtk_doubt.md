---
title: "Python+pygtk doubt"
date: 2009-08-15
forum: Programming Talk
---

### Post by nipunreddevil on 2009-08-15
i have been trying to connect my gui to serial port,but the result is first serial port code runs and then the gui.
I want the gui to readily update the value after receiving new content from serial port.
Here is my code:```

#!/usr/bin/env python


#Program to show text entries

import pygtk
pygtk.require('2.0')
import gtk
import serial
import re


class Entry:
	def enter_callback(self,widget,entry):
		entry_text=entry.get_text()
		print"Entry contents%s\n"%entry_text
	def entry_toggle_editable(self,checkbutton,entry):
		entry.set_editable(checkbutton.get_active())
	def entry_toggle_visibility(self,checkbutton,entry):
		entry.set_visibility(checkbutton.get_active())
	def __init__(self):
		window=gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.set_size_request(200,100)
		window.set_title("Entry")
		window.connect("delete_event",lambda w,e:gtk.main_quit())
		
		vbox=gtk.VBox(False,0)
		window.add(vbox)
		vbox.show()
		
		label1=gtk.Label("Information")

		entry=gtk.Entry()
		entry.set_max_length(50)
		entry.connect("activate",self.enter_callback,entry)
		entry.set_text(alpha.var1)
		vbox.pack_start(label1,True,True,2)
		vbox.pack_start(entry,True,True,2)
		label1.show()
		entry.show()
		
		hbox=gtk.HBox(False,0)
		vbox.add(hbox)
		hbox.show()
		
		check = gtk.CheckButton("Editable")
		hbox.pack_start(check, True, True, 0)
		check.connect("toggled", self.entry_toggle_editable, entry)
		check.set_active(True)
		check.show()

		check = gtk.CheckButton("Visible")
		hbox.pack_start(check, True, True, 0)
		check.connect("toggled", self.entry_toggle_visibility, entry)
		check.set_active(True)
		check.show()

		button = gtk.Button(stock=gtk.STOCK_CLOSE)
		button.connect("clicked", lambda w: gtk.main_quit())
		vbox.pack_start(button, True, True, 0)
		button.set_flags(gtk.CAN_DEFAULT)
		button.grab_default()
		button.show()
		window.show()

class alpha:
	ser=serial.Serial()
	ser.port="/dev/ttyUSB0"
	ser.baudrate=9600
	ser.open()
	i=0
	g=open('/home/nipun/1.txt','r+')
	vars = re.compile('^(\d+\.?\d*)a(\d+\.?\d*)b(\d+\.?\d*)c(\d+\.?\d*)d(.*)')

	s=ser.readline()
	print s
	g.write(s)
	g.write("\n")
	print "\n"
	m = re.search(vars, s) # Run the regexp on the packet
	var1 = m.group(1) # take out the values
	var2 = m.group(2)
	var3 = m.group(3)
	var4 = m.group(4)
	print var1,"\n"
	


def main():
	gtk.main()
	return 0

if __name__ == "__main__":
	Entry()
	main()
		

```

---

