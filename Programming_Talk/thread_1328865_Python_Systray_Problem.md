---
title: "Python Systray Problem"
date: 2009-11-16
forum: Programming Talk
---

### Post by ctult on 2009-11-16
I am trying to create a Python program, but every time I run it, it gives me this error:

```
  File "systray.py", line 9
    stat=blinkity.staticon.get_blinking()
                                        ^
IndentationError: unindent does not match any outer indentation level

```

Here is my program:

```

#!/usr/bin/python

import gtk

class StatusIcc:

    # activate callback
    def activate( self, widget, data=None):
  stat=blinkity.staticon.get_blinking()

  if stat = 'True':
   blinkity.staticon.set_blinking(False)
  else:
    blinkity.staticon.set_blinking(True)

   # Show_Hide callback
    def  show_hide(self, widget,response_id, data= None):
        if response_id == gtk.RESPONSE_YES:
                widget.hide()
        else:
                widget.hide()

    # destroyer callback
    def  destroyer(self, widget,response_id, data= None):
        if response_id == gtk.RESPONSE_OK:
                gtk.main_quit()
        else:
                widget.hide()

    # popup callback
    def popup(self, button, widget, data=None):
        dialog = gtk.MessageDialog(
        parent         = None,
        flags          = gtk.DIALOG_DESTROY_WITH_PARENT,
        type           = gtk.MESSAGE_INFO,
        buttons        = gtk.BUTTONS_OK_CANCEL,
        message_format = "Do you want to close this Status Icon program?")
        dialog.set_title('Popup Window')
        dialog.connect('response', self.destroyer)
        dialog.show()

    def __init__(self):
        # create a new Status Icon
        self.staticon = gtk.StatusIcon()
        self.staticon.set_from_file("yellowled.png")
        self.staticon.set_blinking(True)
        self.staticon.connect("activate", self.activate)
        self.staticon.connect("popup_menu", self.popup)
        self.staticon.set_visible(True)

    self *= blinkity

        # invoking the main()
        gtk.main()

if __name__ == "__main__":
    statusicon = StatusIcc() 

```

---

### Post by Can+~ on 2009-11-16
[FONT="Courier New"]IndentationError[/FONT]

Seriously, doesn't that error give you any clue? Python uses whitespace as logical segments, you should format your code properly.

Either use tabs (discouraged), or 4-spaces for indentation:

[PHP]#!/usr/bin/python

import gtk

class StatusIcc:
	
	# activate callback
	def activate( self, widget, data=None):
		stat=blinkity.staticon.get_blinking()
	
		if stat = 'True':
			blinkity.staticon.set_blinking(False)
		else:
			blinkity.staticon.set_blinking(True)
	
	# Show_Hide callback
	def  show_hide(self, widget,response_id, data= None):
		if response_id == gtk.RESPONSE_YES:
			widget.hide()
		else:
			widget.hide()
	
	# destroyer callback
	def  destroyer(self, widget,response_id, data= None):
		if response_id == gtk.RESPONSE_OK:
			gtk.main_quit()
		else:
			widget.hide()

	# popup callback
	def popup(self, button, widget, data=None):
		dialog = gtk.MessageDialog(
		parent         = None,
		flags          = gtk.DIALOG_DESTROY_WITH_PARENT,
		type           = gtk.MESSAGE_INFO,
		buttons        = gtk.BUTTONS_OK_CANCEL,
		message_format = "Do you want to close this Status Icon program?")
		dialog.set_title('Popup Window')
		dialog.connect('response', self.destroyer)
		dialog.show()
	
	def __init__(self):
		# create a new Status Icon
		self.staticon = gtk.StatusIcon()
		self.staticon.set_from_file("yellowled.png")
		self.staticon.set_blinking(True)
		self.staticon.connect("activate", self.activate)
		self.staticon.connect("popup_menu", self.popup)
		self.staticon.set_visible(True)
		self *= blinkity
		
		# invoking the main()
		gtk.main()

if __name__ == "__main__":
	statusicon = StatusIcc()[/PHP]

On a side note, what is this supposed to do?:

[PHP]self *= blinkity[/PHP]

Why are you multypling self?

Also, an error here, should be '==' (And maybe you meant True (boolean) instead of 'True' (String)):

[PHP]if stat = 'True':[/PHP]

I'm guessing that you're copy+pasting code into a script.

*edit: Fixed an error.

---

