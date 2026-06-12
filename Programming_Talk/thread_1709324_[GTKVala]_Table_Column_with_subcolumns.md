---
title: "[GTK/Vala] Table Column with subcolumns"
date: 2011-03-18
forum: Programming Talk
---

### Post by arvigeus on 2011-03-18
I'm trying to achieve this:
[img]http://lh4.ggpht.com/_nHEt80wjI5c/TCR7f24sjgI/AAAAAAAABZw/VBEugB3gsTQ/template%20designer%20sub%20column%5B16%5D.jpg[/img]
The only thing I could think of was two tables stuck together, the one on top with no entries. Of course it looks ugly...

---

### Post by Tony Flury on 2011-03-18
Looks like the right combination of Vbox and HBox would do here with the right packing, and fill settings.

I have not done much GUI work but i can think of few places where a table is neccessary - unless you are actually laying out a table of data.

---

### Post by arvigeus on 2011-03-18
I already tried that, looks weird. I'm gonna need it because I'm gonna pull information from databese and need to display it in human readable format

---

