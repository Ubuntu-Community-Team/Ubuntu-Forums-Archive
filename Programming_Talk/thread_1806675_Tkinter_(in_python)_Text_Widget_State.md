---
title: "Tkinter (in python) Text Widget State"
date: 2011-07-18
forum: Programming Talk
---

### Post by DBQ on 2011-07-18
Hi everybody.

In Tkinter (python) text widget, is there a way to prevent the Text widget from being edited by the user, but allow the program to do inserts and deletes?

I know one way is to keep the widget disabled and then when I need to e.g. insert, I would briefly set the state to normal, insert, and then disable. However, this seems rather cheesy, because the user may get lucky and edit the thing in the moment of it being enabled.  Are there better ways?

---

### Post by juancarlospaco on 2011-07-18
Using the readonly property...   read here are all the answers to your questions, learned from there:
infohost.nmt.edu/tcc/help/pubs/tkinter.pdf

---

### Post by DBQ on 2011-07-19
The readonly option does not seem to be available for text widget.

---

### Post by juancarlospaco on 2011-07-19
Read the PDF; if you dont post any code, we cant help more than that...  &#664;&#8255;&#664;

---

### Post by DBQ on 2011-07-19
My code is very simple. I just want to be able to achieve the readonly effect on the tkinter text widget.

---

### Post by Bachstelze on 2011-07-19
> **DBQ said:**
> However, this seems rather cheesy, because the user may get lucky and edit the thing in the moment of it being enabled.

Actually no, they may not.

---

### Post by DBQ on 2011-07-19
Why not? Suppose they highlight some text and hold down the delete key. When the widget state is set to normal for a moment, the text may get deleted. Please elaborate if possible.  Thank You!

---

### Post by Bachstelze on 2011-07-19
> **DBQ said:**
> Why not? Suppose they highlight some text and hold down the delete key. When the widget state is set to normal for a moment, the text may get deleted. Please elaborate if possible.  Thank You!

Have you tried this? When a callback gets executed, the program stops responding to events until the callback returns. There is no other way to do what you want.

---

### Post by DBQ on 2011-07-20
I tried my experiment with holding down the delete key and sure enough the text was deleted.

---

