---
title: "Someone to teach me PyGTK."
date: 2006-07-06
forum: Programming Talk
---

### Post by noob_Lance on 2006-07-06
Hey,

Im having a very hard time grasping the concept of programming python and binding it to GTK. if someone would be kind enough to spend a little time helping me understand it better.. it would be Greatly appreciated. Over MSN would be ideal. and since you would be helping me do the programming.. i would suspect that you would have knowladge of glade aswell. if someone is willing... my msn is
silver_suicide_rider [at] hotmail.com

Thanks, and regards
~Lance

---

### Post by Daverz on 2006-07-06
You might want to try #pygtk on irc.gimp.org

---

### Post by Wallakoala on 2006-07-06
I don't know much pygtk, but the best thing to do I would say is learn python fairly well, and make sure you understand it. Then go onto pygtk.

It will make things much easier.

---

### Post by noob_Lance on 2006-07-06
im good with python... its the GTK that im having the issue with

---

### Post by Wallakoala on 2006-07-06
> **noob_Lance said:**
> im good with python... its the GTK that im having the issue with

This is a very good website for learning some pygtk: [http://www.learningpython.com/](http://www.learningpython.com/)

If you look on the right on that page there are categories such as glade, pygtk, etc.

Those tutorials helped me learn a bit as they are well written and straightforward.

---

### Post by noob_Lance on 2006-07-07
oh god... thats the site i tried to learn from.. and no help i now have a basic widget created... but even the button dosnt do anything.. how can i make an about box pop up i have the following code

```

#!/usr/bin/env python

import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
	sys.exit(1)

class Davinci:

	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "davinci.glade"  
		self.wTree = gtk.glade.XML(self.gladefile, "window1") 

		#Create our dictionay and connect it
		dic = {"on_mainWindow_destroy" : gtk.main_quit
				, "on_btnAdd_clicked" : self.About}
		self.wTree.signal_autoconnect(dic)
		
	def About(self, widget):
		"""Called when the use wants to add a wine"""
		self.dlg = self.wTree.get_widget("dlgAbout")

if __name__ == "__main__":
	main = Davinci()
	gtk.main()


LOL nvm... i got that part to work.. now time to expandto text fields.. any advice?
```

---

### Post by kanem on 2006-07-07
I just started with python a few weeks ago and the tutorials I found were great. I previously knew nothing about coding in python or GTK; now I've written an mp3/ogg player.

Here are the links I found the most useful:

For python itself I went through the first few chapters of [this tutorial](http://docs.python.org/tut/). Its just python, no GTK, but I found it extremely useful later when doing the actual coding. Both becasuse of what I learned from it, and as a reference.

Two good and simple tutorials/examples of pygtk/Glade are from the same person:
[hello world](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
[wine store](http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/)

Going through these gave me enough to start building widgets and functionality that aren't in those examples. At this point a [reference for all of pygtk](http://www.pygtk.org/pygtk2reference/) is essential. When their definitions are too cryptic, this [pygtk](http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html)  tutorial is very helpful as it seems to cover and have examples of just about everything in the reference.

One thing to be careful of when browsing other's examples: if they didn't use Glade it will look much more complicated. Once you have grokked what Glade does you'll be able to look at some code that didn't use Glade and mentally filter out all the redundant stuff that you won't need.

---

### Post by kanem on 2006-07-07
> **noob_Lance said:**
> oh god... thats the site i tried to learn from.. and no help i now have a basic widget created... but even the button dosnt do anything.. how can i make an about box pop up i have the following code

```

	def About(self, widget):
		"""Called when the use wants to add a wine"""
		self.dlg = self.wTree.get_widget("dlgAbout")

if __name__ == "__main__":
	main = Davinci()
	gtk.main()
```


LOL nvm... i got that part to work.. now time to expandto text fields.. any advice?
Oops, I see you've already seen that tutorial I mentioned. Well, no 'About' dialog pops up here because it hasn't been told to. All that 'self.dlg=self.wTree.get_widget("dlgAbout")' does is associate self.dlg with the 'dlgAbout' widget, so instead of giving a command like gtk.about_dialog.show_up('dlgAbout'...) you can just use self.dlg.show_up(). To get the About dialog to actually do stuff you have to code the rest of the tutorial.

---

### Post by noob_Lance on 2006-07-08
how can i add items to a menu? a quick commented way would be nice so i know what im doing. if anyone can help... it would be appreciated

~Lance

---

