---
title: "Python Tkinter Text widget help"
date: 2010-09-28
forum: Programming Talk
---

### Post by kerimabdullah on 2010-09-28
#Hi friends, I want help how to select lines in text widget 
#when I press Ctrl+a , the lines are not selected My codes are below please help
[LEFT] 
from Tkinter import *
root = Tk()
 
def textselect(event):
    print " you pressed ctrl+a "
    #mytextbox.selection(1.0, end) how will be?
 
mytextbox=Text(root,exportselection=1,selectbackground="orange")
for i in range(10):
    mytextbox.insert(END,"Line Line Line\n")
 
mytextbox.bind('<Control-a>', textselect)
mytextbox.pack(fill='both', expand=1)
root.mainloop()[/LEFT]

---

