---
title: "[SOLVED] python Tkinter not displaying stdout"
date: 2008-12-30
forum: Programming Talk
---

### Post by TreeFinger on 2008-12-30
[php]
from Tkinter import *

class Checkers:
	def __init__(self, myParent):
		self.myContainer1 = Frame(myParent)
		self.myContainer1.pack()
	
		self.button1 = Button(self.myContainer1)
		self.button1["text"] = "Welcome to Checkers!"
		self.button1["background"] = "green"
		self.button1.pack()

root = Tk()
checkersgame = Checkers(root)
root.mainloop
[/php]

nothing being displayed..

---

### Post by Paul Miller on 2008-12-30
Change the last line to
```

root.mainloop()

```
Note the parentheses.

---

