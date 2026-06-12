---
title: "Tkinter multiple file selection - somebody test please"
date: 2009-04-08
forum: Programming Talk
---

### Post by stevescripts on 2009-04-08
As a result of another thread, [http://ubuntuforums.org/showthread.php?t=1117679](http://ubuntuforums.org/showthread.php?t=1117679)
I am trying to figure out what might be
going wrong with my Python/Tkinter setup on my Gutsy box...

As this takes me about a minute in tcl/tk, I assumed it would be a pretty quick hack in Python/Tkinter (which, it turns out to be, it is...;)

The following little snippet works as expected everywhere I can test it,
**except** here on my Gutsy box, which is where I was trying to develop it.

```

from Tkinter import *

import tkFileDialog



root = Tk()


root.title("Selected Files")


files = tkFileDialog.askopenfilename(parent = root, filetypes = [('JPEG', '*.jpg'), ('ICON', '*.ico'), ('GIF', '*.gif')], multiple = 1 )



for i in files:

    print i



lb = Listbox(root, width = 80, height = 10, background = 'white')

lb.pack()



for i in files:

	lb.insert(END, i)



root.mainloop()


```

So, am asking somebody else to take a minute to test it on a Gutsy install.

Thanks,

Steve
(PS: any insights on what might be broken re my Python/Tkinter install here are welcome ... after entirely too many hours, I remain clueless...)

---

### Post by stevescripts on 2009-04-09
duh ... bump ...

Am I the only one still running python/tkinter on Gutsy?
(I fear this *may* be the case... ;) )

I would also appreciate knowing that it runs correctly under
other systems. (tested, so far, on three win boxes, on SuSE,
and one Mac OSX)

TY,

Steve

---

