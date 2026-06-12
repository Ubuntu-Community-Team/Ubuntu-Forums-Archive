---
title: "Python &amp; SuperKaramba"
date: 2007-01-03
forum: Programming Talk
---

### Post by Mithrilhall on 2007-01-03
I'm having some issues with my superkaramba theme I'm making. When I initially loaded it it worked perfectly. I then went to work and came home and now it just shows the X's again even though I have 2 files in the directory.

Any clue what's wrong here?


Here is my .theme file:
```

karamba x=30 y=30 w=500 h=200 interval=2000
text x=0 y=10 color=255,255,255 font="Neuropol" fontsize=20 shadow=0 value="Queue"

```

Here is my python (.py) file:
```

#this import statement allows access to the karamba functions
import karamba
import os
import sys

#this is called when you widget is initialized
def initWidget(widget):
	global statusText
	global txt
	global directory
	statusText = karamba.createText(widget, 15, 40, 0, 0, "XXXXXXXXXXXXXXXX")
	karamba.redrawWidget(widget)
	pass

#this is called everytime your widget is updated
#the update inverval is specified in the .theme file
def widgetUpdated(widget):
	global statusText
	global txt
	global directory
	directory = "/home/downloads/"
	if os.path.exists(directory):
		files = os.listdir(directory)
		for file in files:
			txt = txt + "\n" + file
	else:
		txt = "Directory not found....are you sure of its location?"
		
	karamba.changeText(widget, statusText, txt)
	karamba.redrawWidget(widget)
	txt = ""
	pass


```

---

