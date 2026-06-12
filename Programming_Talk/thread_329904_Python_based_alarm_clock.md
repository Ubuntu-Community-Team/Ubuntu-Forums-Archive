---
title: "Python based alarm clock"
date: 2007-01-02
forum: Programming Talk
---

### Post by mordox on 2007-01-02
I have made a small alarm clock using python and gtk. If you feel interested you can get it at [http://abuccaneer.googlepages.com/pyalarmclock](http://abuccaneer.googlepages.com/pyalarmclock)

I am also working on python based frontend for mplayer ... having library support . 
It will be complete in a few days.... Hoping tht it would be useful.. atleast it will be for me ! :D

---

### Post by Omnios on 2007-01-18
Very nice. You might want to check this out kuz I think it has python script ability.

---

### Post by mordox on 2007-01-18
thanks ! 

what is the link ? that u r refering . 

Also, Cud u help me out with this > [http://ubuntuforums.org/showthread.php?t=340238](http://ubuntuforums.org/showthread.php?t=340238)

---

### Post by Omnios on 2007-01-18
> **Omnios said:**
> Very nice. You might want to check this out kuz I think it has python script ability.


[http://ubuntuforums.org/showthread.php?t=183709](http://ubuntuforums.org/showthread.php?t=183709)

 SOrry about that I was having a lot of computer problems yesterday.

---

### Post by adelgado on 2007-11-26
I was about to start one project of a PyGTK-based alarm. Thanks for sharing it!

However, there are some problems:

&#8213; I can't chose the command that'll be executed.
&#8213; The ID gets wrong after a few messing around. And I think it's useless, given that we already have a Task Name.
&#8213; I think it would be better to select the time from a spinbutton rather than from a normal button.
&#8213; The included command does not work for me. It just opens a Terminal and puts it in forever-looping.

Of course, I am not just going to criticize your good work:

Would you consider merging some of the changes in case I post the code here?


Thanks for starting it, man!

---

### Post by adelgado on 2007-11-26
Why is your code divided in BaseWindow and MyWindow?

---

### Post by mordox on 2007-11-26
thanks :)


well now to the questions


Q:  I can't chose the command that'll be executed.
A:  You can just change the mplayer.sh file

Q: The ID gets wrong after a few messing around. And I think it's useless, given that we already have a Task Name.
A: It's a matter of personal preference, neways i'll post an update soon
Q: I think it would be better to select the time from a spinbutton rather than from a normal button.
A: Ya, that is true, but when I wrote this I was just learning. Point noted updated package will soon add this.
Q: The included command does not work for me. It just opens a Terminal and puts it in forever-looping.
A: That's maybe because you don't have test.mp3 which is hard coded in the Alarm.py . Missed to add it in the README.


well when i wrote this small alarm clock, I really didn't have any sort of architecture in place, i just started coding and here is what i have. 
so there maybe some bugs.. but i am really happy that it is helpful so some 1. :guitar:

---

### Post by mordox on 2007-11-26
Update released: 
[http://abuccaneer.googlepages.com/pyalarmclock](http://abuccaneer.googlepages.com/pyalarmclock)

Download:
[http://abuccaneer.googlepages.com/pyAlarmClock-u2.tar.gz](http://abuccaneer.googlepages.com/pyAlarmClock-u2.tar.gz)

:guitar:

---

### Post by tjagoda on 2007-11-27
Nice clock!

I'm just begining to learn python, and I think this is a good example to try to break and fix in my educational pursuit.  :)

---

### Post by adelgado on 2007-11-27
Wow, THAT was fast!

---

### Post by adelgado on 2007-11-27
The removal of the ID caused a bug with the Remove button:

```

Traceback (most recent call last):
  File "/home/elros/Programming/Python/pyAlarmClock (2)/basewindow.py", line 254, in btnDel_click
    delID = int(model.get_value(iterx,0))
ValueError: invalid literal for int() with base 10: ''

```


Since I do not yet understand the code fully, I'll use the version 1 while doing my coding... I think the bug has to do with the removal of the ID column...

---

### Post by adelgado on 2007-11-27
I merged all the files and the MyWindow and BaseWindow classes into a class named Window.

Here's the source code:


```

#!/usr/bin/env python
# --- File pyAlarmClock.py

import pygtk
import threading
import time
import datetime
import gobject
import os
import re
import getopt
import gtk
import sys

pygtk.require('2.0')


class Window:
	def delete_event(self, widget, event, data=None):
		print "Delete Event Occured"
		return False

	def self_destroy(self, widget, data=None):
		gtk.main_quit()
	
	def name_edited(self, cell, path_string, new_text, model):
		iterx = model.get_iter_from_string(path_string)
		col = cell.get_data("column")
		print new_text
		model.set(iterx,col,new_text)

	def __init__(self):
		print "BaseWindow __init__"
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.connect("delete_event",self.delete_event)
		self.window.connect("destroy",self.self_destroy)
		# window init done
		
		self.btnAdd = gtk.Button(stock=gtk.STOCK_ADD)
		self.btnDel = gtk.Button(stock=gtk.STOCK_REMOVE)
		self.btnClear = gtk.Button(stock=gtk.STOCK_CLEAR)
		self.btnSave = gtk.Button(stock=gtk.STOCK_SAVE)

		self.liststore = gtk.ListStore(str,str,str,bool)
		self.listview = gtk.TreeView(self.liststore)
		self.listview.set_size_request(300,-1)

		self.cellRender = gtk.CellRendererText()
		self.cellRender_edit = gtk.CellRendererText()
		self.cellRender_edit.connect("edited",self.name_edited,self.liststore)
		self.cellRender_edit.set_data("column",int(1))
		self.tvcolumn = gtk.TreeViewColumn("ID",self.cellRender,text=0)
		self.tvcolumn2 = gtk.TreeViewColumn("Name",self.cellRender_edit,text=1,editable=3)
		self.tvcolumn3 = gtk.TreeViewColumn("Time",self.cellRender,text=2)
		self.tvcolumn2.set_resizable(True)
		self.tvcolumn3.set_resizable(True)
		self.listview.append_column(self.tvcolumn)
		self.listview.append_column(self.tvcolumn2)
		self.listview.append_column(self.tvcolumn3)				
		
		self.scrlTree = gtk.ScrolledWindow()
		self.scrlTree.add(self.listview)
		
		self.lblHr = gtk.Label("Hour: ")
		self.lblMin = gtk.Label("Minute: ")
		self.lblName = gtk.Label("Name: ")
		self.lblTicker = gtk.Label("Time Now Is: ")
		self.lblTicker.set_markup("<span size=\"xx-large\">XXX</span>")
		
		self.txtHr = gtk.Entry(2)
		self.txtMin = gtk.Entry(2)
		self.txtName = gtk.Entry()
		self.txtHr.set_size_request(30,-1)
		self.txtMin.set_size_request(30,-1)
		
		self.vboxmain = gtk.VBox()
		self.hpane_tree_cal_time = gtk.HPaned()
		self.vbox_cal_time = gtk.VBox()
	
		self.hbox_btn = gtk.HBox(False)
		self.hbox_time = gtk.HBox()
		self.calendar = gtk.Calendar()
		
		self.vboxmain.pack_start(self.hpane_tree_cal_time,True,True,2)
		self.vboxmain.pack_start(self.hbox_btn,False,False,2)
		
		self.hpane_tree_cal_time.pack1(self.scrlTree,True,True)
		self.hpane_tree_cal_time.pack2(self.vbox_cal_time,True,True)
		
		self.vbox_cal_time.pack_start(self.lblTicker,False,False,2)
		self.vbox_cal_time.pack_start(self.calendar,True,True,2)
		self.vbox_cal_time.pack_start(self.hbox_time,False,False,2)
		
		self.hbox_time.pack_start(self.lblName,False,False,2)
		self.hbox_time.pack_start(self.txtName,True,True,2)
		self.hbox_time.pack_start(self.lblHr,False,False,2)
		self.hbox_time.pack_start(self.txtHr,True,True,2)
		self.hbox_time.pack_start(self.lblMin,False,False,2)
		self.hbox_time.pack_start(self.txtMin,True,True,10)
		

		self.hbox_btn.pack_start(self.btnAdd,False,False,2)
		self.hbox_btn.pack_start(self.btnDel,False,False,2)
		self.hbox_btn.pack_start(self.btnClear,False,False,2)
		self.hbox_btn.pack_end(self.btnSave,False,False,2)

		self.window.add(self.vboxmain)
		self.window.show_all()

#		print "MyWindow __init__"
		self.alarmList = []
		self.txtName.set_text("Alarm#" + repr(alarm_id_nodupl +1 ) )
		self.update_time = UpdateTime(self.lblTicker,self.alarmList)
		self.update_time.start()
		self.keepRunning = True		

		self.btnAdd.connect("clicked", self.btnAdd_clicked,None)
		self.btnDel.connect("clicked", self.btnDel_clicked,None)
		self.btnSave.connect("clicked", self.save_settings,None)
		self.btnClear.connect("clicked",self.goClear)		
		self.txtHr.set_text(time.strftime("%H",time.localtime()))
		self.txtMin.set_text(time.strftime("%M",time.localtime()))
		self.txtName.grab_focus()

#class MyWindow(BaseWindow):

	def load_settings(self):
		sFile = os.getenv('HOME')	
		if sFile == None:
			sFile = ""
		if os.access(sFile,os.F_OK | os.R_OK | os.W_OK) == False:
			print "Cannot Access Home Directory"
			gtk.MessageDialog(None,0,gtk.MESSAGE_ERROR,gtk.BUTTONS_NONE,"Cannot Access Home Directory").show()
		sFile = sFile + os.sep + ".alarm" + os.sep
		if os.access(sFile,os.F_OK) ==  False:
			os.mkdir(sFile)
			print "Created Config Directory.. " + sFile
		sFile = sFile + "config"
		
		if os.access(sFile,os.F_OK) == True:	# If config exists !
			fIn = open(sFile,'r')
			fData = fIn.readlines()
			for line in fData:
				nm, mtime, mdate= re.split(",", line)
				hr, mn  = re.split(":",mtime)
				dy, mth, yr  = re.split("/",mdate)
				new_al = Alarm(yr,mth,dy, hr, mn )
				self.alarmList.append(new_al)					# Update AlarmList
				new_al.setName(nm)
		
				newRow = self.liststore.append()				# Add to list
				self.liststore.set(newRow,0,repr(new_al.id),1,(new_al.myName),2,new_al.getAlarm(),3,True)
				# Add Alarm Done
			fIn.close()
			print "Loaded " + sFile		
			
			
	def save_settings(self,widget,data=None):
		sFile = os.getenv('HOME')	
		if sFile == None:
			sFile = ""
		if os.access(sFile,os.F_OK | os.R_OK | os.W_OK) == False:
			print "Cannot Access Home Directory"
			gtk.MessageDialog(None,0,gtk.MESSAGE_ERROR,gtk.BUTTONS_NONE,"Cannot Access Home Directory").show()
		sFile = sFile + os.sep + ".alarm" + os.sep
		if os.access(sFile,os.F_OK) ==  False:
			os.mkdir(sFile)
			print "Created Config Directory.. " + sFile
		sFile = sFile + "config"
		fConf = open(sFile ,'w')
		mdl = self.listview.get_model()
		iterx = mdl.get_iter_first()
		while iterx:
			iID = int(mdl.get_value(iterx,0))
			iName = mdl.get_value(iterx,1)
			iTime ,iDate = re.split(" " , mdl.get_value(iterx,2))
			print "Saving " + " " + iName + " " + iDate
			fConf.write(iName + "," + iTime + "," + iDate + "\n")
			iterx = mdl.iter_next(iterx)
		fConf.close()
	
	def goClear(self,widget,data=None):
		self.liststore.clear()
		self.update_time.alRef = []
		self.alarmList = []
		
	def self_destroy(self,widget,data=None):
		self.update_time.keepRunning = False
		self.update_time.join(2)
		self.keepRunning = False
	
	
	
	
	def btnAdd_clicked(self,widget,data=None):
#		print "btnAdd 2 click ",
		dt = self.calendar.get_date()
		hr = int(self.txtHr.get_text())
		mn = int(self.txtMin.get_text())
		if hr<0 or hr > 23:
			print "Wrong Hr"
			return
		if mn<0 or mn > 59:
			print "Wrong Min"
			return
		new_al = Alarm(dt[0],dt[1]+1,dt[2], hr, mn )
		self.alarmList.append(new_al)					# Update AlarmList
		new_al.setName(self.txtName.get_text())
		
		newRow = self.liststore.append()				# Add to list
		self.liststore.set(newRow,0,repr(new_al.id),1,(new_al.myName),2,new_al.getAlarm(),3,True)
		# Add Alarm Done
		self.txtName.set_text("Alarm#" + repr(alarm_id_nodupl +1 ) )

		
	def btnDel_clicked(self,widget,data=None):
#		print "btnDel2 click " , 
		selection = self.listview.get_selection()
		model, iterx = selection.get_selected()
		if iterx:
#			path = model.get_path(iterx)[0] 		Not Used
			delID = int(model.get_value(iterx,0))
			model.remove(iterx)
			for i in range(len(self.alarmList)):
				print self.alarmList[i].id , " " , delID
				if self.alarmList[i].id == delID:	# Seek to the deleted alarm object 
					del self.alarmList[i]			# Delete it
					break
			print "Len: ", len(self.alarmList)

	
	def main(self):
		self.load_settings()
		while(self.keepRunning):
			while(gtk.events_pending()):
				gtk.main_iteration()
			time.sleep(0.1)


class UpdateTime(threading.Thread):
	def __init__(self,lblWin,al):
		threading.Thread.__init__(self)
		self.lblRef = lblWin
		self.keepRunning = True
		self.alRef = al
		
	def run(self):
		print "Started Time Updater"
		while(self.keepRunning):
#			self.lblRef.set_text(time.strftime("Time is: %H : %M : %S",time.localtime()))
			self.lblRef.set_markup("<span font_family=\"monospace \" size=\"50000\" >" + time.strftime(" %H:%M",time.localtime()) + "<span rise=\"2000\" size=\"15000\" foreground=\"#FF0000\">" + 	time.strftime("     [%S]",time.localtime()) + "</span></span>")
			print len(self.alRef)
			for i in range(0,len(self.alRef)):
				try:
					if self.alRef[i].isNotDone and self.alRef[i].isAlarm(): # Check for Alarm
						self.alRef[i].doAlarm()								# Raise Alarm
						self.alRef.pop(i)									# Erase Done Alarm
				except IndexError:
					break
			time.sleep(1)
		print "End Time Updater"
		

#############################################


alarm_id_nodupl = 0
exec_string = '/usr/bin/gnome-terminal'
path = sys.argv[0]
parampath = path[0:path.rfind(os.sep)]
param_string = ["-e " + parampath + os.sep + "mplayer.sh " + parampath + os.sep + "test.mp3","-e " + parampath + os.sep + "mplayer.sh " + parampath + os.sep + "test.mp3" ]

print param_string

class Alarm:
	def __init__(self,dt_yr,dt_mn,dt_dy,hr,mn):
		global alarm_id_nodupl
		self.date_day = int(dt_dy)
		self.date_month = int(dt_mn)
		self.date_year = int(dt_yr)
		self.hour = int(hr)
		self.minute = int(mn)
		self.myName="Alarm!!"
		self.isNotDone = True
		alarm_id_nodupl = alarm_id_nodupl + 1
		self.id = alarm_id_nodupl
		self.keepRunning = True
	def getAlarm(self):
		s = repr(self.hour) + ":" + repr(self.minute) + " " + \
		repr(self.date_day) + "/" + repr(self.date_month) + "/" + \
		repr(self.date_year)
		return s
		
	def setName(self,name):
		self.myName=name
		
	def isAlarm(self):
		cDay = datetime.date.today().day
		cMonth = datetime.date.today().month 
		cYear =  datetime.date.today().year
		cDay =  datetime.date.today().day
		cHour = int(time.strftime("%H",time.localtime()))
		cMinute = int(time.strftime("%M",time.localtime()))
#		print self.hour
		if cHour == self.hour and cMinute == self.minute \
		and self.date_day == cDay \
		and self.date_month == cMonth \
		and self.date_year == cYear:
			return True
		return False
	
	def doAlarm(self):
		print self.id, " " , self.myName
#		os.spawnvpe(os.P_WAIT,'mplayer','mplayer test.wav',os.environ)	
#		os.system(exec_string)
		os.spawnv(os.P_NOWAIT,exec_string,param_string)
		self.isNotDone = False


wMain = Window()
wMain.window.set_title("pyAlarmClock")
wMain.main()

```

---

### Post by adelgado on 2007-11-27
I changed the Window.load_settings() and the Window.save_settings() functions.

Here it goes:

```

	def load_settings(self):
		"""Loads the settings of the Alarm from a predefined file. Default: $HOME/.alarm/config"""	

		#Check if $HOME exists
		if (os.getenv('HOME') == None):
			sFile = "" + ".alarm" + os.sep + "config"
		else:
			sFile = os.getenv('HOME') + os.sep + ".alarm" + os.sep + "config"

		#Checks if settings file exists, is readable and writable
		if os.access(sFile, os.F_OK | os.R_OK):
			#If it is, load the contents of the file
			sData = open(sFile, 'r')
			try:
				for line in sData.readlines():
					name, time, date = re.split(",", line)
					hour, minute = re.split(":", time)
					day, month, year = re.split("/", date)
					new_al = Alarm(year, month, day, hour, minute)
					self.alarmList.append(new_al)
					new_al.setName(name)
					newRow = self.liststore.append()
					self.liststore.set(newRow, 0, repr(new_al.id), 1, (new_al.myName), 2, new_al.getAlarm(), 3, True)
			finally:
				sData.close()
			print "Loaded " + sFile
		else:
			#If it doesn't or isn't, issue an error
			print "Cannot access Home directory"
			gtk.MessageDialog(None, 0, gtk.MESSAGE_ERROR,gtk.BUTTONS_NONE, "Cannot access Home directory!").show()

		#----- Window.loadsettings() ends


	def save_settings(self, widget, data=None):
		"""Saves the settings of the Alarm to a predefined file. Default: $HOME/.alarm/config"""

		#Check if $HOME exists
		if (os.getenv('HOME') == None):
			sFile = "" + ".alarm" + os.sep + "config"
		else:
			sFile = os.getenv('HOME') + os.sep + ".alarm" + os.sep + "config"

		#Creates the settings file if it doesn't exists
		if os.access(sFile, os.F_OK) == False:
			os.mkfile(sFile)
		
		#Checks if the settings file is readable and writable
		if os.access(sFile, os.R_OK | os.W_OK):
			#If it is, writes the alarms to the file
			sData = open(sFile, 'w')
			try:
				mdl = self.listview.get_model()
				iterx = mdl.get_iter_first()
				while iterx:
					iID = int(mdl.get_value(iterx, 0))
					iName = mdl.get_value(iterx, 1)
					iTime, iDate = re.split(" " , mdl.get_value(iterx, 2))
					print "Saving " + " " + iName + " " + iDate
					sData.write(iName + "," + iTime + "," + iDate + "\n")
					iterx = mdl.iter_next(iterx)
			finally:
				sData.close()
		else:
			#If the file isn't readable or writable, issue an error
			print "Error while saving settings: the settings file may be unreadable or unwritable."

		#----- Window.save_settings() ends

```

I'll change more stuff when I have time ;D

Greetings!

---

