---
title: "pygtk error?"
date: 2008-04-27
forum: Programming Talk
---

### Post by chris200x9 on 2008-04-27
hi, I'm trying to make my first GUI apps, I installed pygtk but when I follow a tutorial and try to execute this:

```


# Load GTK
import gtk

# Load our own source code from gtktest.py
# There you can find the main class gtktest()
from gtktest import gtktest

# Load sugar libraries
from sugar.activity import activity  

class gtktestActivity(activity.Activity):
	def __init__(self, handle):
		activity.Activity.__init__(self, handle)
		self._name = handle

		# Set title for our Activity
		self.set_title('gtk test')

		# Attach sugar toolbox (Share, ...)
		toolbox = activity.ActivityToolbox(self)
		self.set_toolbox(toolbox)
		toolbox.show()

		# Create the main container
		self._main_view = gtk.VBox()

		# Import our class gtktest():

		# Step 1: Load class, which creates gtktest.widget
		self.gtktest = gtktest()

		# Step 2: Remove the widget's parent
		if self.gtktest.widget.parent:
			self.gtktest.widget.parent.remove(self.gtktest.widget)
 
		# Step 3: We attach that widget to our window
		self._main_view.pack_start(self.gtktest.widget)

		# Display everything
		self.gtktest.widget.show()
		self._main_view.show()
		self.set_canvas(self._main_view)
		self.show_all()

```



I get this error:

```
 chris200x9@chris200x9-desktop:~$ ~/untitled.py
/home/chris200x9/untitled.py: line 2: import: command not found
from: can't read /var/mail/gtktest
from: can't read /var/mail/sugar.activity
/home/chris200x9/untitled.py: line 11: syntax error near unexpected token `('
/home/chris200x9/untitled.py: line 11: `class gtktestActivity(activity.Activity):'

```

what am I doing wrong?

---

### Post by Can+~ on 2008-04-27
Sugar libraries? You don't need those (Whatever they are)

Follow the pygtk tutorial:
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by twisted_steel on 2008-04-27
> **chris200x9 said:**
> what am I doing wrong?

The shell is trying to execute the first non-comment line of your program, which in your case is "import gtk".  You should add in a line before everything "#!/usr/bin/python" which will let your shell know what to run to interpret all your code in the rest of the file.  The beginning would then look like:
```

#!/usr/bin/python

# Load GTK
import gtk
```If you have not already done so, be sure to make your script executable.

---

### Post by WW on 2008-04-27
You could also run your program with the **python** command. E.g.
```

$ python myapp.py

```
Then you don't need the first line to be **#!/usr/bin/python** (but you might as well put the line in; then either method of running your program will work).

---

### Post by jespdj on 2008-04-28
The #! line is called the [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29"), and you should include it as the first line in your program to let the shell know how to run it.

---

