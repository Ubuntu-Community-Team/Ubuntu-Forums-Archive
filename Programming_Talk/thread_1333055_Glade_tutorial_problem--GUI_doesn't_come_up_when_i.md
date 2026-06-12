---
title: "Glade tutorial problem--GUI doesn't come up when it should"
date: 2009-11-21
forum: Programming Talk
---

### Post by SoftwareExplorer on 2009-11-21
Hi.
I'm trying to learn how to make GUI's for python with glade, and I'm following this tutorial:
[[COLOR="DeepSkyBlue"]http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/[/COLOR]]("http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/"). However, the program doesn't do anything when it should be showing the gui. When I use the tutorial's .glade file, it worked, but when I use the one I made (which is the pywine2.txt file I attached, I had to change the extention from .glade for the forums), it doesn't work.

I'm using glade 3.6.7 . If you could tell me what I'm doing wrong and how to fix it, I would greatly appreciate it.

GTK/ .glade (libglade) file is attached.

Python:
```
import sys
try:
    import pygtk
    pygtk.require("2.0")
except:
    print "lines 3 or 4 failed"

try:
    import gtk
    import gtk.glade
except:
    print "lines 9 or 10 failed"
    sys.exit(1)

class pyWine:
    def __init__(self):
        #Set the Glade file
        self.gladefile = "pywine2.glade"
        self.wTree = gtk.glade.XML(self.gladefile, "mainWindow")
        #Create our dictionay and connect it
        dic = {"on_mainWindow_destroy" : gtk.main_quit
        , "on_AddWine" : self.OnAddWine}
        self.wTree.signal_autoconnect(dic)
        #Here are some variables that can be reused later
        self.cWine = 0
        self.cWinery = 1
        self.cGrape = 2
        self.cYear = 3
        
        self.sWine = "Wine"
        self.sWinery = "Winery"
        self.sGrape = "Grape"
        self.sYear = "Year"
        #Get the treeView from the widget Tree
        self.wineView = self.wTree.get_widget("wineView")
        #Add all of the List Columns to the wineView
        self.AddWineListColumn(self.sWine, self.cWine)
        self.AddWineListColumn(self.sWinery, self.cWinery)
        self.AddWineListColumn(self.sGrape, self.cGrape)
        self.AddWineListColumn(self.sYear, self.cYear)
        #Create the listStore Model to use with the wineView
        self.wineList = gtk.ListStore(str, str, str, str)
        #Attache the model to the treeView
        self.wineView.set_model(self.wineList)
    
    def AddWineListColumn(self, title, columnId):
        """This function adds a column to the list view.
        First it create the gtk.TreeViewColumn and then set
        some needed properties"""
        #
        column = gtk.TreeViewColumn(title, gtk.CellRendererText(), text=columnId)
        column.set_resizable(True)
        column.set_sort_column_id(columnId)
        self.wineView.append_column(column)
    
    def OnAddWine(self, widget):
        """Called when the use wants to add a wine"""
        #Cteate the dialog, show it, and store the results
        wineDlg = wineDialog();
        result,newWine = wineDlg.run()
        
        if (result == gtk.RESPONSE_OK):
            """The user clicked Ok, so let's add this
            wine to the wine list"""
            self.wineList.append(newWine.getList())

class wineDialog:
    """This class is used to show wineDlg"""
    
    def __init__(self, wine="", winery="", grape="", year=""):
        
        #setup the glade file
        self.gladefile = "pywine2.glade"
        #setup the wine that we will return
        self.wine = Wine(wine,winery,grape,year)
        
    def run(self):
        """This function will show the wineDlg"""
        
        #load the dialog from the glade file
        self.wTree = gtk.glade.XML(self.gladefile, "wineDlg")
        #Get the actual dialog widget
        self.dlg = self.wTree.get_widget("wineDlg")
        #Get all of the Entry Widgets and set their text
        self.enWine = self.wTree.get_widget("enWine")
        self.enWine.set_text(self.wine.wine)
        self.enWinery = self.wTree.get_widget("enWinery")
        self.enWinery.set_text(self.wine.winery)
        self.enGrape = self.wTree.get_widget("enGrape")
        self.enGrape.set_text(self.wine.grape)
        self.enYear = self.wTree.get_widget("enYear")
        self.enYear.set_text(self.wine.year)
        
        #run the dialog and store the response
        self.result = self.dlg.run()
        #get the value of the entry fields
        self.wine.wine = self.enWine.get_text()
        self.wine.winery = self.enWinery.get_text()
        self.wine.grape = self.enGrape.get_text()
        self.wine.year = self.enYear.get_text()
        
        #we are done with the dialog, destory it
        self.dlg.destroy()
        
        #return the result and the wine
        return self.result,self.wine

class Wine:
    """This class represents all the wine information"""
    
    def __init__(self, wine="", winery="", grape="", year=""):
        
        self.wine = wine
        self.winery = winery
        self.grape = grape
        self.year = year
    
    def getList(self):
        """This function returns a list made up of the
        wine information.  It is used to add a wine to the
        wineList easily"""
        return [self.wine, self.winery, self.grape, self.year]

if __name__ == "__main__" :
    wine = pyWine()
    gtk.main()
```

---

### Post by giuspen on 2009-11-21
I would advice you [this]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html") tutorial

---

### Post by SoftwareExplorer on 2009-11-21
I saw that, but when I picked a tutorial to start with, but it was too complicated too soon for me. I would just like to understand what I'm doing wrong.

---

### Post by ib.lundgren on 2009-11-22
PyGTK doesnt automaticly display your GUI, you need to do that yourself. Adding a line like this in the end of your init will do wonders.

[PHP]class pywine:
    def __init__(self):
    ...
    ...
    self.wTree.get_widget("mainWindow").show()[/PHP]

Also you have forgotten to rename the dialog in glade to "wineDlg", it is still called "dialog1" which is default in glade.

---

### Post by Olav on 2009-11-22
In Glade, did you forget to set Visible = Yes on the window? Happens to me all the time...

---

### Post by SoftwareExplorer on 2009-11-22
> **ib.lundgren said:**
> PyGTK doesnt automaticly display your GUI, you need to do that yourself. Adding a line like this in the end of your init will do wonders.

[PHP]class pywine:
    def __init__(self):
    ...
    ...
    self.wTree.get_widget("mainWindow").show()[/PHP]

Also you have forgotten to rename the dialog in glade to "wineDlg", it is still called "dialog1" which is default in glade.

After fixing the 'wineDlg' error you mentioned and setting that main window to visible, it works. I didn't have to add the last line for the __init__. It makes sense to have to do that, I did read you need to do that somewhere. So why is it "mysteriously" working? Also, what good does the gtk.main() do when the window comes up right after you do wine = pyWine()? 

> **Olav said:**
> In Glade, did you forget to set Visible = Yes on the window? Happens to me all the time...

Ding Ding Ding We have a winner. How could I forget? ](*,)

---

