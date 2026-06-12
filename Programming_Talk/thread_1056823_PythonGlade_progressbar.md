---
title: "Python/Glade progressbar"
date: 2009-02-01
forum: Programming Talk
---

### Post by Sandsound on 2009-02-01
I have just started fiddling with Python/Glade and have made my first program, but I cant get the progressbar to work.
I have Googled for "python glade progressbar" but havent found anything ( well at least not anything that made sense to me :-) )

I have ten steps, and for each step the progressbar should move 1/10. I have tried to simplify it and use a 25mb wav file to test it with :

> self.wTree.get_widget("progressbar1").set_fraction(0.1)
os.system('cp test1.wav test2.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.2)
os.system('cp test2.wav test3.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.3)
os.system('cp test3.wav test4.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.4)
os.system('cp test4.wav test5.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.5)
os.system('cp test5.wav test6.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.6)
os.system('cp test6.wav test7.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.7)
os.system('cp test7.wav test8.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.8)
os.system('cp test8.wav test9.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.9)
os.system('cp test9.wav test99.wav')
self.wTree.get_widget("progressbar1").set_fraction(1.0)

The files are copied correctly, but the bar does nothing until all files are copied, then it jumps to full (1.0).

What am I doing wrong ?

---

### Post by Sandsound on 2009-02-01
> **Sandsound said:**
> What am I doing wrong ?

Found the solution :-)
I have to update gtk like this :

> os.system('cp test1.wav test2.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.1)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test2.wav test3.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.2)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test3.wav test4.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.3)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test4.wav test5.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.4)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test5.wav test6.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.5)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test6.wav test7.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.6)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test7.wav test8.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.7)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test8.wav test9.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.8)
while gtk.events_pending():
	gtk.main_iteration()
os.system('cp test9.wav test99.wav')
self.wTree.get_widget("progressbar1").set_fraction(0.9)
while gtk.events_pending():
	gtk.main_iteration()
self.wTree.get_widget("progressbar1").set_fraction(1.0)

---

