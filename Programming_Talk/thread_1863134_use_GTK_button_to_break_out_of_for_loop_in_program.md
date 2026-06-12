---
title: "use GTK button to break out of for loop in program when pressed"
date: 2011-10-17
forum: Programming Talk
---

### Post by mushy365 on 2011-10-17
I'm making a gui program to copy lots of files from one place to another. There is a for loop that copies all files one at a time. Because i cant take so long i was looking for a way to implement a cancel button that would break out of the loop when pressed. But its just a basic for loop in a function i created and i dont know how to create an event to break out of it.

---

### Post by Smart Viking on 2011-10-17
You could connect the button to a function that sets a variable to something, and check the value for that variable in the for loop and break if it's some value. I'm not sure if this is gonna work.

---

### Post by mushy365 on 2011-10-17
thats what i actually thought of myself after i posted this thread, but ive been unable to test it though because when i run the part of my program to copy over the files, the files start copying but my gui application greys out. and i cant press any buttons or see the progress bar move. 

So i cant hit the stop sync button and i cant see the progress bar move. I know the progress bar is working thought because when i cancel the program in terminal the gui ungreys and i can see that the progress bar has updated and so has the scroll window. 

what would be causing the program to grey out? 
ill post the code

```

#!/usr/bin/env python

#imports
import os
import sys
import gtk
import glob
import pygtk
import shutil
import ConfigParser
pygtk.require('2.0')

class Base:

    def destroy(self,widget,data=None):
        gtk.main_quit() 
           

    def scanSourceDir(self,widget):
        self.srcDir = self.sourceTxtBox.get_text()
        self.sourcestore.clear()
        os.chdir(self.srcDir)
        self.srcfiles = glob.glob("*.*")
        
        for f in self.srcfiles:
           self.sourcestore.append([f])

       

    def scanDestDir(self,widget):
        self.dstDir = self.destTxtBox.get_text()
        print self.dstDir
        self.deststore.clear()
        os.chdir(self.dstDir)
        self.dstfiles = glob.glob("*.*")
        
        for f in self.dstfiles:
           self.deststore.append([f])

    def stopSyncFolders(self, widget):
        self.pbar.set_text("Cancelling...")   
        
    def syncFolders(self, widget):
        self.sd = self.sourceTxtBox.get_text()
        self.dd = self.destTxtBox.get_text()
        self.files_to_copy = 0
        self.files_copied = 0
        os.chdir(self.sd)
        self.ffiles = glob.glob("*.*")
        for f in self.ffiles:
            if not os.path.exists(self.dd + f):
               self.files_to_copy = self.files_to_copy + 1
        for f in self.ffiles:
           if not os.path.exists(self.dd + f):
              self.files_copied = self.files_copied + 1
              self.notice = "Copying file " + str(self.files_copied) + " of " + str(self.files_to_copy) + "( " + f + ")"
              self.pbar.set_text(self.notice)
              shutil.copyfile(self.sd + f, self.dd + f)
              self.deststore.append([f])
              self.pbar.pulse()  
              self.message = self.pbar.get_text()
              if self.message == "Cancelling...":
                break
        self.pbar.set_text("Done") 



    def __init__(self):
        #lets start developing
        #lets make main background window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_position(gtk.WIN_POS_CENTER)
        self.window.set_size_request(800,800)
        self.window.set_title("Pysync - Folder Sync")

        #create the vertical and horizontal boxes
        self.mainvbox = gtk.VBox()
        self.topaddrbox = gtk.HBox()
        self.topscrollwindowbox = gtk.HBox()
        self.bottomaddrbox = gtk.HBox()
        self.bottomscrollwindowbox = gtk.HBox()
        self.actionbar = gtk.HBox()
        
        #set the sizes of the hboxs
        self.topaddrbox.set_size_request(800,30)
        #self.topscrollwindowbox.set_size_request(800,300)
        self.bottomaddrbox.set_size_request(800,30)
        #self.bottomscrollwindowbox.set_size_request(800,300)
        self.actionbar.set_size_request(800,30)


        #########CREATE LISTSTORES###########
        self.sourcestore = gtk.ListStore(str)
        self.deststore = gtk.ListStore(str)
        #########CREATE LISTSTORES END########


        #########CREATE TREEVIEWS#######
        #creating the treeview object to put in src scroll window
        self.srctreeView = gtk.TreeView(self.sourcestore)
        #self.srctreeView.connect("row-activated", self.on_activated)
        self.srctreeView.set_rules_hint(True)

        #creating the treeview object to put in src scroll window
        self.dsttreeView = gtk.TreeView(self.deststore)
        #self.dsttreeView.connect("row-activated", self.on_activated)
        self.dsttreeView.set_rules_hint(True)
        #########CREATE TREEVIEWS END#########


        #######CREATE COLUMNS#########
         #creating the columns to be listen in the scroll window
        self.srcrendererText = gtk.CellRendererText()
        self.srccolumn = gtk.TreeViewColumn("Name", self.srcrendererText, text=0)
        self.srccolumn.set_sort_column_id(0)   
        self.srccolumn.set_sort_order(gtk.SORT_DESCENDING)
 
        self.srctreeView.append_column(self.srccolumn)

        #creating the columns to be listen in the scroll window
        self.dstrendererText = gtk.CellRendererText()
        self.dstcolumn = gtk.TreeViewColumn("Name", self.dstrendererText, text=0)
        self.dstcolumn.set_sort_column_id(0)    
        self.dstcolumn.set_sort_order(gtk.SORT_DESCENDING)

        self.dsttreeView.append_column(self.dstcolumn)
        ######CREATE COLUMNS END#######







        #Create the widgets to go in boxes
        #Fist topaddrbox  /label/textbox/button
        self.sourceLabel = gtk.Label("Source:")
        self.sourceTxtBox = gtk.Entry()
        self.sourceTxtBox.set_size_request(600,30)
        self.sourceTxtBox.set_text("/home/brian/Desktop/music/")
        self.sourceButton = gtk.Button("Set Folder")
        self.sourceButton.connect("clicked",self.scanSourceDir)
        

        #second topscrollwindowbox  scroll window and list
        self.ssw = gtk.ScrolledWindow()
        self.ssw.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.ssw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.ssw.add(self.srctreeView)

        #third bottomaddrbox /label/textbox/button
        self.destLabel = gtk.Label("Dest:")
        self.destTxtBox = gtk.Entry()
        self.destTxtBox.set_size_request(600,30)
        self.destTxtBox.set_text("/home/brian/Desktop/mus/")
        self.destButton = gtk.Button("Set Folder")
        self.destButton.connect("clicked",self.scanDestDir)


        #scan paths for files
        self.scanSourceDir(None)
        self.scanDestDir(None)
      
        #fourth bottomscrollwindowbox /scroll window and list
        self.dsw = gtk.ScrolledWindow()
        self.dsw.set_shadow_type(gtk.SHADOW_ETCHED_IN)
        self.dsw.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
        self.dsw.add(self.dsttreeView)

        #fifth actionbar
        self.syncButton = gtk.Button("Sync Folders")
        self.syncButton.connect("clicked",self.syncFolders)
 
        self.stopsyncButton = gtk.Button("Stop sync")
        self.stopsyncButton.connect("clicked",self.stopSyncFolders)
        
        self.pbar = gtk.ProgressBar()
        self.pbar.set_size_request(500,30)
        
        
        #now add all widgets to boxes.
        #topaddrbox
        self.topaddrbox.pack_start(self.sourceLabel,False,False,5)
        self.topaddrbox.pack_start(self.sourceTxtBox,False,False,5)
        self.topaddrbox.pack_start(self.sourceButton,False,False,5)

        #bottomaddrbox
        self.bottomaddrbox.pack_start(self.destLabel,False,False,5)
        self.bottomaddrbox.pack_start(self.destTxtBox,False,False,5)
        self.bottomaddrbox.pack_start(self.destButton,False,False,5)

        #topscrollwindowbox
        self.topscrollwindowbox.pack_start(self.ssw)

        #bottomscrollwindowbox
        self.bottomscrollwindowbox.pack_start(self.dsw)

        #actionbar
        self.actionbar.pack_start(self.pbar,False,False,5)
        self.actionbar.pack_start(self.syncButton,False,False,5)
        self.actionbar.pack_start(self.stopsyncButton,False,False,5)
        
        #add final horizontal boxes to vertical box
        self.mainvbox.pack_start(self.topaddrbox,False,False,5)
        self.mainvbox.pack_start(self.topscrollwindowbox)
        self.mainvbox.pack_start(self.bottomaddrbox,False,False,5)
        self.mainvbox.pack_start(self.bottomscrollwindowbox)
        self.mainvbox.pack_start(self.actionbar,False,False,5)

        
        #add the mainvbox to windown and display it
        self.window.add(self.mainvbox)
        self.window.show_all()
        self.window.connect("destroy",self.destroy)

    def main(self):
        gtk.main()


if __name__ == "__main__":
    base = Base()
    base.main()

```

