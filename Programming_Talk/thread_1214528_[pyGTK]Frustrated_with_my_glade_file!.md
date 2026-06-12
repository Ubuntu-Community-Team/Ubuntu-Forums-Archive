---
title: "[pyGTK]Frustrated with my glade file!"
date: 2009-07-16
forum: Programming Talk
---

### Post by j7%&lt;RmUg on 2009-07-16
Hey everyone,

Im using pygtk to code a task list manager application, it all works fine before i execute my setup.py file, but when i go to the terminal after running setup.py, it says that it cant find my glade file.

which is in the same directory as my script that runs my application, its also in multiple other places that should be right if one was wrong.

After i discovered that it couldnt find the glade file i went back to the directory that i store it in while im developing it, before i executed setup.py. I chucked this in terminal:

```

python myapp.py

```

and it works fine. i then tried running the script that gets put in /usr/local/bin and that also works fine.

Im really stuck so any help would be appreciated, ill post all my application files below.

my setup.py file:
```
#!/usr/bin/env python

from distutils.core import setup
from distutils.cmd import Command
from distutils.command.install_data import install_data
from distutils.command.build import build
from distutils.log import warn, info, error, fatal
import os
import sys
import platform

setup(name='PyTask',
	version='0.1.0',
	description='Task list manager',
	long_description='A simple task list manager but with extra features designed for developers, programmers and teams.',
	author='Ryan Macnish',
	author_email='nisshh@hotmail.com',
	maintainer='Ryan Macnish',
	maintainer_email='nisshh@hotmail.com',
	license='GNU GPL v3',
	url='http://www.launchpad.net/pytask',
	download_url='https://launchpad.net/pytask',
	scripts=['pytask'],
	packages=['pytasklib'],
	package_data={'pytasklib':['gui.glade']},
	data_files=[
		('/usr/local/bin', ['pytasklib/gui.glade']),
		('/usr/share/applications', ['pytask.desktop']),
		('/usr/share/pixmaps', ['icons/pytask.png']),
		],
)
```

my script that goes to /usr/local/bin/:
```
#!/usr/bin/env python

# Copyright 2009 Ryan Macnish
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

# Import all the neccessary modules.

import sys
try:
	import pygtk
	pygtk.require("2.0")
except:
	pass
try:
	import gtk
	import gtk.glade
	import gobject
except:
	sys.exit(1)

from pytasklib.pytask import PyTask
import gui
```

