---
title: "Glade/Python. Dialog only works once."
date: 2011-07-08
forum: Programming Talk
---

### Post by Chris_no on 2011-07-08
I have the following program in two python files plus an xml file from
glade and a little txt-file containing the data.

```
#!/usr/bin/python

from gui_func import * 
    
if __name__ == "__main__":
    go = Start()
    go.window.show()
    gtk.main()
```

```
import sys, gtk, re

class Start:
    
    #Gets the gui data from the xml file and gets everything rolling
    def __init__(self):
        
        #Link up builder with xml
        builder = gtk.Builder()
        builder.add_from_file("search_layout.xml")
        #Make builder exportable to the other function with self
        self.build = builder 
        
        #Link up to main window
        self.window = builder.get_object("main_window")
        #Find all the signals
        builder.connect_signals(self)
    
    #Destroys the program when x is clicked    
    def on_main_window_destroy(self, widget, data=None):
        gtk.main_quit()
    
    #Destroy the dialog 
    #Trouble finding a use for this
    def on_dialog1_destroy(self, widget, data=None):
        pass

    #When a row is clicked launch another window with edit capabilities.    
    def on_treeview1_row_activated(self, path, column, param):
        self.dialog = self.build.get_object("dialog1").show()
            

    #Collects the data from the entry field and calls the search function  
    def on_btn_clicked(self, widget):
        #Get the term to search on
        info = self.build.get_object('entry_one').get_text()
    
        keep_lines = [] #Holds the matches to be sent back
        file_1 = open('kunder.dat', 'r') #Opens the database file
            
        #Flag for dropping first line
        flag = 1
            
        #Taking one line at a time
        for line in file_1:
            #Checking if this is first line and dropping it if it is
            if flag == 1:
                flag = 0
                continue
                
            #Check if the search term matches the search
            if re.search(info, line, re.I):
                keep_lines.append(line)
            
        file_1.close()
        
        to_send = [] #List to hold element of match each line
            
        #Get the liststore object
        store = self.build.get_object("liststore1")
        #Clear the rows for new results
        store.clear()
            
        #Split the object into parts and add to list    
        for items in keep_lines:
            to_send = items.split(";")
            store.append([to_send[0], to_send[1], to_send[2], to_send[3], to_send[4], to_send[5]])
```

When I open the dialog when pressing the data in treeview,
I get the dialog properly.
If I then close the dialog and open it again I get a tiny compressed
window with nothing in it with the title of the first script "start.py".
I can't understand why this is so.
Anyone?

---

### Post by Chris_no on 2011-07-08
Found the solution on another forum.
```
import sys, gtk, re

class Start:
    
    #Gets the gui data from the xml file and gets everything rolling
    def __init__(self):
        
        #Link up builder with xml
        self.build = gtk.Builder()
        self.build.add_from_file("search_layout.xml")
        
        #Link up to main window
        self.window = self.build.get_object("main_window")
        #Find all the signals
        self.build.connect_signals(self)
    
    #Destroys the program when x is clicked    
    def on_main_window_destroy(self, widget, data=None):
        gtk.main_quit()
    
    #Destroy the dialog
    def on_dialog1_destroy(self, widget, data=None):
        pass

    #When a row is clicked launch another window with edit capabilities.    
    def on_treeview1_row_activated(self, path, column, param):
        dialog()
            

    #Collects the data from the entry field and calls the search function  
    def on_btn_clicked(self, widget):
        #Get the term to search on
        info = self.build.get_object('entry_one').get_text()
        
        search_terms = [] #Container for the different search terms
        search_terms = info.split(" ")
    
        keep_lines = [] #Holds the matches to be sent back
        file_1 = open('kunder.dat', 'r') #Opens the database file
            
        flag = 1 #Flag for dropping first line
        truth = 0 #Check if whole search term matches
            
        #Taking one line at a time
        for line in file_1:
            #Checking if this is first line and dropping it if it is
            if flag == 1:
                flag = 0
                continue
                
            #Check if the search term matches the search
            for term in search_terms: 
                if re.search(term, line, re.I):
                    pass
                else:
                    truth = 1
            #
            #End of inner_loop
            #
            
            #Adding the line if it matches all the terms        
            if truth == 0:    
                keep_lines.append(line)
                
            truth = 0    
            
        #
        #End of outer_loop
        #    
        
        #Closing the file after use    
        file_1.close()
        
        to_send = [] #List to hold element of match each line
            
        #Get the liststore object
        store = self.build.get_object("liststore1")
        #Clear the rows for new results
        store.clear()
            
        #Split the object into parts and add to list    
        for items in keep_lines:
            to_send = items.split(";")
            store.append([to_send[0], to_send[1], to_send[2], to_send[3], to_send[4], to_send[5]])
        
        
class dialog:

    #Starts the dialog
    def __init__(self):
        self.build = gtk.Builder()
        self.build.add_from_file("search_layout.xml")
        self.dialog = self.build.get_object("dialog1").show()
        self.build.connect_signals(self)
```

---

