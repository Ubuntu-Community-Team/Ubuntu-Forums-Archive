---
title: "Python Tkintel Button widget"
date: 2009-05-19
forum: Programming Talk
---

### Post by SkyPlooM on 2009-05-19
Hi, 
I'm trying to program a python mini applet which I want it does something like this:

2, 3, 4...n buttons depending on the options.
When pressed, writes its value.
Well, I always have printed the last value from the array.
Here is the code:
```

from Tkinter import *

def writing():
    print a
    
root = Tk()
cont = 0
texto=["a","b","c","d"]
for a in texto:
     cont = cont + 1 
     elemento = Button(root, text=a, command=writing, justify=LEFT, width=25)
     elemento.grid (row=cont, column=1, sticky=W)
  
root.mainloop()

```The problem is I don't know how to associate the a value each time to the button and send it to writing.

Thanks and Cheers

---

### Post by unutbu on 2009-05-19
You could move the def of writing into the loop:
[PHP]for a in texto:
     def writing(astr=a):
# 	 When you give astr a default value, the default value a is evaluated
# 	 at the time writing is *defined*, not when writing is *called*.
# 	 Thus variable a saves the right value each time through the loop
         print astr
     cont = cont + 1 
     elemento = Button(root, text=a, command=writing, justify=LEFT, width=25)
[/PHP]

---

### Post by SkyPlooM on 2009-05-19
Working perfectly, thanks a lot

---

