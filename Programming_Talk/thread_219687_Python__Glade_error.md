---
title: "Python / Glade error"
date: 2006-07-20
forum: Programming Talk
---

### Post by jethro10 on 2006-07-20
Hi,
I am really new to glade/python so bear with me.
It was working with a small demo program I downloaded and something i've done must have broke it.
Is this bit of code at the top of my file legitimate ?

[CODE]
import sys
try:
	import pygtk
	pygtk.require("2.0")
except:
        sys.exit(1)
try:
        import gtk
except:
        sys.exit(2)
try:
	import gtk.glade
except:
	sys.exit(3)
[END CODE]

It's chopped around from the original but i've discovered if I do the above I get a system exit (2) error

Is this telling me gtk is not loading right?

If so it's a step in the right direction.

Jeff

[EDIT]
THe code is correctly indented, just does not display here
[END EDIT]

---

### Post by Daverz on 2006-07-20
Use [/code] to end a code segment and try again.

---

### Post by ifokkema on 2006-07-21
I took your code from the HTML page source:
```

import sys
try:
	import pygtk

	pygtk.require("2.0")
except:
        sys.exit(1)
try:
        import gtk
except:
        sys.exit(2)

try:
	import gtk.glade
except:
	sys.exit(3)

```
And it looks like 'import gtk' throws an exception.

---

### Post by jethro10 on 2006-07-21
Thanks, at least I know i'm looking for a GTK loading error.

And secondly thats what I thought it was so i'm happy i'm learning!

J

---

### Post by Daverz on 2006-07-21
I wouldn't wrap those lines with try/excepts like that.  An exectpion will cause an exit at those points anyway, and wrapping them in a try like that just eats the traceback.

Make sure you have the python-gtk2 package, and that you can import gtk from the interactive prompt.

---

