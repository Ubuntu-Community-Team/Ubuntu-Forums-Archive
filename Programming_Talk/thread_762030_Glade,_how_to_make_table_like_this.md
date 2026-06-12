---
title: "Glade, how to make table like this?"
date: 2008-04-21
forum: Programming Talk
---

### Post by smartboyathome on 2008-04-21
Hello, I saw QuickStart and saw the table, and thought that was exactly what I needed for my program. I was wondering how to do it in glade. Thanks to anyone who helps.

Smartboy

EDIT: Image of what I want:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60220&d=1203527356[/IMG]

---

### Post by dje on 2008-04-21
I'm pretty sure that's done using zenity:
```
sudo apt-get install zenity
```
(I think it's installed by default but just in case)
Then have a look [here]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/") and [here]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-1/") or just do:
```
zenity --help
``` 
or specifically for the table:
```
zenity --help-list
```

hope that helps you,
dje

---

### Post by smartboyathome on 2008-04-21
Would you know how to do it using Glade, though? And I will look into Zenity, thanks.

---

### Post by dje on 2008-04-21
I could probably work it out but it would take a while, I've only just started using python, pygtk and glade (see blue link in my sig). Someone else can probably be of more help

dje

---

### Post by sq377 on 2008-04-21
I believe that is a treeview (though I haven't looked at the code).  I recently made a stopwatch where I needed to save their times in one, and I had to implement one like this.
[http://scentric.net/tutorial/treeview-tutorial.pdf](http://scentric.net/tutorial/treeview-tutorial.pdf) gives a good in depth explanation of how to do this in c.

Glade can only create the widget to store the model in, I dont believe you can put in any data or even the column headers in it.

---

### Post by Can+~ on 2008-04-21
That's a treeView, if you're using python:

Reference:
[http://www.pygtk.org/pygtk2reference/class-gtktreeview.html](http://www.pygtk.org/pygtk2reference/class-gtktreeview.html)

Tutorial:
[http://www.pygtk.org/pygtk2tutorial/sec-TreeViews.html](http://www.pygtk.org/pygtk2tutorial/sec-TreeViews.html)

---

### Post by smartboyathome on 2008-04-21
Can+~ Thanks for that. :)

EDIT: How would I use a gtk xml file with pygtk?

---

### Post by Can+~ on 2008-04-21
> **smartboyathome said:**
> Can+~ Thanks for that. :)

EDIT: How would I use a gtk xml file with pygtk?

I made a template, and put it on my ~/Templates/ folder. The usual syntax is this (using a class for tidiness):

[PHP]#!/usr/bin/env python
#Python with GTK source file.

import gtk, gtk.glade

class mainWindow:
	def event_destroy(self, widget, data=None):
		gtk.main_quit()
	
	def event_debug(self, widget, data=None):
		print "widget %s called with data %s" % (widget, data)
	
	def __init__(self):
		self.xml = gtk.glade.XML("gladefile.glade")
		self.win = self.xml.get_widget("MainWindow")

		#Signals
		signals = { 
		"destroy_event"	: self.event_destroy,
		"my_event" : 	self.event_debug }
		
		self.win.connect("destroy", self.event_destroy, None)
		self.xml.signal_autoconnect(signals)
		
		self.win.show_all()

	def main(self):
		gtk.main()

if __name__ == "__main__":
	mwin = mainWindow()
	mwin.main()
[/PHP]

(The destroy_event, and my_event are just examples. I mostly use the destroy_event when user clicks on a button to exit)

*edit*
I just discovered that the forum converts tabs into spaces on the presentation, but if you quote, you can get the tabbed version.

---

### Post by RIchard James13 on 2008-04-22
I have one of those in my personal accounting program. Actually I have three tabs in my accounting program each with a treeview. The treeview is created using Glade which I import using python. Then I need to add some more objects to the treeview in order to get the column headings and the data in the rows.

My code is a bit complicated since it pulls data out of a database. Also I sometimes call the treeviews listboxes.

[PHP]    def fillLstPayees(self):
        """ Fill the ListBox in the Payees Pane and set it's column headings """
        lstPayees = self.queryLstPayees()
        columns = ['Pk_Payee','Payee','Address','Suburb/City','Post Code']
        self.addCellRenderers(lstPayees, columns)

    def queryLstPayees(self):
        """ Create a GTK treestore containing the values in the tblPayees 
            and then insert that into the Categories Pane ListBox """
        treestore = gtk.TreeStore(str,str,str,str,str)
        for result in self.accountsDB.runQuery("SELECT * FROM tblPayees ORDER BY 2"):
            treestore.append(None, [result[0],result[1],result[2],result[3],result[4]])
        self.lstPayees.set_model(treestore)
        return self.lstPayees

    def addCellRenderers(self, treeView, columns):
        """ Add the column headings to a treeView """
        count = 0
        for column in columns:
            tvcolumn = gtk.TreeViewColumn(column)
            treeView.append_column(tvcolumn)
            cell = gtk.CellRendererText()
            tvcolumn.pack_start(cell, True)
            tvcolumn.add_attribute(cell, 'text', count)
            count += 1
[/PHP]

Basically you create a treestore object in the constructor you tell it what data you are going to insert. 
[PHP]treestore = gtk.TreeStore(str,str,str,str,str)[/PHP]
Then you insert the data with the append command
[PHP]treestore.append(None, [result[0],result[1],result[2],result[3],result[4]])[/PHP]
Then you bind the treestore to the treeview 
[PHP]self.lstPayees.set_model(treestore)[/PHP]

To add the column labels I created the generic function addCellRenderers. All this does is iterate over a list of strings. Create a TreeViewColumn for each one. Then it appends the TreeViewColumn to the TreeView. Then it creates a text Cell Renderer and applies that to the TreeViewColumn

The reason they are in three separate functions is that if you want to refresh the row data, you don't want to add the column data again. So I had to separate the adding rows from the adding rows and columns. The function addCellRenderers is separate because it is called by three different functions so I would have duplicate code if it was placed in fillLstPayees.  


Also before these functions are called I create GTK object references in an init function like this
[PHP]    def gladeInit(self):
        """ make all the glade objects we want as members of this class """
        self.lstPayments = self.wTree.get_widget("lstPayments")
        self.dtmPayment = self.wTree.get_widget("dtmPayment")
        self.txtPaymentPayee = self.wTree.get_widget("txtPaymentPayee")
        self.txtPaymentCategory = self.wTree.get_widget("txtPaymentCategory")
        self.txtCategoryName = self.wTree.get_widget("txtCategoryName")        
        self.lstCategories = self.wTree.get_widget("lstCategories")
        self.lstPayees = self.wTree.get_widget("lstPayees")
        self.cmbPaymentPayee = self.wTree.get_widget("cmbPaymentPayee")
        self.cmbPaymentCategory = self.wTree.get_widget("cmbPaymentCategory")
        self.txtPaymentTotal = self.wTree.get_widget("txtPaymentTotal")
        self.txtPayeeName = self.wTree.get_widget("txtPayeeName")
        self.txtAmount = self.wTree.get_widget("txtAmount")
        self.nudHours = self.wTree.get_widget("nudHours")
        self.nudMinutes = self.wTree.get_widget("nudMinutes")
        self.nudSeconds = self.wTree.get_widget("nudSeconds")
        self.txtPaymentMethod = self.wTree.get_widget("txtPaymentMethod")[/PHP]

Hope that helps.

---

