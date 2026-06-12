---
title: "Python: Add backslashes to a sting containing a path"
date: 2014-08-30
forum: Programming Talk
---

### Post by Dave.YNA on 2014-08-30
Hello All,
  I am using python 3 to create a script which trancodes files input from sys.argv using handbrakeCLI. This is so I can create a nautilus script that will enable me to simply right click on a file or bunch of files and convert them to my PS-Vita format. 

It is working great with file paths which contain no spaces. Spaces are causing me a problem 

sys.argv imports each path as a string in a list. The each string contains spaces without the backslash. Therefore when I use the string as an argument for HandBrakeCLI, the path is incorrect. 

So I need to convert the string

/home/dave/PS-Vita/Videos/Community S05 Season 5 Complete x264 AAC E-Subs [GWC]/Community S05E07 HDTV x264 AAC E-Subs.mp4

to 

/home/dave/PS-Vita/Videos/Community\ S05\ Season\ 5\ Complete\ x264\ AAC E-Subs\ [GWC]/Community\ S05E07\ HDTV\ x264\ AAC\ E-Subs.mp4\

Does anyone know an good method for converting the path?

---

### Post by Dave.YNA on 2014-08-30
So far the best approach I can think of is to do 

string.replace(' ', '\\')

Seems to work... Any better suggestions welcome

---

### Post by Vaphell on 2014-08-30
care to post the relevant part of code?

preserving spaces seems easy if you pass a tidy list of arguments

```
>>> import subprocess
>>> subprocess.call( [ "printf", "[%s]\n", "param with space", "another one" ] )
[param with space]
[another one]
0
```

Either way why not use shell scripts? Running stuff and passing paths is literally their job. I can't imagine it being much more complicated than 

```
#!/bin/bash

for f in "$@"
do
   handbrakecli "$f" "converted_$f" # whatever the actual params are
done
```

---

### Post by Dave.YNA on 2014-08-30
> care to post the relevant part of code?

Sure, no problem. 

Here is the full code. Probably a bit overkill but I am trying to learn python so it was a good exercise :)


