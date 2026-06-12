---
title: "Python Help"
date: 2013-05-27
forum: Programming Talk
---

### Post by HernanLinux93 on 2013-05-27
Hello Everyone, I am fairly new to Python in fact is the first langauge I am trying to learn and I have been Reading several books and watching some YouTube videos. What I am trying to do is create a window with a botton here is the code: from tkinter import *
from tkinter import messagebox
app = Tk()
def helloCallBack():
    tkMessageBox.showinfo( "Hello Python", "Hello World")
 
B = Tkinter.Button(top, text = "Hello", command = helloCallBack)
B.pack()
top.mainloop()                         the thing is that I am getting several errors and I cant run it maybe some of you out there that know a bit more about Python could understand what is going on, thanks a lot for any help :)   btw I am using IDLE 3.2.5

---

### Post by Vorlog on 2013-05-28
> **HernanLinux93 said:**
> Hello Everyone, I am fairly new to Python in fact is the first langauge I am trying to learn and I have been Reading several books and watching some YouTube videos. What I am trying to do is create a window with a botton here is the code: from tkinter import *
from tkinter import messagebox
app = Tk()
def helloCallBack():
    tkMessageBox.showinfo( "Hello Python", "Hello World")
 
B = Tkinter.Button(top, text = "Hello", command = helloCallBack)
B.pack()
top.mainloop()                         the thing is that I am getting several errors and I cant run it maybe some of you out there that know a bit more about Python could understand what is going on, thanks a lot for any help :)   btw I am using IDLE 3.2.5

```
from Tkinter import *


app = Tk()
def helloCallBack():
    tkMessageBox.showinfo( "Hello Python", "Hello World")

    B = Tkinter.Button(top, text = "Hello", command = helloCallBack)
    B.pack()

app.mainloop()
```

This code work for me. What error are you getting?

Don't use the IDLE, it's inconvenient. Try IDE Ninja [http://ninja-ide.org/](http://ninja-ide.org/)

---

### Post by Tony Flury on 2013-05-30
I would suggest for a simple program like this then an IDE is complete overkill - and actually gets in the way.

I personally would encourage you to learn using a text editor and the python console, and use an IDE when you start working on large multiple file projects.

---

