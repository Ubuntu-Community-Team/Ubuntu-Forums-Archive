---
title: "Using Glade with Python-Changing Widgets"
date: 2007-04-26
forum: Programming Talk
---

### Post by LaurelLynn on 2007-04-26
Hi Boys,

I'm old to programming but new to Python.  Since there are no fixed types or recasting, I can't figure out how my program can change widget properties in callbacks.  For example, this is some of my basic Hello World Code:
[INDENT]
class HellowWorldGTK:

	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "TopMa/topma.glade"
	        self.wTree = gtk.glade.XML(self.gladefile) 
		
		#Create our dictionay and connect it
		dic = { "on_hiButton_clicked" : self.hi_clicked,
			"on_MainWin_destroy" : gtk.main_quit }
		self.wTree.signal_autoconnect(dic)

#callback for hi button
	def hi_clicked(self, widget):
		print "Top of the World Ma!!!"
[/INDENT]

The callback "hi_clicked" just prints the text to the command line, but what I want, is to change the button's label in the callback.

A GUI isn't very useful if I can't pass settings back **and** forth.

Can someone help a damsel in distress?

---

### Post by pmasiar on 2007-04-26
Ok, surely some expert will help you.

BTW next time, use CODE tags instead of INDENT. It will keep whitespace.

> **LaurelLynn said:**
> 

```

#callback for hi button
	def hi_clicked(self, widget):
		print "Top of the World Ma!!!"

```

The callback "hi_clicked" just prints the text to the command line, but what I want, is to change the button's label in the callback.


print just prints. I am no expert on Glade, but I would expect that you need to use some widget properties to change label.

self.something = "Top of the World Ma!!!" instead of print  "Top of the World Ma!!!"

---

### Post by LaurelLynn on 2007-04-26
Thanks  pmasiar,

I got it, actually it was:

```
widget.set_label( "Top of the World Ma!!!" )
```

I had tried that with self, and I guess I forget to try it with widget the first time around.

---

