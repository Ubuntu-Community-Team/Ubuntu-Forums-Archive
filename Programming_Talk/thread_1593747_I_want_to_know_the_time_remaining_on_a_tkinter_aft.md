---
title: "I want to know the time remaining on a tkinter after method"
date: 2010-10-11
forum: Programming Talk
---

### Post by trikster_x on 2010-10-11
I have created a python/tkinter trivia game that uses after() to end a session, and I would like to be able to display the remaining time on after() at various points through out the session.  Is this possible?  Or am I going to have to create a separate countdown timer that is invoked simultaneously with after()?

Edit:  

I found a way to use an after() loop to count down a variable to zero and end the session.  Then it was just a matter of doing some mathemagics to make the variable behave as minutes and seconds.

```
#!/usr/bin/python
import Tkinter
import time

class App(Tkinter.Tk):
    def __init__(self,parent):
        Tkinter.Tk.__init__(self,parent)
        self.parent = parent
        self.initialize() 

    def initialize(self):#This is where the info for the main window starts.

        self.secv = Tkinter.StringVar()
        self.minv = Tkinter.StringVar()
        self.timerv = Tkinter.StringVar()
        self.timer = 300
        

        self.testlabel1 = Tkinter.Label(self, textvariable=self.timerv).grid(column=0, row=0, columnspan=2, sticky='W'+'E')
         
        if self.timer == 300:
            self.test()

    def test(self):
        self.m = self.timer/60
        self.s = self.timer%60
        self.secv.set(self.s)
        self.minv.set(self.m)
        self.timerv.set(self.minv.get() + 'm : ' + self.secv.get() + 's')
        kill = self.after(1000, self.test) 
        if self.timer == 0:
            self.after_cancel(kill)
        self.timer -= 1

        
    



if __name__ == "__main__":
    app = App(None)
    app.title('Study Night')
    app.geometry('+100+70')
    app.mainloop()
```

This is the basic gist of it if anyone is curious.

---

