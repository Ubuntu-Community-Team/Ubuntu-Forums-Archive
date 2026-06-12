---
title: "Quick Python Glade/GTKbuilder question."
date: 2010-06-28
forum: Programming Talk
---

### Post by Karakh on 2010-06-28
What is the easiest way to have an entry continually update without any user actions?

Simplest example I could think of is below. It prints the time when the button is pressed, but how would I have it continually update without any user input?

```
class timerGUI():
	def __init__(self):
		
		self.builder = gtk.Builder()
		self.builder.add_from_file('timer.glade')
		
		self.start = time.time()
		
		dic = {
		'on_window1_destroy' : self.quit,
		'on_button1_pressed' : self.update,
		}
		
		self.builder.connect_signals(dic)
		
	def quit(self, widget):
		sys.exit(0)
	
	def update(self,widget):
		
		t = str(time.time()-self.start)
		self.builder.get_object('entry1').set_text(t)

			
timer = timerGUI()
gtk.main()

```

---

### Post by StephenF on 2010-06-28
[gobject.timeout_add(interval, callback)]("http://www.pygtk.org/pygtk2reference/gobject-functions.html#function-gobject--timeout-add")

---

### Post by Karakh on 2010-06-28
Thanks for info, after some more googling, found [this]("http://ubuntuforums.org/showthread.php?t=1301661") which works fine for me.

---

