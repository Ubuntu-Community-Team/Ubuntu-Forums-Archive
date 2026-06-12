---
title: "PyGTK Entry and TreeView"
date: 2008-06-15
forum: Programming Talk
---

### Post by EXCiD3 on 2008-06-15
So I'm working on a pygtk project currently and have a Search box that I would like to implement a Clear button inside, just like Compiz Config Settings Manager does or various other programs. How do i go about doing this?

Another question is on the TreeView...ive got it adding entries to the treeview model and would like to have it sorted by the 2nd column by default (which I have working fine currently) but I would also like to use the Search text to filter through all of the items. How do I implement both the PyGTK sort and filter together? Plus when I am loading the items from their files I need to load it into a regular model then a sorted model so that appending each item doesnt cause it to resort every time. I have tried searching online and have read through the Pygtk tutorials however all this seems to be over my head...:(

Any help would be greatly appreciated, especially a simple tutorial that could cover both like the source from a program or something. I've been reading through Deluge's source and learning quite a bit from it. Best way I can learn is by example since the documentation is always very technical.

**EDIT:** One other question, some of the text has invalid characters for the default language im using causing a Pango warning, is there any way I can strip these characters or convert them so that I wont be getting the error anymore?

---

### Post by EXCiD3 on 2008-06-18
bump :)

---

### Post by days_of_ruin on 2008-06-18
Did you read the tutorial from the pygtk website.
Also I think the reference manual might of talked about that.

---

### Post by EXCiD3 on 2008-06-18
I have read through it, but being new to python itself and never done GUI programming before, the documentation was well over my head. I download a the official tutorial for the treeview filter method and am still having trouble understanding it. I will keep trying maybe it will just click. If you can think of any applications written in PyGTK that I could read through the source that would be great. I know the deskbar-applet in gnome is in PyGTK and i think it has filtering, i havent had the chance to read through the source on it yet, but hopefully it will be insightful.

---

### Post by days_of_ruin on 2008-06-18
[http://pygtk.org/applications.html]("http://pygtk.org/applications.html")
Here is a big list:D

---

### Post by EXCiD3 on 2008-06-18
Found that just before you mentioned it. ;) You wouldnt happen to know how to add a button inside an entry box would you? like the search box in Exaile or Compiz Config for example

---

### Post by days_of_ruin on 2008-06-18
```
apt-get source compizconfig-settings-manager
```
It will be in c gtk which isn't oo but that will probably be the best
way to find out how to do it:D

---

### Post by days_of_ruin on 2008-06-18
Just finished downloading it and its written in python.
So that should make it easy to find out how.

---

### Post by EXCiD3 on 2008-06-18
I was thinking it was written in python, do you know if they use glade files or if the interface is done in the python files by chance?

---

### Post by days_of_ruin on 2008-06-18
No glade files.Just download it.

---

### Post by EXCiD3 on 2008-06-18
On dialup at the moment, ill be sure to download it tomorrow at work ;)

---

### Post by days_of_ruin on 2008-06-18
> **EXCiD3 said:**
> On dialup at the moment, ill be sure to download it tomorrow at work ;)

lol so am I.It really isn't very big.

---

### Post by days_of_ruin on 2008-09-15
```
import sexy
entry = sexy.IconEntry()
```

---

