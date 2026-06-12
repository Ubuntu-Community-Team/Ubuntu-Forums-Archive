---
title: "[SOLVED] Can I delete python's cache?"
date: 2008-03-11
forum: Programming Talk
---

### Post by Jadd on 2008-03-11
I've created a layout in Glade 3 and saved it as filename.glade
My code is:
```
#!/usr/bin/env python
 
import sys
import gtk
import gtk.glade
 
class TutorialApp:
 
  def __init__(self):
  
    self.wTree = gtk.glade.XML("filename.glade")
 
    dic = { "on_window_destroy" : gtk.main_quit }
    self.wTree.signal_autoconnect(dic)
    self.wTree.get_widget("window").show()
 
if __name__ == "__main__":
  app = TutorialApp()
  gtk.main()
```

I get this error:```
Traceback (most recent call last):
 File "/home/user/Documents/Programming/tutorial.py", line 18, in 
app = TutorialApp()
 File "/home/user/Documents/Programming/tutorial.py", line 15, in __init__
self.wTree.get_widget("window").show()
AttributeError: 'NoneType' object has no attribute 'show'
```

I know what the problem is: previously I had called my window win_, saved it and ran a similar python script, with win_ instead of window. It worked. But gtk.glade.XML cached the glade file, and the change I made to the window's name isn't acknowledged.

So my question is, how can I clear python's cache?

