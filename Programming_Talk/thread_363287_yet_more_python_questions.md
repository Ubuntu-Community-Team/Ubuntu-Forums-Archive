---
title: "yet more python questions"
date: 2007-02-16
forum: Programming Talk
---

### Post by Choad on 2007-02-16
ignore....

---

### Post by Choad on 2007-02-16
ok, an actuall question

firstly, is it just me, or is the pyGTK reference manual the deliberately set out so that you can never find what you're looking for?

anyhow, how can i create a gtk.HBox then set the number of columns it has on the fly?

thanks.

---

### Post by WW on 2007-02-16
I'm learning to use PyGTK myself at the moment, so I may have missed something, but my understanding is that you don't "set the number of columns" in an HBox.  You just add widgets to it with either the pack_start or pack_end method, and it will organize them in a row for you.

---

### Post by Choad on 2007-02-16
aha! i see. that makes a bit of sense

---

### Post by Choad on 2007-02-17
ok, next question. may as well raise this thread seeing as its still on page 1

at the moment, in my main window class i have

mainTable = self.wTree.get_widget("table1")

which obviously gets a table from the glade file. now what if i want to make that a global variable? would i have to (at the beggining of the file) write 

mainTable = gtk.Table()

and then it would be global... right? but doesnt that mean i have wasted a bit of memory calling gtk.Table(), and creating an instance of a table that is never used? *confused* im sure there must be a better way :)

---

### Post by Choad on 2007-02-17
ok, so here are some classes

```

class Sequencer:
	def __init__(self):
		self.tracks = {}
		for i in range (trackCount):
			newHBox = gtk.HBox()
			mainTable.attach(newHBox, 1, 2, i+1, i+2, gtk.FILL, gtk.FILL)
			self.tracks[trackNames[i]] = Track(trackNames[i], newHBox)
			
	
	
class Track:
	def __init__(self, trackName="track", trackBoxI=gtk.HBox()):
		self.name = trackName
		self.beats = tsTop * barCount
		self.buttons = ([])
		self.trackBox = trackBoxI
		for i in range(self.beats):
			newButton = gtk.ToggleButton()
			self.trackBox.pack_end(newButton)
			newButton.show()
			self.buttons.append(newButton)
		self.trackBox.show()

```

first off, if i have done anything obviously really stupid regarding the python, please point it out to me... im still not very sure about arrays in python.

anyhow, i can run this program, and i get no errors, however none of the toggle buttons show up

in the main window class, i simply create an instance of sequencer, which should in turn create 4 tracks, which each should create 16 toggle buttons 

but none of them show up.

if you need me to show you more code i can... all the global variables i referenced are correct afaik

---

### Post by WW on 2007-02-17
I recommend starting with a very simple--but working--pygtk program, such as the really basic example here: [http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html](http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html)
Actually, you should look further in the tutorial for something a bit more advanced.
Then modify it to do what you need.  That way you will have a working template on which to build. That's basically what I did to create the program here: [http://ubuntuforums.org/showthread.php?t=239082](http://ubuntuforums.org/showthread.php?t=239082)

---

### Post by Choad on 2007-02-17
i've created a handful of pyGTK apps already tho

its really getting on my nerves now lol. nothing i try seems to work!

---

### Post by Choad on 2007-02-17
aha! got it!

you have to explicitly tell python you are assigning to a global variable, otherwise it creates a new local instance

---

