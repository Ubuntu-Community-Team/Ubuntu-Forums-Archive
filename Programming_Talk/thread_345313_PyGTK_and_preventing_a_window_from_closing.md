---
title: "PyGTK and preventing a window from closing?"
date: 2007-01-24
forum: Programming Talk
---

### Post by WakkiTabakki on 2007-01-24
Hi all
How can I intercept a closing signal from a gtk-window and prevent it from closing?
I'd like to pop up an "Unsaved changes! Do you really want to quit?"-message.

I'm using python 2.5 and Glade 3.0.2

Cheers
/N

---

### Post by ssam on 2007-01-24
you need to look at the event the window sends when it is deleted. you need to connect a function to this signal. if this function returns False the the window is destroyed,

have a look at [http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld](http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld)

---

### Post by po0f on 2007-01-24
WakkiTabakki,

Like ssam said, you need to set up a callback for the signal that is emitted when a window is closed (namely, "delete_event").  Inside the callback, just check for the status of a global variable telling you whether the file has been changed or not.

```
[FONT="Courier New"]file_changed = False

# ... blah blah
window.connect('delete_event', on_close)

# ... more blah blah
file_changed = True

# ... blar
def on_close(widget, data):
    if file_changed:
        # dialog popup
        # check return value on the dialog to see if we should
        # return early out of this function (so we don't exit)
    gtk.main_quit()
[/FONT]
```

---

### Post by WakkiTabakki on 2007-01-25
[Edit: Problems solved, but the question why still remains...] 

Thanks for the input.
But, I should have been clearer... The problem isn't really /how/ to do it in that sense (I'm professional programmer since about 10 years, but a complete python/gtk noob).  
I do catch the delete-signal (I was unsure if that was the proper one) and do pop-up the dialog and all, but regardless of what I do in the handler, the window still gets destroyed...

Also, if I try to show the same window twice, the second time the app crashes with the following:
```

Traceback (most recent call last):
  File "main.py", line 89, in __event_rowActivated_List
    self.__editFile(self.CONFIGS_PATH + "/" + sFile)
  File "main.py", line 138, in __editFile
    editor = edit.CEditor()
  File "/home/niklas/devel/myXConf/edit.py", line 48, in __init__
    self.txtSection.get_buffer().connect("changed", self.__on_text_changed)
AttributeError: 'NoneType' object has no attribute 'get_buffer'

```
It seems just as if the object didn't get properly destroyed the first time, and hence doesn't get properly initiate the second time around.
I get the feeling I'm doing something fundamentally wrong somewhere.

This is the start of the file edit.py that causes the crash:
```

#!/usr/bin/env python

import gtk, gtk.glade, gobject, xorg_utils
	
class CEditor:
# Magic for the listview
	COLUMN_CAPTION = 0
# Widgets
	widgets = gtk.glade.XML("editForm.glade")
	lvwSections = None
	lblSection = None
	txtSection = None
	cmdSave = None
# Private variables
	oXorgFile = None # The current xorg_utils.CXorgFile to edit
	sSaveToFilePath = ""
	sCurrentSectionID = None
	bHasChanged = False
	bSwitchingBuffers = False # State flag to indicate that textbox is changing contents due to section change (mouse click) 
	
	# Constructor
	def __init__(self):
		# Init Widgets
		## Listview
		self.lvwSections = self.widgets.get_widget("lvwSections")
		## Label
		self.lblSection = self.widgets.get_widget("lblCurrentSection")
		## Textbox
		self.txtSection = self.widgets.get_widget("txtSection")
		## Save button
		self.cmdSave = self.widgets.get_widget("cmdSave")

		# Connect events
		signals = { \
				'on_lvwSections_cursor_changed' : self.__event_cursorChange,
				'on_cmdSave_clicked' : self.__event_save_pressed,
				'on_EditDialog_delete_event' : self.__event_quit,
				}
		
		self.widgets.signal_autoconnect(signals)
		self.txtSection.get_buffer().connect("changed", self.__on_text_changed)

		
# ####################
# Event Handlers
# ###################
	def __event_quit(self, widget, event):
		print "Caught a quitting event!!!\n"
		print event

		bInhibit = False
		if(self.bHasChanged):
			dialog = gtk.MessageDialog(parent = self.__getRootWindow(), 
							   flags = gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT,
							   type = gtk.MESSAGE_QUESTION, 
							   buttons = gtk.BUTTONS_YES_NO,
							   message_format = "Config file has changed, all changes will be lost!\n\n" + 
									    "Do you really want to close?")

			answer = dialog.run()

			if(answer == gtk.RESPONSE_NO):
				bInhibit = True

			dialog.destroy()

		if(not bInhibit):
			self.__getRootWindow().destroy


```

And this is how I load the window from the main.py window:
```

	# Sends the file for editing (param is a full file path)
	def __editFile(self, p_sFileName):
		oFile = self.m_oXorgParser.parseFile( p_sFileName)		
		editor = edit.CEditor()
		editor.editFile( oFile, p_sFileName)

```
Now, being a Java/C/C++ programmer, I'd really like to write 
```
editor = new edit.CEditor()
```
'cuz to me 
```
editor = edit.CEditor()
```
feels like some kind of built-in singleton-pattern-thing, which would explain the problem with the window not getting properly initialized the second time. But I guess I'm wrong (right?).


Grateful for any input...
/N

---

### Post by WakkiTabakki on 2007-01-25
Well, in the fine old tradition of answering your own posts :roll: 

The problem with the window getting destroyed regardless was a quite a no-brainer... Just return True from the handler to indicate that the signal was taken care of...

The problem with not being able to show the same window twice still remains though... (well, give it a minute and I'll probably answer that aswell... :p )
[Edit: Indeed...]
By doing a hide() instead of destroy() in the delete-event handler, the crash is avoided. But sill, can anyone explain why the CEdit class in edit.py doesn't re-read and initialize the glade file if it has been destroyed and re-created... I just don't get it...

/N

---

