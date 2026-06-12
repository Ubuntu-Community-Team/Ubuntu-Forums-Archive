---
title: "pygtk broke totem. :("
date: 2009-08-26
forum: Programming Talk
---

### Post by AncientPC on 2009-08-26
I wouldn't normally post this here, but I tried out the quick pygtk example from the [wikipedia]("http://en.wikipedia.org/wiki/Pygtk#Syntax") page.

```
import gtk
 
def createWindow():
	window = gtk.Window()
	window.set_default_size(200, 200)
	window.connect('destroy', gtk.main_quit)
 
	label = gtk.Label('Hello World')
	window.add(label)
 
	label.show()
	window.show()
 
createWindow()
gtk.main()

```

However now when I open a video with totem, it opens up the Hello World dialog box as well and refuses to play the media.  If I close either totem or the Hello World box, both windows close.  Any ideas how to destroy the window?  Rebooting doesn't seem to help.

---

### Post by Tony Flury on 2009-08-26
what did you call the python file when you created it. It maybe that Totem is executing your file instead of something of its own.

---

### Post by AncientPC on 2009-08-26
~/pygtk.py

---

### Post by Tony Flury on 2009-08-26
there is the problem - pygtk.py is the name of the pygtk module file which many python gtk based applications will import - and my guess is that Totem is importing the pygtk module - and importing your file instead. 

rename your file - and you will probably find that totem works fine :-)

---

### Post by AncientPC on 2009-08-26
That worked! *ugh*, but what an obscure issue.  I'm kinda surprised that my home directory is in the python library path, and on top of that higher priority than the /usr/lib/ (or wherever they're stored).

Anyway, thanks!

---

### Post by Tony Flury on 2009-08-26
i think the modules are searched in the local directory first and then via the PYTHONPATH environment variable, and it does make sense to search local stuff first, it makes it easy for a developer to make a local copy of a system module - and fix bugs etc - without needing to change the PATH.

I would not say it is obscure - it is the 2nd or 3rd time it (or something similar) has come up in this forum in the past few weeks.

---

### Post by AncientPC on 2009-08-26
Yeah that does make sense, I guess it's just obscure to me. :P

Seriously though, thanks for helping out and explaining everything!

---

