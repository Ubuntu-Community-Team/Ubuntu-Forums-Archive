---
title: "PyQt QTableView Help"
date: 2012-04-02
forum: Programming Talk
---

### Post by ngrieb on 2012-04-02
I have a QMainWindow containing a number of dock widgets that interact with eachother, and I have been having one problem that I cannot find the answer to. I have a QTableView widget that reads data from a nested list:

[[a, b, c, d][e, f, g, h][i, j ,k, l]] 

I import these features based on the users request from another widget, and use list item[0] as the vertical header. Everything looks fine until I attempt to append the list. When the main loop refreshes the screen I get repeating values for headers because I can't seem to find how to remove the header items permanently. If I use something like this:

```

self.table.verticalHeader().setVisible(False)
self.table.clearContents()
for i in range(0, self.table.rowCount()):
    self.table.removeRow(i)

... rename the headers and repopulate the table
self.table.verticalHeader().setVisible(True)

```

the problem is solved only for the first append? How can I fully remove the rows and their headers before refreshing the widget?
--------------------------------------------------------------------------------------------------------------------------------

After looking over my code I think the problem lies in my call to self.table.insertRow(i), but I am still unable to find a solution for a table which is changing info and or possibly growing row-wise.

---

### Post by benson444 on 2012-04-04
I haven't used Qt for a while but think the problem is with the call to removeRow(i) inside the loop and the fact that table rows are always indexable from 0 through rowCount() - 1.

On the first pass, row[0] is removed and what was row[1] becomes row[0]. Then you remove row[1], skipping over what was originally row[1], and so on.

Eventually you will be calling removeRow(i) with values that are larger than the remaining number of rows. It might help to see what is going on if it crashed with some kind of out-of-bounds error, but it doesn't. It just does nothing. You can try it with removeRow(rowCount() + 100) or something.

If you change the call to removeRow(0) then I think it'll work.

Also, you don't need to clearContents() before removing the rows. Removing a row will delete any items it contains, and the vertical header. In fact, I'm pretty sure you can replace clearContents() and the loop with a call to setRowCount(0) as that will delete all the rows and do pretty much exactly the same thing.

---

### Post by ngrieb on 2012-04-04
Thanks a lot! I had the same issue with list.pop(), while removing entities from the list that creates the table, but I was able to see what was going on in that case. I fixed this obvious problem by running a backwards loop. I think this might be the way to go with the table as well. Run a backwards loop from n->0, and remove rows, but setRowCount() might be a very simple solution as well i.e. -> setRowCount(0) then removeRow(0).
 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 
After attempting this, I found it doesn't work. :-( I keep getting th vertical header items, but as before, they don't refresh. Everything else refreshes, but the vertical headers just turn into mush. When I expand the window they turn into a black stripe. Any clue about how to fix this?

---

### Post by benson444 on 2012-04-05
Could you post some code that exhibits the problem you are having?

Maybe just a window with a table widget and a button that updates the rows and headers.

---

### Post by ngrieb on 2012-04-06
Ya, no problem. I'll post it in the next reply.
 
You wouldn't happen to know how to multithread a widget interface would you? 
 
I'm having one other problem with this code, and I think threading is the key: 
I have a button, that opens a seperate widget (window), and writes global information back to the main program. 
 
The problem is that the main window loop is stopped because of this process from the button, so the information I'm passing back doesn't get updated in the QLabel I'm attempting to write to while in this widget. I want it to dynamically update this QLabel.
 
Can I call the full widget interface via a thread or should I make this widget a child to the main? I have been searching for examples of this but have not found any. 
 
Pardon my ignorance on this matter. I have been using PyQt for a while, but never gone as far as on this project before. You seem much better versed in it than I am.
 
Thank you so much for the help.

---

### Post by ngrieb on 2012-04-06
```


    

global defs....

global List
List = []

MainWindow(QtMainWindow):

def __init__()...
     initUI()

def initUI(self):
   ...
   ...
   ...

   placing file and edit menus...
   
   self.connect(editAddAction, SIGNAL("triggered()"), self.addItem)


   def addItem(self):

         #BUILD TABLE LIST TO GET ITEMS FROM
         global List

         #REMOVE PREVIOUS ADDS IF POSSIBLE
         for i in range(self.table.rowCount(), -1, -1):
             self.table.removeRow(i)
         
         loops for reading data into a list here ....

         #SHOW IN TABLE VIEW    
         for i in range(0, len(List)):
             self.table.insertRow(i)
             for j in range(0, len(List[i])):
                 #HEADERS ARE BEING BYPASSED AT THE MOMENT, WORKS FINE WITHOUT VERTICAL HEADERS....???
                 #if j == 0:
                 #   itemname = QTableWidgetItem(str(List[i][j][0]))
                 #   self.table.setVerticalHeaderItem(i, itemname)
                 #else:
                 newItems = QTableWidgetItem(str(List[i][j][0]))
                 self.table.setItem(i, j, newItems) #>>>>> j-1 with vertical header <<<<
                 #SET HEADER FIELDS AS NON-EDITABLE
                 if j == 0 or j == 1:
                    data = self.table.item(i, j) #>>>>> j-1 with vertical header <<<<
                    data.setFlags(Qt.ItemIsEditable)


```Sorry if this is overly vague. I'm doing this for a work project, so there might be some odd concerns with proprietary rights (gag :-() etc.
As I mentioned in a comment, the problem only happens when I am using vertical headers.  I bypassed the problem by setting the isVisible() mode to False. 
As far as I know the main loop should be refreshing the vertical headers along with the data, but fails to do so...
Again thanks for the help. It is much appreciated.

---

### Post by benson444 on 2012-04-07
As far as I understand it, and I think it's pretty much the same in all GUI toolkits, there can only be one GUI thread. You can start other worker threads but they can't directly update the GUI.

If you want to use a dialog window or start a new thread, and dynamically update a widget in the main window, then I think the standard way is to set up a signal/slot between them. When you want to update the main window, emit the signal and pass the data back. You would do something like

```
# in main window class
def __init__(self, parent=None):
    # ...
    dialog = MyDialog(self)
    self.connect(dialog, SIGNAL("updateGUI"), self.updateLabel)

def updateLabel(self, data):
    self.label.setText(data)

# in dialog class
    self.emit(SIGNAL("updateGUI"), newData)
```

I don't see what's going wrong with the headers. Should work fine I reckon. Maybe, just to try something different, you could create a list that you want to use and call table.setVerticalHeaderLabels(headerList) after adding all the rows and cell data in the loop. I'd print out the list just to check it's correct too.

There doesn't seem to be many people here that use Qt, which is a shame because it's a really nice toolkit.

---

### Post by ngrieb on 2012-04-07
Ya, I agree. Qt offers a very large range of functionality and looks great. 

As for the headers, I'm not really sure that it is worth too much more dubug time, but I will let you know what is going on if I figure it out. You might be correct in thinking it is a list issue, because the horizontal header items are generally set using a QStringList (Maybe it is only setting one header that is then overwriting itself as I go down the list). 

I'll give the signals/slots update a go.

Again, thanks for all of the help.

---

