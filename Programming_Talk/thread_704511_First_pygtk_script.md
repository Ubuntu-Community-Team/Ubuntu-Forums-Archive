---
title: "First pygtk script"
date: 2008-02-22
forum: Programming Talk
---

### Post by Can+~ on 2008-02-22
**Name:** Cisoplus gui.
**Description:** My first venture on pygtk, as I was just starting, I wanted to make a test of my skills. So I took this psp converter (that converts .iso images into .cso (compressed)), but cisoplus only works on the shell, so I made a gui for it, that finally calls xterm and hands the full command.

**Screenshot:**
[IMG]http://img.photobucket.com/albums/v517/CanXp/cisoplusb.png[/IMG]

**Source:**
```
#!/usr/bin/env python
#Cisoplus GUI: Python GTK script, release 03. -can

import gtk
import pygtk
import re
import os

class ConvertionWindow:
	def defaults(self):
		self.compress = True # True = Compression, False = Decompression
		self.quality  = 9 #Compression Quality
		self.executable = "./cisoplus"
	
	def misc_event(self, widget, data=None):
		self.build_string()
	
	def error_report(self, message):
		self.report = gtk.Dialog("Error", self.win, gtk.DIALOG_DESTROY_WITH_PARENT, (gtk.STOCK_OK, gtk.RESPONSE_OK))
		self.msg = gtk.Label(message)
		
		self.report.set_size_request(180, 100)
		self.report.vbox.pack_start(self.msg, True, True, 10)

		self.msg.show()
		self.report.run()
		self.report.destroy()
	
	def fix_spaces(self, data):
		return data.replace(" ", "\ ")
	
	def check_build_string(self, widget, data=None):
		temp_errors = ""
		temp_ready = True
		if self.comtable.inpfileline == "":
			temp_errors += "No Input file defined!\n"
			temp_ready = False
		if self.comtable.outfileline == "":
			temp_errors += "No Output file defined!\n"
			temp_ready = False
			
		if temp_ready:
			self.build_string()
			self.run_string()
		else:
			self.error_report(temp_errors)
		
	def build_string(self):
		temp_comp    = ("dec", "com")[self.compress]
		temp_quality = ("", " -l"+str(self.quality))[self.compress]
		temp_thread  = ("", " -MT")[self.compress and self.comtable.chthread.get_active()]
		temp_optim   = ("", " -opt")[self.compress and self.comtable.choptimized.get_active()]
		temp_video   = ["", " -vid"][self.compress and not self.comtable.chvideo.get_active()]
		temp_audio   = ["", " -aud"][self.compress and not self.comtable.chaudio.get_active()]
		
		self.configline = "%s -%s%s%s%s%s%s %s %s" % (self.executable, temp_comp, temp_quality, temp_thread,\
		temp_optim, temp_video, temp_audio, self.comtable.inpfileline.get_text(), self.comtable.outfileline.get_text())
		
		self.comtable.progress.set_text(self.configline)
		
	def run_string(self):
		try:
			os.system("xterm -e "+self.configline)
		except:
			temp_causes = """Could not execute.
				-Check that you have execution permissions
				-Check that cisoplus executable is on the same folder"""
			error_report(temp_causes)
	
	def destroy_event(self, widget, data=None):
		gtk.main_quit()
		return False
	
	def quality_change_event(self, widget, data=None):
		h = int(widget.get_value())
		if h>=1 and h<=9:
			self.quality = h
		else:
			self.quality = 9
		self.build_string()
			
	def change_output_entry(self, data):
		self.comtable.outfileline.set_text(data)
		self.build_string()
		
	def change_input_entry(self, data):
		#Fix spaces
		data = self.fix_spaces(data)
		if (data != ""):
			expression = re.split("cso|iso", data, 1)[0]+("cso", "iso")[1-self.compress]
			self.change_output_entry(expression)
		self.comtable.inpfileline.set_text(data)

	def compress_change_event(self, widget, data=None):
		self.compress = widget.get_active()
		self.comtable.qhscale.set_sensitive(self.compress)
		self.comtable.chthread.set_sensitive(self.compress)
		self.comtable.choptimized.set_sensitive(self.compress)
		self.comtable.chvideo.set_sensitive(self.compress)
		self.comtable.chaudio.set_sensitive(self.compress)
		self.change_input_entry("")
		self.change_output_entry("")
		self.build_string()

	def fileselect_input_event(self, widget, data=None):
		#Create dialog
		self.fileselinp = gtk.FileChooserDialog("File selection.", None,\
		gtk.FILE_CHOOSER_ACTION_OPEN, (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_OK))
		
		#Filters
		self.fileselinp.filter = gtk.FileFilter()
		self.fileselinp.filter.set_name(("Compressed Disc Image", "Disc Image")[self.compress])
		self.fileselinp.filter.add_pattern(("*.cso", "*.iso")[self.compress])
		self.fileselinp.add_filter(self.fileselinp.filter)

		#Set response
		self.fileselinp.resp = self.fileselinp.run()
		if self.fileselinp.resp == gtk.RESPONSE_CANCEL:
			print "Input file canceled."
		else:
			print "Input file selected." 
			self.change_input_entry(self.fileselinp.get_filename())
			
		self.fileselinp.destroy()
		self.build_string()
	
	def fileselect_output_event(self, widget, data=None):
		#Create dialog
		self.fileselout = gtk.FileChooserDialog("Output file selection.", None,\
		gtk.FILE_CHOOSER_ACTION_OPEN, (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL, gtk.STOCK_OPEN, gtk.RESPONSE_OK))
		
		#No Filter :(
		self.fileselout.filter = gtk.FileFilter()
		self.fileselout.filter.set_name(("Compressed Disc Image", "Disc Image")[1-self.compress])
		self.fileselout.filter.add_pattern(("*.cso", "*.iso")[1-self.compress])
		self.fileselout.add_filter(self.fileselout.filter)

		#Set response
		self.fileselout.resp = self.fileselout.run()
		if self.fileselout.resp == gtk.RESPONSE_CANCEL:
			print "Output file canceled."
		else:
			print "Output file selected." 	
			self.change_output_entry(self.fileselout.get_filename())
			
		self.fileselout.destroy()
		self.build_string()
	
	def comtableMaker(self):
		#Build table
		self.comlabel = gtk.Label("(De)compression")
		self.comtable = gtk.Table(10, 3, False)
		self.notebook.append_page(self.comtable, self.comlabel)
		
		#c is a helping letter, for less writing
		c = self.comtable
		
		#Sub gtk elements
		c.inptitle    = gtk.Label("Input File:                          ")
		c.inpfileline = gtk.Entry()
		c.inpfilebutt = gtk.Button("Open", gtk.STOCK_OPEN)
		c.outtitle    = gtk.Label("Output File:                         ")
		c.outfileline = gtk.Entry()
		c.outfilebutt = gtk.Button("Open", gtk.STOCK_OPEN)
		c.contypec    = gtk.RadioButton(None, "Compress")
		c.contyped    = gtk.RadioButton(c.contypec, "Decompress")
		c.conframe    = gtk.Frame("Task:")
		c.conhbox     = gtk.HBox()
		c.qadjust     = gtk.Adjustment(9, 1, 9, 1, 1, 0)
		c.qhscale     = gtk.HScale(c.qadjust)
		c.qframe      = gtk.Frame("Compression: (Higher is more compressed)")
		c.chthread    = gtk.CheckButton("Multi-thread")
		c.choptimized = gtk.CheckButton("Optimized")
		c.chvideo     = gtk.CheckButton("Compress Video")
		c.chaudio     = gtk.CheckButton("Compress Audio")
		c.progress    = gtk.Entry()
		c.pstart      = gtk.Button("Start", gtk.STOCK_APPLY)
		
		#defaults
		c.chaudio.set_active(True)
		c.chvideo.set_active(True)
		c.progress.set_editable(False)

		#sizes
		c.set_size_request(self.tabdim[0], self.tabdim[1])
		c.inpfileline.set_size_request(self.entdim[0], self.entdim[1])
		c.inpfilebutt.set_size_request(self.butdim[0], self.butdim[1])
		c.outfileline.set_size_request(self.entdim[0], self.entdim[1])
		c.outfilebutt.set_size_request(self.butdim[0], self.butdim[1])
		c.progress.set_size_request(self.entdim[0], self.entdim[1])
		c.conframe.set_size_request(self.entdim[0], 60)
		c.qframe.set_size_request(self.entdim[0], 70)
		c.conhbox.set_border_width(10)
		c.qhscale.set_digits(0)
		
		c.set_col_spacing(0, 10)
		c.set_col_spacing(1, 5)
		c.set_row_spacing(1, 10)
		c.set_row_spacing(4, 10)
		c.set_row_spacing(5, 10)
		c.set_row_spacing(6, 10)
		c.set_row_spacing(7, 20)
		c.set_border_width(10)
		
		c.conframe.add(c.conhbox)
		c.qframe.add(c.qhscale)
		c.conhbox.pack_start(c.contypec, False, False, 0)
		c.conhbox.pack_start(c.contyped, False, False, 0)
		c.attach(c.inptitle,    0, 1, 0, 1, 0, 0, 0, 0)
		c.attach(c.inpfileline, 0, 2, 1, 2, gtk.FILL, 0, 0, 0)
		c.attach(c.inpfilebutt, 2, 3, 1, 2, gtk.FILL, 0, 0, 0)
		c.attach(c.outtitle,    0, 1, 2, 3, 0, 0, 0, 0)
		c.attach(c.outfileline, 0, 2, 3, 4, gtk.FILL, 0, 0, 0)
		c.attach(c.outfilebutt, 2, 3, 3, 4, gtk.FILL, 0, 0, 0)
		c.attach(c.conframe,    0, 2, 4, 5, gtk.FILL, 0, 0, 0)
		c.attach(c.qframe,      0, 2, 5, 6, gtk.FILL, 0, 0, 0)
		c.attach(c.chthread,    0, 1, 6, 7, 0, 0, 0, 0)
		c.attach(c.choptimized, 1, 2, 6, 7, 0, 0, 0, 0)
		c.attach(c.chvideo,     0, 1, 7, 8, 0, 0, 0, 0)
		c.attach(c.chaudio,     1, 2, 7, 8, 0, 0, 0, 0)
		c.attach(c.progress,    0, 2, 8, 9, gtk.FILL, 0, 0, 0)
		c.attach(c.pstart,      2, 3, 8, 9, gtk.FILL, 0, 0, 0)

		
		
	def gentableMaker(self):
		#Build table
		self.genlabel = gtk.Label("About")
		self.gentable = gtk.Table(10, 3, False)
		self.notebook.append_page(self.gentable, self.genlabel)
		self.gentable.set_size_request(self.tabdim[0], self.tabdim[1])
		
		g = self.gentable
		
		g.filler = gtk.Label("Nothing here yet")
		g.set_border_width(30)
		g.attach(g.filler,    0, 1, 0, 1, 0, 0, 0, 0)
	
	def __init__(self):
		#coding elements
		self.defaults()
		
		#dimensions
		self.mainString = ""
		self.windim = (450, 500)
		self.butdim = (110, 40)
		self.entdim = (150, 24)
		self.tabdim = (480, self.windim[1]-70)
		
		#objects
		self.win        = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.bquit      = gtk.Button("", gtk.STOCK_CLOSE)
		self.notebook   = gtk.Notebook()
		self.mainvbox   = gtk.VBox()
		self.subvbox    = gtk.VBox()
		self.buttonrow  = gtk.HBox()
		self.toolbox    = gtk.Tooltips()
		
		self.fileselout = gtk.FileChooserDialog("Folder selection.")
				
		#style
		self.win.set_title("Cisoplus GUI")
		self.win.set_size_request(self.windim[0], self.windim[1])
		self.win.set_border_width(10)
		self.win.set_resizable(False)
		self.bquit.set_size_request(self.butdim[0], self.butdim[1])
		self.notebook.set_size_request(self.tabdim[0], self.tabdim[1])
		self.notebook.set_tab_pos(gtk.POS_TOP)
		
		#pack
		self.win.add(self.mainvbox)
		self.mainvbox.pack_start(self.notebook, False, False, 0)
		self.mainvbox.pack_start(self.buttonrow, True, True, 5)
		self.buttonrow.pack_end(self.bquit, False, False, 0)
		
		#subpackaging (Comment any of this to remove a whole tab section)
		self.comtableMaker()
		self.gentableMaker() 
		
		#connections
		self.win.connect("destroy", self.destroy_event, None)
		self.bquit.connect("clicked", self.destroy_event, None)
		self.comtable.contypec.connect("toggled", self.compress_change_event, None)
		self.comtable.inpfilebutt.connect("clicked", self.fileselect_input_event, None)
		self.comtable.outfilebutt.connect("clicked", self.fileselect_output_event, None)
		self.comtable.qadjust.connect("value_changed", self.quality_change_event, None)
		self.comtable.pstart.connect("clicked", self.check_build_string, None)
		self.comtable.choptimized.connect("toggled", self.misc_event, None)
		self.comtable.chthread.connect("toggled", self.misc_event, None)
		self.comtable.chvideo.connect("toggled", self.misc_event, None)
		self.comtable.chaudio.connect("toggled", self.misc_event, None)
		self.comtable.outfileline.connect("changed", self.misc_event, None)
		self.comtable.inpfileline.connect("changed", self.misc_event, None)
		
		self.win.show_all()
		self.build_string()
		
	def main(self):
		gtk.main()

if (__name__ == "__main__"):
	a = ConvertionWindow()
	a.main()

```

**File:**
(with cisoplus binary and the pygtk script)

---

### Post by WarMonkey on 2008-03-17
Nice.

---

### Post by Can+~ on 2008-03-17
> **WarMonkey said:**
> Nice.

Whoa, 3 weeks already? I feel like I did this yesterday.

Probably, I should do this again with my new knowledge, just to test my skill progress.

---

### Post by nakul on 2008-05-01
thank you u have made my life easier

---

### Post by RyanfromtheShire on 2010-02-06
How do I install this?

---

### Post by lavinog on 2010-02-07
> **RyanfromtheShire said:**
> How do I install this?

extract it to a folder somewhere.
right click the pspconvert03.py file and select properties>permissions tab
then check the allow executing file as a program.

---