my main application .py file:
```
#!/usr/bin/env python

# Copyright 2009 Ryan Macnish
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

# Import all the neccessary modules.

import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
  	import gobject
except:
	sys.exit(1)

# Define the main pytask class
class PyTask:
	def __init__(self):
		
		# Grab the glade file.
		self.gladefile = "gui.glade"  
		self.wTree = gtk.glade.XML(self.gladefile, "mainWindow") 
			
		# Create the dictionary.
		dic = {"on_mainWindow_destroy" : gtk.main_quit
				, "on_AddTask" : self.OnAddTask
				, "on_RemoveTask" : self.OnRemoveTask
				, "on_EditTask" : self.OnEditTask
				, "on_togglestatusbar_toggled" : self.OnToggleStatusBarToggled
				, "on_toggletoolbar_toggled" : self.OnToggleToolBarToggled
				, "on_about_activate" : self.OnAboutActivate}
		self.wTree.signal_autoconnect(dic)
		
		# Set up some variables and name them.
		self.cTaskObject = 0
		self.cName = 1
		self.cPriority = 2
		self.cDue = 3
		self.cDetails = 4
		
		self.sName = "Name"
		self.sPriority = "Priority"
		self.sDue = "Due"
		self.sDetails = "Details"
				
		# Get the taskview widget from pytask.glade.
		self.taskView = self.wTree.get_widget("taskView")
		
		# Add columns to the treeview.
		self.AddTaskListColumn(self.sName, self.cName)
		self.AddTaskListColumn(self.sPriority, self.cPriority)
		self.AddTaskListColumn(self.sDue, self.cDue)
		self.AddTaskListColumn(self.sDetails, self.cDetails)
	
		# Create the liststore to store the treeview data.
		self.taskList = gtk.ListStore(gobject.TYPE_PYOBJECT
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING)

		self.taskView.set_model(self.taskList)
		
		# Get the statusbar and toolbar widgets from pytask.glade.
		self.statusbar = self.wTree.get_widget("statusbar")
		self.toolbar = self.wTree.get_widget("toolbar")
		
		# get the menu items for the statusbar and toolbar.
		self.statusbarCheck = self.wTree.get_widget("togglestatusbar")
		self.toolbarCheck = self.wTree.get_widget("toggletoolbar")
		
		# Set the initial state of the menu items to toggled on.
		self.statusbarCheck.set_active(True)
		self.toolbarCheck.set_active(True)
	
	# This is needed so that pytask can quit properly.	
	def on_mainWindow_destroy(self, widget):
		gtk.main_quit
		
	# Creates the about dialog and displays it when the OnAboutActivate signal handler is called.
	def OnAboutActivate(self, widget):
		about = gtk.AboutDialog()
		about.set_program_name("PyTask")
		about.set_version("(Under Development)")
		about.set_copyright("Copyright 2009 Ryan Macnish")
		about.set_comments("A simple task list manager but with extra features designed for developers, programmers and teams.")
		about.set_website("https://launchpad.net/pytask")
		about.run()
		about.destroy()
	
	# Show/hide functions for the statusbar and toolbar.
	def OnToggleStatusBarToggled(self, widget):
		if widget.active:
			self.statusbar.show()
		else:
			self.statusbar.hide()
			
	def OnToggleToolBarToggled(self, widget):
		if widget.active:
			self.toolbar.show()
		else:
			self.toolbar.hide()
	
	# Add the columns to the treeview and set their properties.
	def AddTaskListColumn(self, title, columnId):
		column = gtk.TreeViewColumn(title, gtk.CellRendererText()
			, text=columnId)
		column.set_resizable(True)		
		column.set_sort_column_id(columnId)
		self.taskView.append_column(column)
	
	# This is called when the user wants to add a task.
	def OnAddTask(self, widget):
		taskDlg = taskDialog();		
		result,newTask = taskDlg.run()
		
		if (result == gtk.RESPONSE_OK):
			self.taskList.append(newTask.getList())

	# This is called when the user wants to remove a task.
	def OnRemoveTask(self, widget):
		selection = self.taskView.get_selection()
		model, selection_iter = selection.get_selected()
		
		if (selection_iter):
			task = self.taskList.get_value(selection_iter, self.cTaskObject)
			
			self.taskList.remove(selection_iter)
			
	def OnEditTask(self, widget):
		selection = self.taskView.get_selection()
		model, selection_iter = selection.get_selected()
		
		if (selection_iter):
			task = self.taskList.get_value(selection_iter, self.cTaskObject)
			taskDlg = taskDialog(task);
			result,newTask = taskDlg.run()
			
			if (result == gtk.RESPONSE_OK):
				self.taskList.set(selection_iter
					, self.cTaskObject, newTask
					, self.cName, newTask.name
					, self.cPriority, newTask.priority
					, self.cDue, newTask.due
					, self.cDetails, newTask.details)

# The add task dialog is displayed when the OnAddTask signal handler is called.	
class taskDialog:
	def __init__(self, task=None):
		self.gladefile = "gui.glade"
		
		if (task):
			self.task = task
		else:
			self.task = Task()
			
	def run(self):
		self.wTree = gtk.glade.XML(self.gladefile, "taskDlg")
		
		self.dlg = self.wTree.get_widget("taskDlg")
		
		self.enName = self.wTree.get_widget("enName")
		self.enName.set_text(self.task.name)
		self.enPriority = self.wTree.get_widget("enPriority")
		self.enPriority.set_text(self.task.priority)
		self.enDue = self.wTree.get_widget("enDue")
		self.enDue.set_text(self.task.due)
		self.enDetails = self.wTree.get_widget("enDetails")
		self.enDetails.set_text(self.task.details)
		
		self.result = self.dlg.run()
		
		self.task.name = self.enName.get_text()
		self.task.priority = self.enPriority.get_text()
		self.task.due = self.enDue.get_text()
		self.task.details = self.enDetails.get_text()
		
		self.dlg.destroy()
		
		return self.result,self.task

# This then displays the data that was just added to the liststore.
class Task:
	def __init__(self, name="", priority="", due="", details=""):
		self.name = name
		self.priority = priority
		self.due = due
		self.details = details
		
	def getList(self):
		return [self, self.name, self.priority, self.due, self.details]		
		
PyTask()
gtk.main()
```

