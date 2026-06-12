---
title: "PyGTK - Runs in terminal, but no GUI functionality"
date: 2007-09-21
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-09-21
I'm going through the PyGTK tutorial. Here's the code:

```

#!/usr/bin/env python

import pygtk
import gtk

class Base:
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.show

    def main(self):
        gtk.main()

print __name__
if __name__ == "__main__":
    base = Base()
    base.main()

```

Interestingly enough, if I run it in a terminal, it outputs "__main__". The code is supposed to produce a 200X200 window, but outside of the terminal, it does absolutely nothing.

There was a post addressing a similar issue - the suggested fix was to install python-gobject-dev. I did, but it didn't seem to have any effect.

I imagine this will turn out to be some bonehead python configuration error, but at the moment I'm frustrated and completely tapped for clues. Please help.

---

### Post by Wybiral on 2007-09-21
"show" is a function...

```

        self.window.show()

```

---

### Post by Carl Hamlin on 2007-09-21
Thank you, Wybiral. I owe you a beer.

You can collect on that when I'm finished blushing purple with embarrassment.

---

### Post by Carl Hamlin on 2007-09-21
Maybe you can also help me with this one:

```

#!/usr/bin/env python
import pygtk
import gtk

class HelloWorld:
	def hello(self, widget, data=None):
		print "Hello World"

	def delete_event(self, widget, event, data=None):
		print "delete event occurred"
		return False

	def destroy(self, widget, data=None):
		gtk.main_quit()

	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.connect("delete_event", self.delete_event)
		self.window.connect("destroy", self.destroy)
		self.window.set_border_width(10)
		self.button = gtk.Button("Hello World")
		self.button.connect("clicked", self.hello, None)
		self.button.connect_object("clicked", gtk.Widget.destroy, self.window)
		self.window.add(self.button)
		self.button.show()
		self.window.show()

	def main(self):
		gtk.main()

	if __name__ == "__main__":
		hello = HelloWorld()
		hello.main()

```

I set it as executable and run it from either the shell or X and get *absolutely nothing*. I wrote out the code myself, and then when that didn't work, I copied and pasted right out of the friggin' tutorial. No difference. The first program still works, but this one does *nothing*.

---

### Post by samjh on 2007-09-21
```
	if __name__ == "__main__":
		hello = HelloWorld()
		hello.main()
```Is wrongly indented.  You need to de-indent it like this:
```
if __name__ == "__main__":
	hello = HelloWorld()
	hello.main()
```

---

### Post by nhydra on 2007-09-21
PYGTK is very good wrapper to GTK+. I dare to say that is more suitable for RAD (Rapid Application Development) than C# .NET.
So, if you want to write very complicated and good applications without to stay all day to debug the code  - use PyGTK.

Here you are some useful links:
[Reference Manual]("http://pygtk.org/reference.html")
[PyGTK Tutorial]("http://pygtk.org/pygtk2tutorial/index.html")
[PyGTK FAQ]("http://faq.pygtk.org/index.py?req=index")

---

### Post by Carl Hamlin on 2007-09-21
Well, shut my mouth.

I fixed the indentation and the cursed thing worked.

samjh: Thank you for helping me. I was tearing my hair out trying to figure out where the syntax error was.

nhydra: Also thanks for sending me reference links, although I'm working through the exact tutorial you sent me. I appreciate the info.

---

### Post by samjh on 2007-09-21
> **Carl Hamlin said:**
> Well, shut my mouth.

I fixed the indentation and the cursed thing worked.

samjh: Thank you for helping me. I was tearing my hair out trying to figure out where the syntax error was.

You've got to be extra-careful about indentation in Python.  White-spaces are significant, unlike most other languages.  It can take a while to get used to it. ;)

---

### Post by Wybiral on 2007-09-22
> **samjh said:**
> You've got to be extra-careful about indentation in Python.  White-spaces are significant, unlike most other languages.  It can take a while to get used to it. ;)

I've recently realized that it's scary to jump into a Python project for this reason. I've seen a few recently that have horrified me. I know it's just bad codes, not the language, but it's a dangerous feature because it's so hard to see.

---

### Post by samjh on 2007-09-22
The significant whitespace is a very subjective thing.  I don't hate it, but I don't particularly favour it either.  I'd prefer block and statement delimiters, if there was a choice.

---