(I've just started to learn python and glade.)

---

### Post by Can+~ on 2008-03-11
> **Jadd said:**
> I know what the problem is: previously I had called my window win_, saved it and ran a similar python script, with win_ instead of window. It worked. But gtk.glade.XML cached the glade file, and the change I made to the window's name isn't acknowledged.

So my question is, how can I clear python's cache?

(I've just started to learn python and glade.)

I'm pretty sure that gtk.glade.xml does not cache anything. My guess is that you didn't save correctly on glade, as glade is kinda weird for it's things, like you have to type the name, hit enter to change it, and then save. Trust me with this one, as I've experienced similar problems like. "I renamed my button, hit Ctrl+S, shift desktop, try to get the widget, and fails, then I go back to glade and see that the name didn't change at all"

And your application does not exist correctly, I just tried it and didn't work, connect it manually, and also, I recommend to move the gtk_main loop inside the class, but that's just me.

---

### Post by Jadd on 2008-03-11
> **Can+~ said:**
> I'm pretty sure that gtk.glade.xml does not cache anything. My guess is that you didn't save correctly on glade, as glade is kinda weird for it's things, like you have to type the name, hit enter to change it, and then save. Trust me with this one, as I've experienced similar problems like. "I renamed my button, hit Ctrl+S, shift desktop, try to get the widget, and fails, then I go back to glade and see that the name didn't change at all"

And your application does not exist correctly, I just tried it and didn't work, connect it manually, and also, I recommend to move the gtk_main loop inside the class, but that's just me.
Thank you.
However, I should have mentionned this earlier, gtk.glade.XML is documented, and it's documentation says it does cache the parse tree:
[http://www.pygtk.org/pygtk2reference/class-gladexml.html](http://www.pygtk.org/pygtk2reference/class-gladexml.html)
(Find "cached")
Also, I have verified that I had saved correctly, I even opened the XML .glade file in a text editor to do so.

---

### Post by Quikee on 2008-03-11
> **Jadd said:**
> Thank you.
However, I should have mentionned this earlier, gtk.glade.XML is documented, and it's documentation says it does cache the parse tree:
[http://www.pygtk.org/pygtk2reference/class-gladexml.html](http://www.pygtk.org/pygtk2reference/class-gladexml.html)
(Find "cached")
Also, I have verified that I had saved correctly, I even opened the XML .glade file in a text editor to do so.

Of course it caches the tree... for the life time of the application. It doesn't make sense to cache it longer than that.

---

### Post by Jadd on 2008-03-11
Perhaps my IDE has got something to do with it. I'm using SPE.

---

### Post by Can+~ on 2008-03-11
> **Jadd said:**
> Thank you.
However, I should have mentionned this earlier, gtk.glade.XML is documented, and it's documentation says it does cache the parse tree:
[http://www.pygtk.org/pygtk2reference/class-gladexml.html](http://www.pygtk.org/pygtk2reference/class-gladexml.html)
(Find "cached")
Also, I have verified that I had saved correctly, I even opened the XML .glade file in a text editor to do so.

I don't think that cache means a long term cache.

Could you post the glade file (it's plain XML).

Also, try to run from the commandline python myfile.py

I made an example based on your file, this one exits properly, and has the gtk.main inside the class:

[PHP]#!/usr/bin/env python
 
#import sys
import gtk
import gtk.glade
 
class TutorialApp:
	def destroy_event(self, widget, data=None):
		gtk.main_quit()
		return False
	
	def __init__(self):
		self.wTree	= gtk.glade.XML("filename.glade")
		self.win	= self.wTree.get_widget("window1")
		
		
		#__signals__ = { "on_window_destroy" : gtk.main_quit }
		#self.wTree.signal_autoconnect(__signals__)
		
		self.win.connect("destroy", self.destroy_event, None)
		
		self.win.show_all()
		
 	def gtk_main(self):
 		gtk.main()
 		
if __name__ == "__main__":
	app = TutorialApp()
	app.gtk_main()

[/PHP]

---

### Post by Jadd on 2008-03-11
I quit SPE and glade and used just gedit, but it still gives me the same problems.

Here's the code:[PHP]#!/usr/bin/env python
 
import sys
import gtk
import gtk.glade
 
class TutorialApp:
 
  def __init__(self):
  
    self.wTree = gtk.glade.XML("desktop_designer.glade")
 
    dic = { "on_window_destroy" : gtk.main_quit }
    self.wTree.signal_autoconnect(dic)
    self.wTree.get_widget("window").show()
 
if __name__ == "__main__":
  app = TutorialApp()
  gtk.main()
[/PHP]

---

### Post by Jadd on 2008-03-11
And here's the glade file. I had to archive because these forums don't accept .glade.

I doubt you'll get the same problems as me though, you haven't got the version with win_ in your cache.

---

### Post by Jadd on 2008-03-11
I tried your suggested code. I had to convert the spaces into tabs which was annoying. Using window and window1 gave the same kind of error, but using win_ worked perfectly! (By the way, the .glade file I'm using is called desktop_designer.glade, and I did modify that code to reflect that, sorry for triple posting)

---

### Post by Can+~ on 2008-03-11
It works for me, even if I rename it various times.

But I came up with a new theory, maybe, just maybe, you opened the wrong file, maybe you're editing a copy instead of the actual file, that would create the false impression of a "omg it's cached". Close glade and make sure you're opening the right file, and the right .py file. How did I get to this conclusion? It just happend to me, I was working on a copy on my desktop rather than the one next to the python script.

Btw, you have two "WINDOW_TOPLEVEL", make one POPUP.

*edit* And yes, I use tabs, sorry about that.

---

### Post by Jadd on 2008-03-11
You know, I may just try rebooting. SPE did crash once this session, maybe that's affecting things.
Re:BTW: I'm not using showing the first window, I copied it off a blueprint and am using it to teach myself glade.

---

### Post by Jadd on 2008-03-11
I've rebooted and I still have the same problem! What's worse is that renaming desktop_designer.glade to desktop_designer2.glade gave me the same results. Now I think there must be something wrong with the glade file.

---

### Post by Jadd on 2008-03-11
I am embarrassed to admit I've found the problem. I had saved the glade file as a different file, and kept linking to the old file. So of course any changes I make wouldn't be detected!
Sorry to bother you with this, I really should have spotted the mistake myself. I have had enough experience in other programming languages to know better.
Thanks Can+~ and Quickee for your help. This problem is SOLVED.
(Especially Can+~. You spotted the problem with few clues. I feel like the guy who forgot to plug in his computer.)

---

