---
title: "Python gui/Tkinter question"
date: 2007-05-08
forum: Programming Talk
---

### Post by baltimark on 2007-05-08
So, I was sort of following along with an online tutorial, and is often the case, the first time I tried to branch out, I got behavior I didn't understand. 

```
# File: guitest.py

from Tkinter import *

class App:

    def __init__(self, master):

        frame = Frame(master)
        frame.pack()

        self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
        self.button.pack(side=LEFT)

        self.hi_there = Button(frame, text="Hello", command=self.say_hi)
        self.hi_there.pack(side=LEFT)

##baltimark's additions
        s = "Hello."
        self.test = Button(frame, text="Hello2", command=self.say_hello(s))
        self.test.pack(side=LEFT)

##original function defintion
    def say_hi(self):
        print "hi there, everyone!"

##baltimark's addition
    def say_hello(self, s):
        print s

root = Tk()

app = App(root)

root.mainloop()



```

run with 

>> python guitest.py

now, self.hi_there works just like you would expect. A button with "helllo" pops up and every time you click it, "hi there, everyone!" is written to the calling environment. 

So, what should happen when I try to click the button "hello2"? I thought that everytime I clicked it, it should print the string "Hello.", but instead it prints the string "Hello." when the program is initiated, and doesn't print it when I actually click the second button.

If it's calling the command in self.test, then why isn't it calling the command in self.hi_there, and vice-versa.

Any ideas? 

thanks,
Mark

---

### Post by cwaldbieser on 2007-05-08
> **baltimark said:**
> So, I was sort of following along with an online tutorial, and is often the case, the first time I tried to branch out, I got behavior I didn't understand. 

```
# File: guitest.py

from Tkinter import *

class App:

    def __init__(self, master):

        frame = Frame(master)
        frame.pack()

        self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
        self.button.pack(side=LEFT)

        self.hi_there = Button(frame, text="Hello", command=self.say_hi)
        self.hi_there.pack(side=LEFT)

##baltimark's additions
        s = "Hello."
        self.test = Button(frame, text="Hello2", command=self.say_hello(s))
        self.test.pack(side=LEFT)

##original function defintion
    def say_hi(self):
        print "hi there, everyone!"

##baltimark's addition
    def say_hello(self, s):
        print s

root = Tk()

app = App(root)

root.mainloop()



```

run with 

>> python guitest.py

now, self.hi_there works just like you would expect. A button with "helllo" pops up and every time you click it, "hi there, everyone!" is written to the calling environment. 

So, what should happen when I try to click the button "hello2"? I thought that everytime I clicked it, it should print the string "Hello.", but instead it prints the string "Hello." when the program is initiated, and doesn't print it when I actually click the second button.

If it's calling the command in self.test, then why isn't it calling the command in self.hi_there, and vice-versa.

Any ideas? 

thanks,
Mark

For your "self.hi_there" button, the command is "self.say_hi".  self.say_hi is a name that refers to a function.
For your "self.test" button, the command is "self.say_hello(s)".  self.say_hello(s) calls a function that prints "hello" and returns None.  So your command evaluates to None.  That is why the program prints "hello" at the beginning, and then doesn't do anything when you press the button.

Try:
```

from Tkinter import *

class App:

    def __init__(self, master):

        frame = Frame(master)
        frame.pack()

        self.button = Button(frame, text="QUIT", fg="red", command=frame.quit)
        self.button.pack(side=LEFT)

        self.hi_there = Button(frame, text="Hello", command=self.say_hi)
        self.hi_there.pack(side=LEFT)

##new additions
        self.s = "Hello."
        self.test = Button(frame, text="Hello2", command=self.say_hello)
        self.test.pack(side=LEFT)

##original function defintion
    def say_hi(self):
        print "hi there, everyone!"

##new addition
    def say_hello(self):
        print self.s

root = Tk()

app = App(root)

root.mainloop()

```

In this example, "s" is a member variable.  The new button command is the method "say_hello".  The say_hello method prints the member variable, s.

---

### Post by baltimark on 2007-05-08
Oh. I getcha. 

I was completely missing that distinction between the function name, and actually calling the function. 

Thanks.

---