---

### Post by master_kernel on 2009-07-16
I don't think your glade file is getting packaged. Add a manifest file to the directory setup.py is in called MANIFEST.in. Then in it, write:
```
recursive-include pytasklib *
```

Let me know how it goes.

---

### Post by days_of_ruin on 2009-07-16
I think you need to set the "package_dir". See [http://docs.python.org/distutils/setupscript.html#installing-package-data]("http://docs.python.org/distutils/setupscript.html#installing-package-data")

---

### Post by j7%&lt;RmUg on 2009-07-17
Neither of those suggestions worked, ill post the output when i run my installed application in the terminal:

```
(pytask:27071): libglade-WARNING **: could not find glade file 'gui.glade'
Traceback (most recent call last):
  File "/usr/local/bin/pytask", line 33, in <module>
    from pytasklib.pytask import PyTask
  File "/usr/local/lib/python2.6/dist-packages/pytasklib/pytask.py", line 210, in <module>
    PyTask()
  File "/usr/local/lib/python2.6/dist-packages/pytasklib/pytask.py", line 39, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, "mainWindow") 
RuntimeError: could not create GladeXML object
```

EDIT: I dont think its because its not getting copied, because even if i copy it manually it still says it cant find it.

---

### Post by monraaf on 2009-07-17
Use something like this:

[PHP]
self.gladefile = os.path.join(os.path.dirname(__file__),'gui.glade')
[/PHP]

---

### Post by j7%&lt;RmUg on 2009-07-17
Which file should i put this in? My /usr/local/bin/ script?

---

### Post by mmix on 2009-07-17
you can just use the gtk code instead of glade file.

---

### Post by j7%&lt;RmUg on 2009-07-17
I tried that but i kept running into problems with displaying a dialog box that adds a task to a treeview.

---

### Post by j7%&lt;RmUg on 2009-07-18
BUMP. Can anyone else help? i still cant figure this out.

---

### Post by master_kernel on 2009-07-18
I would also love to see the solution to this. bump.

---

### Post by days_of_ruin on 2009-07-19
```
class PyTask:
	def __init__(self):
		
		# Grab the glade file.
		self.gladefile = os.path.join(os.path.dirname(__file__),"gui.glade")  
		self.wTree = gtk.glade.XML(self.gladefile, "mainWindow") 

```

---

### Post by j7%&lt;RmUg on 2009-07-19
W00t! Got it working!

Ok before i thank the living heck out of you all ill explain what i did:

Using days_of_ruin's suggestion i added that to my code, reran setup.py and typed 'pytask' into the terminal, it worked!

Although it turns out that i had to change another call to the glade file with the same code, now everything works great.

A BIG thankyou to all who offered suggestions, and an even bigger thankyou to days_of_ruin for providing the correct fix.

---

### Post by days_of_ruin on 2009-07-19
btw gtk.glade is deprecated, you should use gtk.Builder instead.

---

### Post by j7%&lt;RmUg on 2009-07-20
Ok thanks ill change that around.

---

