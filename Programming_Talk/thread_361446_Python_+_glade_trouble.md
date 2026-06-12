---
title: "Python + glade trouble"
date: 2007-02-14
forum: Programming Talk
---

### Post by Engnome on 2007-02-14
As an excercise (learning python) I'm making a small memory game in python. Using glade files with libglade.
But I get this error:
```
memorygladetest.py:51: GtkWarning: gtk_table_attach: assertion `child->parent == NULL' failed self.board_table.attach(self.cards[x], i, i+1, j, j+1)
```

So I tried simplifying to:
```
self.board_table.attach(self.cards[0], 0, 1, 0, 1)
```

Doesn't work either. All I get is one image and then an error.

[php]
#!/usr/bin/python
import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
import random

def start(self, widget,  a=None):
	global nr_of_rows
	global nr_of_cols
	
	if memory_gui.radiobutton1.get_active():
		difficulty = "easy"
		nr_of_rows = 2
		nr_of_cols = 4
		
	if memory_gui.radiobutton2.get_active():
		difficulty = "medium"
		nr_of_rows = 4
		nr_of_cols = 4
		
	if memory_gui.radiobutton3.get_active():
		difficulty = "hard"
		nr_of_rows = 8
		nr_of_cols = 4
	
	
	#set up the board
	memory_gui.board_table.resize(nr_of_rows, nr_of_cols)
	memory_gui.attachImages()
	

def guess(self, widget,  a=None):
	pass



class memoryGui:
	
	def delete_event(self, widget, event, data = None):
		return False
	
	def destroy(self, widget, data = None):
		gtk.main_quit()
	
	def attachImages(self):
		x = 0
		for j in range(0, nr_of_rows):
			for i in range(0, nr_of_cols):
				self.board_table.attach(self.cards[x], i, i+1, j, j+1)
				self.cards[x].show()
				x += 1
		
		#manually like this doesn't work either:
		#self.board_table.attach(self.cards[0], 0, 1, 0, 1)
		#self.board_table.attach(self.cards[1], 1, 2, 0, 1)
		#self.cards[0].show()
		#self.cards[1].show()
		
		
	def __init__(self):
		xml = gtk.glade.XML("memory.glade")
		
		#window
		self.top_window = xml.get_widget("top_window")
		self.top_window.connect("destroy", self.destroy)
		
		#board tabel
		self.board_table = xml.get_widget("table1")
		
		self.cards = [gtk.Image()] * 16
		for i in range(0, 16):
			self.cards[i].set_from_file("cards/back.jpeg")
		
		self.attachImages()
		
		#control panel buttons and label
		self.start_button = xml.get_widget("start_button")
		self.start_button.connect("clicked", start, None)
		
		self.guesses_label = xml.get_widget("guesses_label")
		self.guesses_label.show()
		
		self.highscore_button = xml.get_widget("highscore_button")
		#self.highscore_button.connect("clicked", showHighScore, None)
		
		#radiobuttons
		self.radiobutton1 = xml.get_widget("radiobutton1")
		self.radiobutton2 = xml.get_widget("radiobutton2")
		self.radiobutton3 = xml.get_widget("radiobutton3")
		
		self.radiobutton2.set_active(True)
		
	
	def main(self):
		gtk.main()

if __name__ == "__main__":
	nr_of_rows = 4
	nr_of_cols = 4
	
	memory_gui = memoryGui()
	memory_gui.main()
[/php]

If you are wondering over the weird way of getting images inte the table it's because I want to be able to resize the table.

---

### Post by duff on 2007-02-14
just guessing, but "self.cards = [gtk.Image()] * 16 " is a list of 16 references to the same object.

```
>>> x=[{}] * 3
>>> x[0]['foo'] = 'bar'
>>> x
[{'foo': 'bar'}, {'foo': 'bar'}, {'foo': 'bar'}]

```

try using "append" inside the loop.

---

### Post by Engnome on 2007-02-14
> **duff said:**
> just guessing, but "self.cards = [gtk.Image()] * 16 " is a list of 16 references to the same object.

```
>>> x=[{}] * 3
>>> x[0]['foo'] = 'bar'
>>> x
[{'foo': 'bar'}, {'foo': 'bar'}, {'foo': 'bar'}]

```

try using "append" inside the loop.

Thanks :) Just what I needed.

if anyone wonders this is what it looks like now:
[php]
self.cards = []
for i in range(0, 16):
	self.cards.append(gtk.Image())
	self.cards[i].set_from_file("cards/back.jpeg")
[/php]

---

