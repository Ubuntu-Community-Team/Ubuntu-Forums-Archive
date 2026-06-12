---
title: "Python Gui"
date: 2010-03-08
forum: Programming Talk
---

### Post by adedi on 2010-03-08
I'm a bit new to python gui programming. I have a code that retrieves all available databases but i want it to display the result in text area for me but this i a cant seem to do. Can anyone please help me?
I tried this line of code

 self.txt.insert(0.0, record)

but it comes up with error

I need help please

---

### Post by Anthon on 2010-03-08
> **adedi said:**
> I'm a bit new to python gui programming. I have a code that retrieves all available databases but i want it to display the result in text area for me but this i a cant seem to do. Can anyone please help me?
I tried this line of code

 self.txt.insert(0.0, record)

but it comes up with error

I need help please
It is very unclear which Python GUI builder you are using. But if self.txt is a list structure or a derivative, you probably do not want to use a float as the first argument (0.0) but an integer (0).

If that does not solve the issue, please be more clear about which GUI you are using and cut and paste the exact error message.

---

### Post by adedi on 2010-03-08
I am using Tkinter and here is the error message
self.txt is the Text area i created

Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1413, in __call__
    return self.func(*args)
  File "snoop.py", line 31, in connect_db
    self.txt.insert(0.0,record)
AttributeError: 'NoneType' object has no attribute 'insert'

---

### Post by Anthon on 2010-03-08
> **adedi said:**
> I am using Tkinter and here is the error message
self.txt is the Text area i created

Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1413, in __call__
    return self.func(*args)
  File "snoop.py", line 31, in connect_db
    self.txt.insert(0.0,record)
AttributeError: 'NoneType' object has no attribute 'insert'
it seems that self.txt is the None object. With what statement did you initialise that variable? Or should it be set by a parent class?

---

### Post by adedi on 2010-03-08
Here is the code

from Tkinter import *
import MySQLdb

class Snoop(Frame):
    def __init__(self, master):
        Frame.__init__(self, master)
        self.grid()
        self.create_widgets()

    def create_widgets(self):
        Label(self, text = "Database Name:").grid(row = 0, column = 0, sticky = W)
        Entry(self).grid(row = 0, column = 1, sticky = W)
        Button(self, text = "Submit", command = self.connect_db).grid(row = 1, column = 1, sticky = W)
        Label(self, text = "Tables:").grid(row = 2, column = 0, sticky = W)
        Label(self, text = "Information:").grid(row = 2, column = 1, sticky = W)
        self.txt = Text(self, width = 40, height = 5, wrap = WORD).grid(row = 3, column = 1, sticky = W)

    def connect_db(self):
        db= MySQLdb.connect(host="localhost", user="root" , passwd="abc")
        cursor = db.cursor()
        cursor.execute("show databases")
        result = cursor.fetchall()
        self.txt.delete(0.0, END)
        record = ""
        for record in result:
            record += record
        self.txt.insert(0.0,record)
                
        db.close


root = Tk()
root.title("Snoop")
start = Snoop(root)

root.mainloop()

---

### Post by Anthon on 2010-03-09
> **adedi said:**
> Here is the code

from Tkinter import *
import MySQLdb

class Snoop(Frame):
    def __init__(self, master):
        Frame.__init__(self, master)
        self.grid()
        self.create_widgets()

    def create_widgets(self):
        Label(self, text = "Database Name:").grid(row = 0, column = 0, sticky = W)
        Entry(self).grid(row = 0, column = 1, sticky = W)
        Button(self, text = "Submit", command = self.connect_db).grid(row = 1, column = 1, sticky = W)
        Label(self, text = "Tables:").grid(row = 2, column = 0, sticky = W)
        Label(self, text = "Information:").grid(row = 2, column = 1, sticky = W)
        self.txt = Text(self, width = 40, height = 5, wrap = WORD).grid(row = 3, column = 1, sticky = W)

    def connect_db(self):
        db= MySQLdb.connect(host="localhost", user="root" , passwd="abc")
        cursor = db.cursor()
        cursor.execute("show databases")
        result = cursor.fetchall()
        self.txt.delete(0.0, END)
        record = ""
        for record in result:
            record += record
        self.txt.insert(0.0,record)
                
        db.close


root = Tk()
root.title("Snoop")
start = Snoop(root)

root.mainloop()
It has been more than 13 years since I used TKInter so there might be more problems than I found at first glance:
1) Did you try this without connecting connect_db() to the submit button and clicking? 
2) In connect_db you do:
  record = ""
  for record in result:
     record += record
That is the same as:
  record = result[-1]
you probably want to do something like:
  record = ""
  for res in result:
     record += res

---

### Post by adedi on 2010-03-09
I tried print the record to the console and it worked also I tried creating in the for loop radio buttons and it worked

---

