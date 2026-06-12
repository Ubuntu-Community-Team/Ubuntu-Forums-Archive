---
title: "N00b with a python/glade/treeview problem :("
date: 2007-04-10
forum: Programming Talk
---

### Post by viciouslime on 2007-04-10
I can't get variables to display in the treeview properly. Code is as follows:

```
#treeview
			
		#Get the treeView from the widget Tree
		self.treeview = self.wTree.get_widget("treeview")
		#Add all of the List Columns to the treeview
		self.AddtracklistColumn("Rip?", 0)
		self.AddtracklistColumn("Name", 1)
		self.AddtracklistColumn("Length", 2)
		self.AddtracklistColumn("Yeah...", 3)
		self.AddtracklistColumn("Yeah...", 4)
		self.AddtracklistColumn("Yeah...", 5)
		self.AddtracklistColumn("Yeah...", 6)
		self.AddtracklistColumn("Yeah...", 7)
		self.AddtracklistColumn("Yeah...", 8)
		self.AddtracklistColumn("Yeah...", 9)
		self.AddtracklistColumn("Yeah...", 10)
		self.AddtracklistColumn("Yeah...", 11)
	
		#Create the listStore Model to use with the treeview
		self.tracklist = gtk.ListStore(str, str, str, str, str, str, str, str, str, str, str, str)
		#Attache the model to the treeView
		self.treeview.set_model(self.tracklist)	
```
```
	def notyetimplemented(self, widget):
		print "Not yet implemented!"
		context_id = self.statusbar.get_context_id("notyetimplemented")		
		self.statusbar.push(context_id, "Not yet implemented!")
		#gtk.CheckButton("checkbutton")		
		test768 = "\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\""
		self.tracklist.append(test768)
```


If i get rid of test768 and just use:
```
self.tracklist.append("dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan")
```

Then it displays perfectly... here it doesn't really matter, but later on in the code I need to a variable to be output to the treeview :(


Anyone see what I am doing wrong? I am a complete beginner with python btw. First started using it yesterday...

---

### Post by ssam on 2007-04-10
i am not too sure about using tree views, but in python

```
test768 = "\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\",\"dan\""
self.tracklist.append(test768)
```
is not the same as
```
self.tracklist.append("dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan", "dan")
```


if its always the same number of items you could use a list
```

test = ["dan","dan","dan"]
self.tracklist.append(test[0], test[1], test[3])

```

or maybe (if multiple appends give the same effect)
```

test = ["dan","dan","dan"]
for item in test:
    self.tracklist.append(item)

```

to convert a string into a list you can use something like
```

test = "dan,dan,dan".split(",")

```
or
```

a =  "dan,dan,dan"
test =a.split(",")

```

---

### Post by viciouslime on 2007-04-10
Thank you! That last example works perfectly!!!

---

