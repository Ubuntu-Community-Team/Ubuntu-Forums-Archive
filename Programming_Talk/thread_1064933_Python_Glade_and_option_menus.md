---
title: "Python Glade and option menus"
date: 2009-02-09
forum: Programming Talk
---

### Post by intel17 on 2009-02-09
I'm created a GUI application that uses Qtk, Python and Glade.  I have created the GUI in glade and loaded it up in python.  But what I want is to get the value of the option menu (drop down list) with the python code. 

I can do this with the entry box like this:

```
types = self.wTree.get_widget("entry1").get_text()
```

But how do I do this with an option menu, if I enter the name of the option menu in place of 'entry1' it won't work. 

Or is there a better/different way of getting values out of the GUI elements?
Thanks, 
Pete

---

