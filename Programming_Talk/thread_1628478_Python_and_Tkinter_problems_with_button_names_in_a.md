---
title: "Python and Tkinter: problems with button names in a list."
date: 2010-11-22
forum: Programming Talk
---

### Post by vmsda on 2010-11-22
Hi, gurus:

I am trying to write a small program, where the number of buttons to be framed is a function of user input. So I build the buttons and keep them referenced in a list. When I want to remove some of the buttons from the frame, I go to the list to get their names. The problem is that I am getting an AttributeError when trying to destroy selected buttons, and am having difficulty seeing where I have gone wrong.

Below you will find the code and thanks in advance for the help.

PS By the way, I am using Python3.1

```
from tkinter import *

class L1(Frame):
    def __init__(self, boss = None):
        Frame.__init__(self)
        self.master.title("O Português da Nônô")
        self.blist = []                    # list to memorize button names
        self.oldname = ''
        Label(self, text = "Word :", width = 8).grid(row = 0, column = 0)
        self.entname = Entry(self, width = 15, bg = 'white')
        self.entname.grid(row = 0, column = 1, padx = 5, pady = 5)
        Button(self, text = 'Start', width = 10, command = self.draw).\
                   grid(row = 0, column = 2)

    def draw(self):
        self.name = self.entname.get()   # keep word entered by user
        r, c = 1, 0
        for letter in self.name:         # now build the list
            self.blist.append(Button(self, command = self.check,
                           text = letter).grid(row = r, column = c))
            if c == 2:
                r = r + 1
                c = 0
            else:
                c = c + 1
        n = len(self.oldname) - len(self.name)  # previous longer than actual?
        if n > 0:
            for number in list(range(0, n)):
                self.blist[-1].destroy()   # remove widget from window
                self.blist.pop()           # remove widget name from list
        self.oldname = self.name           # remember last word entered
       self.blist = []                    # reset the button list

    def check(self):
        pass

if __name__ == '__main__':
    wnd = Tk()
    L1(wnd).pack()
    wnd.mainloop()


```

---

