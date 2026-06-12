---
title: "Problem with GtkBuilder - builder not defined"
date: 2011-03-15
forum: Programming Talk
---

### Post by 102jon on 2011-03-15
Hi there, I'm writing an application using pygtk and glade with GtkBuilder, but I seem to be having some trouble with it.

```
import gtk
import os, sys
import subprocess

class GadTool:
	def on_filechooserdialog1_destroy(self, widget):
		gtk.main_quit()
		
	def __init__(self):
		builder = gtk.Builder()
        builder.add_from_file("CSA_Tool.glade")        
        self.window = builder.get_object("filechooserdialog1")
        self.entry = builder.get_object("entry1")
        self.button1 = builder.get_object("button1")
        self.button1.set_sensitive = False
        builder.connect_signals(self)
    
	def on_filechooserdialog1_file_activated(self, widget):
		self.entry.set_text(self.window.get_filename())
		self.button1.set_sensitive = True
    	
	def on_filechooserdialog1_current_folder_changed(self, widget):
		os.chdir(self.window.get_current_folder())
    	
	def on_button1_clicked(self, widget):
		gad_process = subprocess.Popen("nc.exe -p 4001 -i 5 -L > " + self.entry.get_text())
    	
    
if __name__ == "__main__":
    interface = GadTool()
    interface.window.show()
    gtk.main()
```

on the line "builder.add_from_file("") it says: builder not defined.

I have looked around online and this problem seems to be a version thing, ie. a version before GTK 2.0. However, I have the latest version of GTK installed. What is the problem?

---

### Post by Arndt on 2011-03-15
> **102jon said:**
> Hi there, I'm writing an application using pygtk and glade with GtkBuilder, but I seem to be having some trouble with it.

```
import gtk
import os, sys
import subprocess

class GadTool:
	def on_filechooserdialog1_destroy(self, widget):
		gtk.main_quit()
		
	def __init__(self):
		builder = gtk.Builder()
        builder.add_from_file("CSA_Tool.glade")        
        self.window = builder.get_object("filechooserdialog1")
        self.entry = builder.get_object("entry1")
        self.button1 = builder.get_object("button1")
        self.button1.set_sensitive = False
        builder.connect_signals(self)
    
	def on_filechooserdialog1_file_activated(self, widget):
		self.entry.set_text(self.window.get_filename())
		self.button1.set_sensitive = True
    	
	def on_filechooserdialog1_current_folder_changed(self, widget):
		os.chdir(self.window.get_current_folder())
    	
	def on_button1_clicked(self, widget):
		gad_process = subprocess.Popen("nc.exe -p 4001 -i 5 -L > " + self.entry.get_text())
    	
    
if __name__ == "__main__":
    interface = GadTool()
    interface.window.show()
    gtk.main()
```

on the line "builder.add_from_file("") it says: builder not defined.

I have looked around online and this problem seems to be a version thing, ie. a version before GTK 2.0. However, I have the latest version of GTK installed. What is the problem?

To me it looks like an indentation problem. Indent the "builder." lines one step more and try again.

---

### Post by andrew1992 on 2011-03-15
There's a chance you may have configured your '.glade' file to be used with libglade and not GtkBuilder. Open up your Glade file, and click "Edit->Preferences". Check to make sure your file format is GtkBuilder and not Libglade.

---

### Post by 102jon on 2011-03-15
Problem solved. Things were indented fine, it just came out weird in the code tags. It was a problem with having libglade set as default.

---

