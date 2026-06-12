---
title: "glib.timeout_add not running"
date: 2011-04-18
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-04-18
Hello,

i'm trying the glib.timeout_add() function (see doc [over here]("http://developer.gnome.org/pygobject/stable/glib-functions.html#function-glib--timeout-add")). But i can't seem to get the loop started:

[PHP]import glib

class Thing():
	def sayhi(self):
		print "hello"
		
	def repeat(self):
		glib.timeout_add(3000, self.sayhi)

if __name__ == '__main__':
	thing = Thing()
	thing.repeat()[/PHP]

Any idea how i should do this?
Thanks
Benjamin

---

### Post by simeon87 on 2011-04-18
It will only work when GTK is running. The following code should work but note that it will print the text only once (after 3 seconds), not repeatedly yet:

```
import glib
import gtk

class Thing():
    def sayhi(self):
        print "hello"
        
    def repeat(self):
        glib.timeout_add(3000, self.sayhi)

if __name__ == '__main__':
    thing = Thing()
    thing.repeat()
    gtk.main()
```

---

### Post by jesuisbenjamin on 2011-04-18
That's a first step, thanks :)

---

### Post by jesuisbenjamin on 2011-04-18
OK i found the solution:

The timeout will only repeat if the callback returns True. The following code works:

[PHP]import glib
import gtk

class main():
	def sayhi(self):
		print "hello"
		return True
		
	def repeat(self):
		print "here!"
		glib.timeout_add(3000, self.sayhi)
		

if __name__ == '__main__':
	thing = main()
	thing.repeat()
	gtk.main()[/PHP]

---