```


#!/usr/bin/python3.4

from gi.repository import Gtk, GLib
import os
import sys
import subprocess
import io
import threading
import pdb


# Supported Videos for Vita
#&#12288;MPEG-4 Simple Profile Level 3, Maximum 320x240 pixels, AAC
#&#12288;H.264/MPEG-4 AVC Baseline/Main/High Profile Level 3.1, Maximum 720p, AAC

#Script Variables
GLADE_FILE='/home/dave/Documents/Personal/Python/Video Converter/UI.glade'
TRANS_LIST=sys.argv
TRANS_LIST.pop(0)
PROG_LOCATION='/usr/bin/HandBrakeCLI'
OUTPUT_FOLDER='/home/dave/PS-Vita/Videos/'
VITA_EXT='-VITA'
FORMAT='mp4' # -f
VID_ENC='x264' #-e
AUDIO_ENC='faac' #-E
MAX_HEIGHT='544' #--maxHeight
MAX_WIDTH='960' #--maxWidth (note if this doesn't work try something else
QUALITY='24' # -q

###TESTING###
#TRANS_LIST=['Test\ Folder/Screen.mp4', 'Test\ Folder/Vid.mp4']
#TRANS_LIST= ['/home/dave/PS-Vita/Videos/Community\ S05\ Season\ 5\ Complete\ x264\ AAC\ E-Subs\ [GWC]/Community\ S05E07\ HDTV\ x264\ AAC\ E-Subs.mp4']

print(TRANS_LIST[0])
print(PROG_LOCATION)


class UI (object):

 def __init__ (self):
  self.builder = Gtk.Builder()
  self.builder.add_from_file(GLADE_FILE)
  self.builder.connect_signals(self)


 def START_PROCESS(self, *args):
  if not self.TRANS_LIST:
   self.COMPLETE()
  else:
   self.CURRENT_TASK = self.TRANS_LIST[0]
   #Replace is needed for file paths containing spaces. 
   self.CURRENT_TASK = self.CURRENT_TASK.replace(' ', '\\ ')
   #Splitext allows stripping of the file extension
   self.CT_NO_EXT=os.path.splitext(self.CURRENT_TASK)
   self.CT_NO_EXT=self.CT_NO_EXT[0] 
   self.CT_HEAD, self.CT_TAIL = os.path.split(self.CT_NO_EXT)
   LABEL_FILE = self.builder.get_object("label_file")
   LABEL_FILE.set_text("Currently Processing: "+self.CURRENT_TASK)
   self.TRANS_LIST.pop(0)

   self.command_string=str(
		PROG_LOCATION+' -i '+ self.CURRENT_TASK+
		' -o '+OUTPUT_FOLDER+self.CT_TAIL+VITA_EXT+'.'+FORMAT+ 
		' -f '+ FORMAT+
		' -e '+ VID_ENC+
		' -E '+ AUDIO_ENC+
		' -q '+ QUALITY+
		' --maxHeight '+ MAX_HEIGHT+
		' --maxWidth '+ MAX_WIDTH
		)
   print(self.command_string)
   self.Transcode = subprocess.Popen(self.command_string,
	shell=True,
	stdout=subprocess.PIPE, 
	stderr=subprocess.STDOUT
	) 

   GLib.io_add_watch(self.Transcode.stdout,
		 GLib.IO_IN,
		 self.write_to_buffer)
  
   PID = self.Transcode.pid
   GLib.child_watch_add(PID, self.FIN_PROCESS)

   #The gobject.child_watch_add() function sets the function specified by
   #function to be called with the user data specified by data when 
   #the child indicated by pid exits.


 def FIN_PROCESS(self, *args):
  self.OVERVIEW = self.builder.get_object("textview_overview").get_buffer()
  self.OVERVIEW.insert_at_cursor('[Completed]: ')
  self.OVERVIEW.insert_at_cursor(self.CURRENT_TASK+'\n')
  self.START_PROCESS()  
 
 def write_to_buffer(self, fd, condition):
  if condition == GLib.IO_IN: 
   char = fd.read(1).decode()
   # .decode() converts the bytes to str.
   buf = self.builder.get_object("textview").get_buffer()
   buf.insert_at_cursor(char)	
   #print(char)
   return True
  else:
   return False 

#------Main Window ------------------------------

 def run(self, *args):
  self.main_win = self.builder.get_object("window_main").show()
  Gtk.main()
 
 def on_window_main_show(self, *args):
  self.TRANS_LIST = TRANS_LIST
  self.START_PROCESS()

 #This function makes the scroll bar automatically focus at the bottom
 #It takes the signal from text view to allocate the size
 def on_textview_size_allocate(self, *args):
  win = self.builder.get_object("scrolledwindow")
  adj = win.get_vadjustment()
  adj.set_value(adj.get_upper() - adj.get_page_size()) 

 def on_window_main_delete_event(self, *args):
  self.Transcode.Status = self.Transcode.poll()
  if self.Transcode.Status == None:
   self.WARNING()
   return True
  else:
   Gtk.main_quit()

  #The delete-event is called when clicking on the close icon
  #If you the delete-event returns true, it is not sent.
  #previously I used on_window_main_destroy but that closed the window
  #as I beleive that then sends a delete-event too.


#-----WARNING WINDOW ----------------------------

 def WARNING(self, *args):
  self.warn_win = self.builder.get_object("warning_diag")
  self.warn_win.show()

 def on_warning_action_area_destroy(self, *args):
  self.warn_win.hide()

 def on_warning_quit_clicked(self, *args):
  self.Transcode.kill()
  self.warn_win.destroy()
  Gtk.main_quit()

 def on_warning_continue_clicked(self, *args):
  self.warn_win.hide()

#-----COMPLETE WINDOW ---------------------------

 def COMPLETE(self, *args):
  self.comp_win = self.builder.get_object("complete_diag")
  self.comp_win.show()
  
 def on_complete_quit_clicked(self, *args):
  self.comp_win.destroy()
  Gtk.main_quit()
  

UI().run()



```

---

### Post by Vaphell on 2014-08-30
shell=False and you won't have to escape anything, just pass the list of args, not a constructed string.

---

### Post by Dave.YNA on 2014-08-30
Thanks Vaphell. Appreciate the input. 

Orignally I had shell=false and was passing the arguments as a list. Then I changed it to a long string for some reason. Now I can't remember what the reason was! 

hmm...

---