---

### Post by mushy365 on 2011-10-17
Sorry to keep bumping but could anyone help me with this, been working on it all day, and its so close to being finished i just need the whole gui not to grey out when it starts copying fiels 

i cant even find any google pages on it. Ive no idea how to troubleshoot it.

---

### Post by StephenF on 2011-10-17
Put this in your for loop.
```

while gtk.events_pending():
    gtk.main_iteration()

```

---

### Post by tbastian on 2011-10-17
I'm pretty sure what is happening here is that when your program is in the for loop, you are not allowing the gtk main loop to run. What you might have to do is have your copying loop in a separate thread. The only thing is Gtk doesn't deal with threads very well. You would have to look up how to do that safely.

---

### Post by mushy365 on 2011-10-17
That worked perfectly, can you explain what thats doing? 

Also any idea how i could stop that for loop with a button?

---

### Post by StephenF on 2011-10-18
> **mushy365 said:**
> That worked perfectly, can you explain what thats doing? 

Also any idea how i could stop that for loop with a button?
Set a control variable, if breakout == True: break

The gtk main loop stops in its tracks stuck in your callback routine. The additional code runs the gtk main loop as needed to continue processing events and redrawing the widgets.

---

### Post by crdlb on 2011-10-19
Another approach would be to perform the copying [asynchronously with GIO]("http://www.pygtk.org/docs/pygobject/class-giofile.html#method-giofile--copy-async"). After each copy is completed, the callback you supply will be called. You can then schedule the next copy with glib.idle_add. This way the UI will never block, not even during the copying of individual files.

---

