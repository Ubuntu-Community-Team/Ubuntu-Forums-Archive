---
title: "python/gtk &quot;event&quot; from a keypress..."
date: 2007-02-19
forum: Programming Talk
---

### Post by Choad on 2007-02-19
```

def txtKeyPress(self, widget, event):
		if (the key that was pressed was "enter"):
			updateAndClose()

```

pretty self explanitory. the rather obviously not-real-code bit.... i need to know how to implement this

thanks

cant find a reference for this :(

---

### Post by gradedcheese on 2007-02-19
I believe that you're looking for an EventBox:

[http://www.pygtk.org/pygtk2tutorial/ch-ContainerWidgets.html#sec-EventBox](http://www.pygtk.org/pygtk2tutorial/ch-ContainerWidgets.html#sec-EventBox)

and then, if you read the GTK+ API EventBox section, you can find out how to set up an EventBox to catch particular key presses.  I'm not 100% sure, but I think that's what I did in the past. 

From their example:

```

 	        # And bind an action to it
  	        event_box.set_events(gtk.gdk.BUTTON_PRESS_MASK)
   	        event_box.connect("button_press_event", lambda w,e: gtk.main_quit())

```

this binds the mouse... you can do similar stuff with the keyboard (I think :)).

---

### Post by Engnome on 2007-02-19
snip

---

### Post by gradedcheese on 2007-02-19
Engnome -- he was just posting some psuedocode to explain what he's looking for, I don't see any problem with that?  I'm pretty sure he understands python syntax.

---

### Post by Engnome on 2007-02-19
> if (the key that was pressed was "enter"):

Is the wrong place to start. Before you start hacking on that function you must connect the event.

EDITED: Didn't realize you were looking for *key* event first...

EDIT AGAIN: wth?! tried editing after I but it made a new post instead...

---

### Post by Choad on 2007-02-19
are you sure i need another widget? that doesnt sound very useful... i mean the widget has a key press event... i just need to know what part of the "event" class to evaluate and what to compare it with

```

class UpdateWindow:
	def __init__(self, parent, currentName):
	        self.wTree = gtk.glade.XML("MultiWindowApp.glade", "winUpdate")
	        
		dic = {	"on_winUpdate_destroy" 		: self.destroyMe,
			"on_winUpdate_delete_event"	: self.destroyMe,
			"on_btnApply_clicked"		: self.btnApplyClicked,
			"on_txtName_key_press_event"	: self.txtKeyPress
			}
	
		self.wTree.signal_autoconnect(dic)
		
		self.parent = parent
		self.window = self.wTree.get_widget("winUpdate")
		self.window.set_transient_for(self.parent.window)
		self.parent.window.set_sensitive(False)
		self.txtName = self.wTree.get_widget("txtName")
		self.txtName.set_text(currentName)
	
	def btnApplyClicked(self, widget):
		updateAndClose()
		
	def txtKeyPress(self, widget, event):
[COLOR="Red"]		#here be dragons:[/COLOR]
			updateAndClose()
		
	def destroyMe(self, widget, event):
		self.parent.window.set_sensitive(True)
		self.window.destroy()	
	
	def updateAndClose(self):
		self.parent.updateName(self.txtName.get_text())
		self.parent.window.set_sensitive(True)
		self.window.destroy() 

```

---

### Post by Choad on 2007-02-20
buuuuuuuuuuuuuuump

---

### Post by po0f on 2007-02-20
Choad,

I am just learning PyGTK myself and am by no means an expert, so dismiss if you want to.

What kind of widget is this keypress supposed to happen in?  You are using Glade so I can't see (I prefer "raw" pygtk code myself).  Figure that out, then look into the signals that widget can emit.  If it's a TextView/TextBuffer/TextWhatever, it should have some sort of signal attached to the Enter key, one would think.

---

### Post by Choad on 2007-02-20
its a gtkEntry and it doesnt have a specific "enter event" unless "enter_notify_event" is the event im looking for.

i am using it's key_press_event

---

### Post by po0f on 2007-02-20
Choad,

So basically, if text is changed inside the Entry widget, you want it to be saved?  Please clarify exactly the behavior you expect to have.

---

### Post by Choad on 2007-02-20
no, not changed... that would be wierd

basically the window concists of a single text entry and an "ok" button. as it stands, you type something in to the text entry, and then click on the ok button, which calls the updateAndClose() function you can see up there.

i want the same thing to happen if you hit enter after typing tho. i cant use the "changed" event, as that would mean you could type something, then click on another part of the window, the changed event would trigger and the window would disappear. not what i want. i only want it to happen when the ok button is clicked, or when you hit enter after you've been typing in the text box

---

### Post by j_g on 2007-02-20
You've obviously used Glade to make your UI. Run Glade again and load up your XML file.

Find and select your text box (ie, GtkEntry class) widget in the list of widgets. The "Properties" window should show its settings. On the "General" page, you should see a setting labeled "Activates default". Make sure it is set to "Yes".

Now, find and select your Ok button widget. The "Properties" window should switch to showing that button's settings. Go to the "Common" page. Look for a setting labeled "Can default". Set it to "Yes". Beneath this is another setting labeled "Has default". Set this to "Yes" also.

You've now set your OK button to be the "default widget". You've also set your text box to activate this default widget. That means, when the user presses enter while operating your text box, it will activate your OK button. And that means that your OK button's "clicked" event will happen. Obviously, you've attached your own python function to be called when that button receives its clicked event? If so, you should be good to go.

---

### Post by Choad on 2007-02-20
AHA!

thankyou for this!

works fine, thanks

---

