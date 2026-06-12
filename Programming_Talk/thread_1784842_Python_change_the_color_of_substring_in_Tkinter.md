---
title: "Python change the color of substring in Tkinter"
date: 2011-06-17
forum: Programming Talk
---

### Post by DBQ on 2011-06-17
Hi Everybody.

I am using tkinter in python. I have a listbox object.  Is there a way to set one part of the item to one color and the other part to another?

For example, the listbox contains a single item "Hello World".  Is there a way to make "Hello" one color and "World" the other?

Thank You!

---

### Post by cgroza on 2011-06-17
Check the class reference at:
[http://epydoc.sourceforge.net/stdlib/Tkinter.Listbox-class.html](http://epydoc.sourceforge.net/stdlib/Tkinter.Listbox-class.html)

Listbox.itemconfig() seems to be what you need...

---

### Post by DBQ on 2011-06-17
I think this method can only be used to change the color of the whole item, not a part of it.  Am I wrong?

---

### Post by juancarlospaco on 2011-06-17
Listbox.itemconfig(bg='black', fg='white')

---

### Post by DBQ on 2011-06-17
What I am trying to do is to change PART of the item's foreground color. Like if ONE item is "Hello World" I want "Hello" to be one color and "World" another.

---

### Post by cgroza on 2011-06-17
> **DBQ said:**
> What I am trying to do is to change PART of the item's foreground color. Like if ONE item is "Hello World" I want "Hello" to be one color and "World" another.
I think you will have to inherit and write your own widget to do that.

---

### Post by DBQ on 2011-06-17
What is the easiest way to achieve this? Can you give any tips.

Also, if there is another way to do it in Tkinter I would love to know.

Thank you!

---

### Post by juancarlospaco on 2011-06-17
You can, but not with Listbox, maybe Text

---

