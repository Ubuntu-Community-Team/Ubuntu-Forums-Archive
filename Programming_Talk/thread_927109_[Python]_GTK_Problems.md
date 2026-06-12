---
title: "[Python] GTK Problems"
date: 2008-09-22
forum: Programming Talk
---

### Post by azan00 on 2008-09-22
EDIT: I solved it. To fix this issue rename the main window in Glade from window1 to window.


Hi, so after getting tired of the lengthy dev time of C++ I decided I wanted to try my hand at Python GUI development.

I am currently following this tutorial...
[http://www.micahcarrick.com/12-27-2007/gtk-glade-tutorial-part-2.html](http://www.micahcarrick.com/12-27-2007/gtk-glade-tutorial-part-2.html)

However when I send it off to the interpreter I get the following errors...
```

AttributeError: 'NoneType' object has no attribute 'show'

```

Unfortunately I lack the Python experience to recognize what the problem could be, my C++ experience tells me that I need to import the correct modules but it doesn't complain that the ones I have imported are missing.

Any help would be appreciated.

I am using the following code...
```

import sys
import gtk

class TutorialTextEditor:

	def on_window_destroy(self, widget, data=None):
		gtk.main_quit()
	
	def __init__(self):
	
		builder = gtk.Builder()
		builder.add_from_file("test.xml") 
		
		self.window = builder.get_object("window")
		builder.connect_signals(self)

	
if __name__ == "__main__":
	editor = TutorialTextEditor()
	editor.window.show() #this is the line causing the error.
	gtk.main()

```

---

