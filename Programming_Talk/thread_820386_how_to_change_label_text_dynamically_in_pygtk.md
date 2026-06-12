---
title: "how to change label text dynamically in pygtk"
date: 2008-06-06
forum: Programming Talk
---

### Post by brijith on 2008-06-06
hai,

I am a python programmer. I use pygtk for developing interfaces. What I want to Know is How to change the label text dynamically. I want to show a message like **Loading....** when program is busy with loading data from data base

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by WW on 2008-06-06
Use the [set_label](http://www.pygtk.org/docs/pygtk/class-gtkbutton.html#method-gtkbutton--set-label) method.


EDIT:

Whoops, I was thinking of the label in a [Button](http://www.pygtk.org/docs/pygtk/class-gtkbutton.html) when I made that link, but the [Label](http://www.pygtk.org/docs/pygtk/class-gtklabel.html) widget also has a [set_label](http://www.pygtk.org/docs/pygtk/class-gtklabel.html#method-gtklabel--set-label) method.

---

### Post by brijith on 2008-06-06
> **WW said:**
> Use the [set_label](http://www.pygtk.org/docs/pygtk/class-gtkbutton.html#method-gtkbutton--set-label) method.


EDIT:

Whoops, I was thinking of the label in a [Button](http://www.pygtk.org/docs/pygtk/class-gtkbutton.html) when I made that link, but the [Label](http://www.pygtk.org/docs/pygtk/class-gtklabel.html) widget also has a [set_label](http://www.pygtk.org/docs/pygtk/class-gtklabel.html#method-gtklabel--set-label) method.


I think You Didn't get my Question. I want to continuously change the text . while the program load some data from db.

---

### Post by Flimm on 2008-06-06
You want the set_text(text) function, or the set_label(text) function for text with markup. Just call it everytime you need to update the label.
Documentation is your friend:
[http://www.pygtk.org/docs/pygtk/class-gtklabel.html](http://www.pygtk.org/docs/pygtk/class-gtklabel.html)

---

### Post by brijith on 2008-06-07
> **Flimm said:**
> You want the set_text(text) function, or the set_label(text) function for text with markup. Just call it everytime you need to update the label.
Documentation is your friend:
[http://www.pygtk.org/docs/pygtk/class-gtklabel.html](http://www.pygtk.org/docs/pygtk/class-gtklabel.html)

I know How to set text to a label. I want to set it continuously while control is some where else ,say it is loading data from database. If I just use the *set text* it will set the text after loading the data.But I want to change it when program is busy with loading the data from database.

I want to set text LOADING then continuously put periods after it. Like LOADING.then LOADING.. then LOADING... and then LOADING.... etc

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by Flimm on 2008-06-07
How are you reading the data from the database?

---

### Post by brijith on 2008-06-07
> **Flimm said:**
> How are you reading the data from the database?

I use Pypgsql connect to postgresql.

---

### Post by smartbei on 2008-06-07
You could just use a separate thread that sleeps for a second, adds a period, and so on... Just create a new thread using the thread module, pass it the button instance, and have it continuously add periods.

---

### Post by loell on 2008-06-07
while data is loading call a method intervally through **gobject.timeout_add**

and in that method check if its still loading, of course youll gonna have to pass the gtk label object to change the text dynamically.

---

### Post by brijith on 2008-06-10
> **loell said:**
> while data is loading call a method intervally through **gobject.timeout_add**

and in that method check if its still loading, of course youll gonna have to pass the gtk label object to change the text dynamically.



Yes, thats What I am looking for. Can you give me simple example.. I mean code sample that uses **gobject.timeout_add**

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by loell on 2008-06-10
if you want a working example, look into pygtk's demo **dnd.py**

```
apt-get source python-gtk2  
``` 


in **pygtk-2.12.1/examples/pygtk-demo/demos**

---

