---
title: "Cant get launchpadlib working in my application"
date: 2009-10-29
forum: Programming Talk
---

### Post by j7%&lt;RmUg on 2009-10-29
Hey,
I cant get launchpadlib to work with my application, heres the code first:
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

try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
  	import gobject
  	import os
  	import shelve
  	import sys
	from launchpadlib.launchpad import Launchpad, STAGING_SERVICE_ROOT
	from launchpadlib.credentials import Credentials
except:
	sys.exit(1)
	
FILE_EXT = "task"
addmsg = "Task added"
removemsg = "Task removed"
editmsg = "Task Edited"

class PyTask:
	def __init__(self):
		
		self.gladefile = os.path.join(os.path.dirname(__file__),"gui.glade")
		self.wTree = gtk.glade.XML(self.gladefile, "mainWindow")
		
		dic = {"on_mainWindow_destroy" : gtk.main_quit
				, "on_show_error" : self.ShowError
				, "on_AddTask" : self.OnAddTask
				, "on_RemoveTask" : self.OnRemoveTask
				, "on_EditTask" : self.OnEditTask
				, "on_file_new" : self.OnFileNew
				, "on_file_save" : self.OnFileSave
				, "on_file_open" : self.OnFileOpen
				, "on_togglestatusbar_toggled" : self.OnToggleStatusBarToggled
				, "on_toggletoolbar_toggled" : self.OnToggleToolBarToggled
				, "on_about_activate" : self.OnAboutActivate
				, "on_LaunchpadAuth" : self.OnLaunchpadAuth
				, "launchpad_login_get_credentials" : self.LaunchpadLoginGetCredentials
				, "launchpad_login_from_credentials" : self.LaunchpadLoginFromCredentials
				, "save_credentials" : self.SaveCredentials}
		self.wTree.signal_autoconnect(dic)
		
		self.cTaskObject = 0
		self.cName = 1
		self.cPriority = 2
		self.cDue = 3
		self.cStatus = 4
		self.cDetails = 5
		
		self.sName = "Name"
		self.sPriority = "Priority"
		self.sDue = "Due"
		self.sStatus = "Status"
		self.sDetails = "Details"
		
		self.project_file = ""
		
		self.taskView = self.wTree.get_widget("taskView")
		
		self.AddTaskListColumn(self.sName, self.cName)
		self.AddTaskListColumn(self.sPriority, self.cPriority)
		self.AddTaskListColumn(self.sDue, self.cDue)
		self.AddTaskListColumn(self.sStatus, self.cStatus)
		self.AddTaskListColumn(self.sDetails, self.cDetails)
		
		self.taskList = gtk.ListStore(gobject.TYPE_PYOBJECT
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING
			, gobject.TYPE_STRING)

		self.taskView.set_model(self.taskList)
		
		self.statusbar = self.wTree.get_widget("statusbar")
		self.toolbar = self.wTree.get_widget("toolbar")
		
		self.statusbarCheck = self.wTree.get_widget("togglestatusbar")
		self.toolbarCheck = self.wTree.get_widget("toggletoolbar")
		
		self.statusbarCheck.set_active(True)
		self.toolbarCheck.set_active(True)
		
		credentials = Credentials()
		cachedir = "~/.launchpadlib/cache/"
		
	def on_mainWindow_destroy(self, widget):
		gtk.main_quit
		
	def ShowError(self, error_string):
		error = gtk.MessageDialog(type=gtk.MESSAGE_ERROR
			, message_format=error_string
			, buttons=gtk.BUTTONS_OK)
		error.run()
		error.destroy()
		
	def OnAboutActivate(self, widget):
		about = gtk.AboutDialog()
		about.set_program_name("PyTask")
		about.set_version("0.2.0")
		about.set_copyright("Copyright 2009 Ryan Macnish")
		about.set_comments("A simple task list manager but with extra features designed for developers, programmers and teams.")
		about.set_website("https://launchpad.net/pytask")
		about.run()
		about.destroy()
		
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
		
	def AddTaskListColumn(self, title, columnId):
		column = gtk.TreeViewColumn(title, gtk.CellRendererText()
			, text=columnId)
		column.set_resizable(True)		
		column.set_sort_column_id(columnId)
		self.taskView.append_column(column)
		
	def OnAddTask(self, widget):
		taskDlg = taskDialog();		
		result,newTask = taskDlg.run()
		
		if (result == gtk.RESPONSE_OK):
			self.taskList.append(newTask.getList())
			
			self.statusbar.pop(0)
			self.statusbar.pop(1)
			self.statusbar.pop(2)
			
			self.statusbar.push(0, addmsg)
		
	def OnRemoveTask(self, widget):
		selection = self.taskView.get_selection()
		model, selection_iter = selection.get_selected()
		
		if (selection_iter):
			task = self.taskList.get_value(selection_iter, self.cTaskObject)
			
			self.taskList.remove(selection_iter)
			
			self.statusbar.pop(0)
			self.statusbar.pop(1)
			self.statusbar.pop(2)
			
			self.statusbar.push(1, removemsg)
			
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
					, self.cStatus, newTask.status
					, self.cDetails, newTask.details)
					
				self.statusbar.pop(0)
				self.statusbar.pop(1)
				self.statusbar.pop(2)
				
				self.statusbar.push(2, editmsg)
					
	def file_browse(self, dialog_action, file_name=""):
		if (dialog_action==gtk.FILE_CHOOSER_ACTION_OPEN):
			dialog_buttons = (gtk.STOCK_CANCEL
				, gtk.RESPONSE_CANCEL
				, gtk.STOCK_OPEN
				, gtk.RESPONSE_OK)
		else:
			dialog_buttons = (gtk.STOCK_CANCEL
				, gtk.RESPONSE_CANCEL
				, gtk.STOCK_SAVE
				, gtk.RESPONSE_OK)
				
		file_dialog = gtk.FileChooserDialog(title="Select Project"
			, action=dialog_action
			, buttons=dialog_buttons)
			
		if (dialog_action==gtk.FILE_CHOOSER_ACTION_SAVE):
			file_dialog.set_current_name(file_name)
			
		filter = gtk.FileFilter()
		filter.set_name("PyTask files")
		filter.add_pattern("*." + FILE_EXT)
		file_dialog.add_filter(filter)
		
		filter = gtk.FileFilter()
		filter.set_name("All files")
		filter.add_pattern("*")
		file_dialog.add_filter(filter)
		
		result = ""
		
		if file_dialog.run() == gtk.RESPONSE_OK:
			result = file_dialog.get_filename()
		file_dialog.destroy()
		
		return result
		
	def OnFileNew(self, widget):
		self.taskList.clear()
					
	def OnFileSave(self, widget):
		save_file = self.file_browse(gtk.FILE_CHOOSER_ACTION_SAVE, self.project_file)
		
		if (save_file != ""):
			save_file, extension = os.path.splitext(save_file)
			save_file = save_file + "." + FILE_EXT
			
			db = shelve.open(save_file, "n")
			
			iter = self.taskList.get_iter_root()
			
			while (iter):
				task = self.taskList.get_value(iter, self.cTaskObject)
				db[self.taskList.get_string_from_iter(iter)] = task
				iter = self.taskList.iter_next(iter)
			db.close()
			root, self.project_file = os.path.split(save_file)
			
	def OnFileOpen(self, widget):
		open_file = self.file_browse(gtk.FILE_CHOOSER_ACTION_OPEN)
		
		if (open_file != ""):
		
			try:
				db = shelve.open(open_file, "r")
				
				if (db):
					self.taskList.clear()
					count = 0;
					
					while db.has_key(str(count)):
						newtask = db[str(count)]
						self.taskList.append(newtask.getList())
						count = count +1
					db.close()
					root, self.project_file = os.path.split(open_file)
					
				else:
					self.ShowError("Error opening file")
					
			except:
				self.ShowError("Error opening file")
				
	def OnLaunchpadAuth(self, widget):
		lpDlg = lpDialog();
		lpDlg.run()
		
	def LaunchpadLoginGetCredentials(self, widget):
		launchpad = Launchpad.get_token_and_login("pytask", STAGING_SERVICE_ROOT, cachedir)
		
	def LaunchpadLoginFromCredentials(self, widget):
		credentials.load(open("~/.launchpadlib/pytask-credentials.txt"))
		launchpad = Launchpad(credentials, STAGING_SERVICE_ROOT, cachedir)
		
	def SaveCredentials(self, widget):
		launchpad.credentials.save(file("~/.launchpadlib/pytask-credentials.txt", "w"))
		
