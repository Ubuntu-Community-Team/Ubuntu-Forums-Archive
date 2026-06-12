---
title: "tkinter askdirectory question"
date: 2009-07-20
forum: Programming Talk
---

### Post by dalandtwist on 2009-07-20
Hello,

I need to get the name of a directory and place that name into a label widget.  

Currently I am using the askdirectory function to open the browser and select a folder.  like below and that seems to work no prob.

def Selectjob(self):
    dir1 = askdirectory(title="Select the Job Folder", mustexist=1)
  
What I need to figure out is how to insert that dir1 value (the directory path) into a 
label. What I have below is not working.  I am pretty new at this, and feel like I have somekind of syntax error.

self.lbl = Label(self, text="dir1.get()" )
self.lbl.grid(row=3, column=5)

Any ideas?

thanks!

david

---

### Post by smartbei on 2009-07-20
Just take it out of the quotes:
```

self.lbl = Label(self, text=dir1.get())
self.lbl.grid(row=3, column=5)

```
Does that work?

EDIT: more info:
To change it after it has been created check out the reference here [http://effbot.org/tkinterbook/label.htm](http://effbot.org/tkinterbook/label.htm).

---

### Post by dalandtwist on 2009-07-20
Thank you for replying.  I tried removing the quotes but no luck.  I have attached my script.  It's a simple folder building tool but I need the ability to choose a directory so I can add additional folders when needed.  Any help is appreciated.  I am new to Tkinter and Python but am very interested in learning.  I commented out the area where I am having problems.

thank you all,

david

---

### Post by stevescripts on 2009-07-21
dalandtwist,

No time right now to look at your script.

A quickie hack that might help with your problem:

```

#!/usr/bin/python

from Tkinter import *
from tkFileDialog import *

def the_dir():
	dirname = askdirectory()
	label.configure(text = dirname)

main = Tk()

button = Button(main, text = "Choose Directory", command = the_dir)
label = Label(main)

button.pack()
label.pack()

main.mainloop()

```

If this doesn't help, will try to find time to look at your script.

Steve

---

### Post by dalandtwist on 2009-07-21
hi steve,

I tried you code and it works fine on it's own but I get errors when I try to implement. 
Maybe the problem is because I am using grid.  Not sure. Would appreciate any pointers.

thank you all,

david

---

### Post by stevescripts on 2009-07-21
david,

grid is *NOT* the problem - I took a quick look at your script, and still don't have time right now to help you clean it up a bit. (it appears to be a scope problem, on a quick glance) Maybe tommorrow...

Steve

---

### Post by stevescripts on 2009-07-22
hmm ... I thought I had it fixed, but I don't...

I find your widget naming ... unusual ... and the indentation and program flow a bit confusing.

Maybe I can find some more time later. Gotta pay attention to paywork.

Steve

---

### Post by smartbei on 2009-07-22
If you want the user to select the directory before he even sees the gui, change the part you are confused about to this:
```

	self.Selectjob()
	self.lbl = Label(self, text=self.dirshotname)
	self.lbl.grid(row=3, column=5)

```
That works for me, but is really unintuitive.

I think what you really want is that if the user clicks on "Click to Select Job", to THEN set the label. If so, change the problematic code to:
```

	self.lbl_string = StringVar()
	self.lbl = Label(self, textvariable = self.lbl_string)
	self.lbl.grid(row=3, column=5)

```
and change the method Selectjob to:
```

def Selectjob(self):
        self.lbl_string.set(tkFileDialog.askdirectory())

```

Note that askdirectory returns either a string with the directory path, or None on failure (user canceled, etc.). Make sure to add error checking code to deal with the case of None.

Also, note that your code is really mess with its indentation; there are spaces and tabs mixed...yech. Best Practice for python is considered 4 spaces per indentation level. Lastly, you don't really need to keep every single one of your GUI elements as members of the class, and if you do, then make sure not to override them (like you do (probably accidentaly due to copy/paste) with the labels).

---

### Post by stevescripts on 2009-07-22
smartbei - Glad you found the time I havent been able to make.

david - make sure you understand what smartbei is saying about your code (and the overriding of the label names)

EDIT:  It seems to me, that it might be a good idea to use separate frames for each section of you GUI to help reduce possible user confusion

Steve

---

### Post by dalandtwist on 2009-07-22
Steve, Smartbei,

Thank you very much for your insight, I am brand new at this and will take your comments and work on it tonight.  I am grateful for your time.

-david

---

### Post by smartbei on 2009-07-22
No problem - we are always happy to help, and generally I find that I learn something new every time :-). (In this case, StringVar was a new one for me)

---

