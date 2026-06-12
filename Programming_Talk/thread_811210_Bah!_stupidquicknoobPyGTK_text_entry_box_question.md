---
title: "Bah! stupid/quick/noob/PyGTK text entry box question"
date: 2008-05-28
forum: Programming Talk
---

### Post by Rob-e on 2008-05-28
heres the problem, i dont know how to reference a text entry box, the code I'm using is:
self.entry88.set_text('a')
and it says:
AttributeError: gui instance has no attribute 'entry88'

do i need to put what table/seperator it is in or what, all the stuff i found is just what i have



*curls up into ball in corner*

---

### Post by imdano on 2008-05-28
It'd be helpful to see more of your code.  It looks like you didn't declare entry88 as a member of gui class, so my first guess would be to remove the "self.", but its hard to say without seeing the rest of your code.

---

### Post by Rob-e on 2008-05-28
no, i didnt declare that, how would i go about that?  and i tried with and without the self.

heres the full code:

```
import pygtk
import gtk
import gtk.glade
import string
import os
import gobject

class gui:
	def __init__(self):
		self.wTree=gtk.glade.XML('sudoku.glade')
		dic = {	"on_execute": self.on_execute,
			"on_cancel": (gtk.main_quit),
			"on_clear": self.on_clear}
		self.wTree.signal_autoconnect(dic)
		self.count = 0
		self.win = self.wTree.get_widget("window1")
		self.win.show()
	
	def on_execute(self, widget):
			
			

			self.entry88.set_text('a')


	def on_clear(self, widget):
#	this does nothing yet
		        dialog = gtk.MessageDialog(self.win,
        		gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT,
        		gtk.MESSAGE_INFO, gtk.BUTTONS_CLOSE, None)
			dialog.set_markup('<big><b>'+str(self.count)+'</b></big>')
			answer = dialog.run()
			if answer:
				dialog.destroy()

app = gui()
gtk.main()

```

let me know if you want the glade file also

---

### Post by Can+~ on 2008-05-28
The problem is, that you're not referencing the said widget properly.

[FONT="Courier New"]self.entry88 = self.wTree.get_widget("entry88")[/FONT]

Guessing that you named entry88 on the glade file. Also, you can leave empty functions with [FONT="Courier New"][COLOR="DeepSkyBlue"]pass[/COLOR][/FONT].

The glade file is just a plain xml file that holds the widget properties and names, with the gtk.glade.XML() the object returned holds a list of widgets with their names, which you can request with the get_widget("name") method.

---

### Post by Rob-e on 2008-05-29
ok, i see where the window did the same thing, now am i going to have to do this for all other 87 boxes?

thanks for the help

---

