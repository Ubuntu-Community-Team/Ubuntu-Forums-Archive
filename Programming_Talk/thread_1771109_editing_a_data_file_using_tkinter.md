---
title: "editing a data file using tkinter"
date: 2011-05-30
forum: Programming Talk
---

### Post by Bigmon on 2011-05-30
I wonder if someone can help me with something probably quite simple, but which I am struggling with. I am using tkinter, and want the user of the program to be able to open a data file, edit the file in  a text box, and then write the edited contents to the file again. 

The problem is the contents of the file come in as a list of numbers, and then are converted to text in the text box. I do not know how to restore the edited text as numbers again in the data file. In addition, the numbers were added to the file originally with each number on a newline.```


    def edit(self,file):

        filename = file
        FILE = open(filename,"r")
        lines = FILE.readlines()
        
        j = []
        for line in lines:
            j.append(float(line))

            window = Tk()
            frame = Frame(window)
            frame.pack()

            self.text = Text(frame)
            
            self.text.insert(END,j)
            self.text.pack()
            new_button = Button(frame, text="Save",    command=lambda : self.save_changes(file))
            new_button.pack()
            window.mainloop()
            
            
          def save_changes(self,file):
             n = self.text.get("0.0",END)
              

```

"save_changes" gets the edited text in the form [12.0, 13.6, 67.9] for example ,and it is this that I want to write to a file in the form:
12.0
13.6
67.9

Am I making it more complicated that need be ?

---

### Post by gmargo on 2011-05-30
I would not bother converting the input strings into floating point.  Just keep them as strings, since the text area widget works with strings anyway.

On the output side, I did a rather crude parsing.  I didn't really want to use eval() since Joe User could type anything.

See if this helps:
```

#!/usr/bin/python
import random
from Tkinter import*
import re

class Foo:
    def edit(self,file):
        FILE = open(file,"r")
        lines = FILE.readlines()
        FILE.close()
        
        j = []
        for line in lines:
            #j.append(float(line))
            j.append(re.sub(r'\s+\Z', '', line))     # strip trailing whitespace, newline

        # Do you want this to look like a list?
       #before = '[' + ", ".join(j) + "]"
        # Or just a set of numbers?
        before = " ".join(j)

        window = Tk()
        frame = Frame(window)
        frame.pack()

        self.text = Text(frame)

        self.text.insert(END,before)
        self.text.pack()
        new_button = Button(frame, text="Save",    command=lambda : self.save_changes(file))
        new_button.pack()
        window.mainloop()


    def save_changes(self,file):
        after = self.text.get("0.0",END)
        #print "after=",after

        # Strip all the characters we don't care about
        line = after
        line = re.sub(r',', ', ', line)         # make sure space follows any comma
        line = re.sub(r'[\[\],]', '', line)     # strip brackets, commas
        line = re.sub(r'^\s+', '', line)        # strip leading space
        line = re.sub(r'\s+\Z', '', line)       # strip trailing space
        line = re.sub(r'\s+', ' ', line)        # compress spaces
        line = re.sub(r'[^-+.0-9 ]', '', line)  # strip non-digits, plus, minus, space
        numbers = line.split(" ")               # split string into array

        #FILE = open(file,"w")       # Dangerous to overwrite input
        FILE = open("out.txt","w")   # Use this test file instead for now
        for num in numbers:
            FILE.write(num + '\n')
        FILE.close()


foo = Foo()
foo.edit("num1.txt")
# vim: set ts=8 sts=4 sw=4 et :

```

---

### Post by Bigmon on 2011-05-31
Many thanks. That is a great help !! :D

---

### Post by samiam1000 on 2012-10-11
And what about if I would like to edit a file?

I mean.. Let's say that I have such a file:
```

John 1
Andrew 2
Sam 0

```

and I wanna edit it like this:
```

John 1 1
Andrew 2 1
Sam 0 2

```

what should I do?

Also, is it possible to have a table instead of a plain-text file?

Could you help?

Thanks a lot,
Samuele

---

