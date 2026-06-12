---
title: "Python problems"
date: 2007-08-17
forum: Programming Talk
---

### Post by Ultra Magnus on 2007-08-17
Hi, I'm trying to learn python  - I'm just trying to write a little radio thing to play radio2 from the bbc website, eventually I want to have it as a screenlet type thing but I'm just starting out. Currently its just a button and a function (you press the button and the function executes) - but the problem is that when I execute the file in the terminal the command executes automatically. Any ideas?

This is the code:

```
from Tkinter import *
import os

def play_station():
	os.system('mplayer rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio2/live/r2_dsat_g2.ra?BBC-')

root = Tk()

Play = Button(root, text='Play', command = play_station())
Play.pack()

root.mainloop()
```

---

### Post by Bachstelze on 2007-08-17
Try this :

```

Play = Button(root, text='Play', command = play_station)

```

---

### Post by pmasiar on 2007-08-17
"from Tkinter import *" is very nasty bad habit, it might pollute your namespace with functions which names you might not know. Always use "from Tkinter import a, b c" .

Wiki in my sig has many training tasks suitable for Python learners, try them out.

Good luck!

---

### Post by Ultra Magnus on 2007-08-18
Awesome, thanks allot!

---

