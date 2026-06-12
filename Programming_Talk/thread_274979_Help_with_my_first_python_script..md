---
title: "Help with my first python script."
date: 2006-10-10
forum: Programming Talk
---

### Post by pod25 on 2006-10-10
Below is my first python / Tkinter  script.
My questions are below the code.
And please be nice, I'm still learning ;) 
```
#! /usr/bin/env python
from Tkinter import *
import tkMessageBox

class GUIFramework(Frame):
    
    
    def __init__(self,master=None):
        
        
        
        Frame.__init__(self,master)
        
       
        self.master.title("FTP CREATING - TOOL")
        self.configure(height=300,width=300)
        
        self.grid(padx=15, pady=15,sticky=N+S+E+W)
        self.CreateWidgets()
       
    def CreateWidgets(self):
        
        
        self.lbRSSSiteText = Label(self, text="Select Folders:")
        self.lbRSSSiteText.grid(row=0, column=0, sticky=W)
        self.lbRSSItemText = Label(self, text="User Name - Password:")
        self.lbRSSItemText.grid(row=0, column=6, sticky=E)
        
        
        self.lbSites = Listbox(self, selectmode=BROWSE, relief=SUNKEN, bg="black")
                        
        self.lbSites.grid(row=1, column=0)
        
        
        self.btn1Add = Button(self, text="Browse")
        self.btn1Add.grid(column=5, row=1, padx=5, sticky=N, pady=35)
        
        
        self.lbText = Label(self, text="Skeleton Folder :")
        self.lbText.grid(column=0, row=1, sticky=N, pady=35)
        
        
        self.enText = Entry(self, bg="white")
        self.enText.grid(column=1, row=1, columnspan=3, sticky=N, pady=35)
        
        
        self.btn2Add = Button(self, text="Browse")
        self.btn2Add.grid(column=5, row=1, padx=5, sticky=S, pady=35)
        
        
        self.lbText = Label(self, text="Home Folder :")
        self.lbText.grid(column=0, row=1, sticky=S, pady=35)
        
        
        self.enText = Entry(self, bg="white")
        self.enText.grid(column=1, row=1, columnspan=3, sticky=S, pady=35)
        
        
        
        self.btn3Add = Button(self, text="Apply Changes")
        self.btn3Add.grid(column=0, row=2, stick=W, pady=5)
        
          
        self.btnRemove = Button(self, text="Cancel",)
        self.btnRemove.grid(column=9, row=2, stick=W, pady=5)
    
        
        self.btnReset = Button(self, text="Reset")
        self.btnReset.grid(column=2, row=2, stick=W, pady=5)
        
        self.lbSites.grid(row=1, column=0, columnspan=40, sticky=N+W+S+E)
        
      
        spaceframe = Frame(self, width=25)
        spaceframe.grid(column=5,row=3)
        
        
        self.lbsSites = Listbox(self, selectmode=BROWSE, relief=SUNKEN, bg="black")
                        
        self.lbsSites.grid(row=1, column=6)
        
        
        self.lbText = Label(self, text="User-Name :")
        self.lbText.grid(row=1, column=6, sticky=N+W, pady=35, padx=5)
        
        
        self.enText = Entry(self, bg="white")
        self.enText.grid(row=1, column=7, columnspan=3, sticky=N+W, pady=35, padx=5)
        
       
        self.lbText = Label(self, text="Password :")
        self.lbText.grid(row=1, column=6, sticky=S+W, pady=35, padx=5)
        
       
        self.enText = Entry(self, bg="white")
        self.enText.grid(row=1, column=7, columnspan=3, sticky=S+W, pady=35, padx=5,)
        
        
        self.btn4Add = Button(self, text="Create Account")
        self.btn4Add.grid(column=6, row=2)
        
        self.lbsSites.grid(row=1, column=6, columnspan=40, sticky=N+W+S+E)
                  
if __name__ == "__main__":
     guiFrame = GUIFramework()
     guiFrame.mainloop()
```
So question 1 :
How do I create the "Quit Function" As in when I hit "Cancel" it closes the entire program down ?

Question 2 :
How do I create the "Browse Function" So I can browse for the 2 required folders ?

Question 3 :
How do I set the "Apply Changes" and "Create Account" to communicate with a mysql database ?

And question 4 :
How do I create the "Reset Function" to reset everything entered without closing the program down ?

---

### Post by pod25 on 2006-10-11
So far I have figured this bit out
By "Browse" Button now works, I found this :
```
from tkFileDialog   import askopenfilename

```
```
self.btn1Add = Button(self, text="Browse", command=askopenfilename)
```
I'm still trying to figure the rest out.

---

