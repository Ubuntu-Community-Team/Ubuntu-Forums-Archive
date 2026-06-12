---
title: "Learning Python and tkinter"
date: 2007-06-08
forum: Programming Talk
---

### Post by FXFman1209 on 2007-06-08
Alright, well, I just bought a book that is helping me learn Python. Right now I'm at the tkinter tutorial and for some reason I can't figure out why this won't change the title of the box being made. The new window still has 'tk' as the title. Can someone help??

from Tkinter import *
from tkMessageBox import showinfo

def reply(name):
    showinfo(title='Reply', message='Hello %s!' % name)

top = Tk()
**top.title=('Echo')**

Label(top, text="Enter your name:").pack(side=TOP)
ent = Entry(top)
ent.pack(side=TOP)
btn = Button(top, text="Submit", command=(lambda: reply(ent.get())))
btn.pack(side=RIGHT)

top.mainloop()

---

### Post by WW on 2007-06-08
Change that line to
```

top.title('Echo')

```
(i.e. remove the =).

---

### Post by FXFman1209 on 2007-06-08
Ugh, I glanced right over that! Blah! Thanks so much!

---