class lpDialog:
	def __init__(self):
		self.gladefile = os.path.join(os.path.dirname(__file__),"gui.glade")
		
	def run(self):
		self.wTree = gtk.glade.XML(self.gladefile, "lpDlg")
		
		self.dlg = self.wTree.get_widget("lpDlg")
		
		self.result = self.dlg.run()
		
		self.dlg.destroy()
		
		return self.result

class taskDialog:
	def __init__(self, task=None):
		self.gladefile = os.path.join(os.path.dirname(__file__),"gui.glade")
		
		if (task):
			self.task = task
		else:
			self.task = Task()
			
	def run(self):
		self.wTree = gtk.glade.XML(self.gladefile, "taskDlg")
		
		self.dlg = self.wTree.get_widget("taskDlg")
		
		self.enName = self.wTree.get_widget("enName")
		self.enName.set_text(self.task.name)
		self.cbPriority = self.wTree.get_widget("cbPriority")
		self.cbPriority.set_active(2)
		self.enDue = self.wTree.get_widget("enDue")
		self.enDue.set_text(self.task.due)
		self.cbStatus = self.wTree.get_widget("cbStatus")
		self.cbStatus.set_active(2)
		self.enDetails = self.wTree.get_widget("enDetails")
		self.enDetails.set_text(self.task.details)
		
		self.result = self.dlg.run()
		
		self.task.name = self.enName.get_text()
		self.task.priority = self.cbPriority.get_active_text()
		self.task.due = self.enDue.get_text()
		self.task.status = self.cbStatus.get_active_text()
		self.task.details = self.enDetails.get_text()
		
		self.dlg.destroy()
		
		return self.result,self.task

class Task:
	def __init__(self, name="", priority="", due="", status="", details=""):
		self.name = name
		self.priority = priority
		self.due = due
		self.status = status
		self.details = details
		
	def getList(self):
		return [self, self.name, self.priority, self.due, self.status, self.details]		
		
PyTask()
gtk.main()
```

The problem im having is that when i go to click on a button to login to launchpad in my application, which should execute this function:

```

def LaunchpadLoginGetCredentials(self, widget):
launchpad = Launchpad.get_token_and_login("pytask", STAGING_SERVICE_ROOT, cachedir)

```

Which should then open a browser window and ask the user to login and grant access to my application, it doesnt do anything and python reports no errors.

This has me stumped as to why it wont work, iv read and re-read the API docs for launchpadlib. Iv done heaps of button code before this.

Would greatly appreciate some help here. Thanks in advance.

---

### Post by j7%&lt;RmUg on 2009-10-30
BUMP, still cant figure this one out.

---

### Post by j7%&lt;RmUg on 2009-11-01
BUMP, i really need help with this, i have gone over and over the lplib docs on launchpad, they arent able to help me one bit with this issue, also if i split my launchpad code into a seperate file then it runs fine, i think im going to try creating a new app that just auths with launchpad, then ill merge that with pytask.

---