### Post by kwalo on 2006-10-11
Your variable nameing is horrible! 'btn1Add' variable doesn't mean anything to me! Change the variable names, so that they have some meaning. Your code would be more readable, if you had variables like 'browseHomeButton'. The code would be easier to read for you and anyone, who's planning to hack on this.

> **pod25 said:**
> So question 1 :
How do I create the "Quit Function" As in when I hit "Cancel" it closes the entire program down ?This is simple just add one line, you know where ;):```
self.btnRemove["command"] = self.quit
```

> **pod25 said:**
> Question 2 :
How do I create the "Browse Function" So I can browse for the 2 required folders ?First, you're using self.enText to create Text entries. That's not good, because you need to get and set information within that entries. You should replace enText with something like:```
        self.homeText = Entry(self, bg="white")
        self.homeText.grid(column=1, row=1, columnspan=3, sticky=S, pady=35)
...
        self.skeletonText = Entry(self, bg="white")
        self.skeletonText.grid(column=1, row=1, columnspan=3, sticky=N, pady=35)
```

Create this function in your main class:```
    def StoreFilename(self, store):
        name = askopenfilename()
        if (name):
            storelen = len(store.get())
            if storelen > 0:
                homeText.delete(0,storelen)
            store.insert(0,name)
```The store parameter is a Text Entry we want to store the value of filename.
Create two other functions within the main class:```
    def GetHomeFolder(self):
        self.StoreFilename(self.homeText)

    def GetSkeletonFolder(self):
        self.StoreFilename(self.skeletonText)
```Now you need to assign theese functions to proper widgets:```
        self.btn1Add["command"] = self.GetSkeletonFolder
...
        self.btn2Add["command"] = self.GetHomeFolder

```Theese two lines should be put in CreateWidgets() function. Other way to achieve this is through bind() call. Read about it in Python Reference Manual to learn more...

Hope that helped you a little ;)

---

### Post by pod25 on 2006-10-12
Thankyou kwalo

It most certainly did help. I have renamed the lines you suggested, now when I look at the source it makes more sense.

Now I have made a mistake, I do not want to open a file I want to open a folder when the Browse Button is pressed ?

---

### Post by junglepeanut on 2006-10-13
Bad_names == job_security .or. fortran_programmer

jk

---

### Post by pod25 on 2006-10-13
> **junglepeanut said:**
> Bad_names == job_security .or. fortran_programmer

jk

???

---

### Post by slavik on 2006-10-13
> **junglepeanut said:**
> Bad_names == job_security .or. fortran_programmer

jk
why? just use perl :P

---

### Post by nereid on 2006-10-14
Perl? Just real assembler. Nothing beats some MOV statements :D

---

### Post by cwaldbieser on 2006-10-14
> 
Bad_names == job_security .or. fortran_programmer

jk
> **pod25 said:**
> ???
This is just a joke.  The idea is that if no one else can read your code, then the boss needs to keep you around to maintain it.

---

### Post by pod25 on 2006-10-14
> **cwaldbieser said:**
> This is just a joke.  The idea is that if no one else can read your code, then the boss needs to keep you around to maintain it.
I am the boss :-D 

Now back to this script. I know how to browse for files, but whats the code to browse for "Folders"  ?

---

### Post by pod25 on 2006-10-15
I no longer need the Browse button as the Home Folder and Skeleton Folder will always be the same, so I have removed them and set it as text.

I now know how to connect to a MySQL database, but I'm not fully sure how to link all this together:
```
 """Create the Text User-Name"""
        self.UserText = Label(self, text="User-Name :")
        self.UserText.grid(row=1, column=6, sticky=N+W, pady=35, padx=5)
        
        """Create the Entry, set it to be a bit wider"""
        self.UserTextBox = Entry(self, bg="white")
        self.UserTextBox.grid(row=1, column=7, columnspan=3, sticky=N+W, pady=35, padx=5)
        
        """Create the Text Password"""
        self.PassText = Label(self, text="Password :")
        self.PassText.grid(row=1, column=6, sticky=S+W, pady=35, padx=5)
        
        """Create the Entry, set it to be a bit wider"""
        self.PassTextBox = Entry(self, bg="white")
        self.PassTextBox.grid(row=1, column=7, columnspan=3, sticky=S+W, pady=35, padx=5,)
        
        """Create the Create Account Button"""
        self.AccountBTN = Button(self, text="Create Account")
        self.AccountBTN.grid(column=6, row=2)
```

---

### Post by junglepeanut on 2006-10-16
from tkFileDialog import *
dir = askdirectory()
print dir


oops just read and I think you have changed it so you do not need this.

Google search showed it to me.

---

