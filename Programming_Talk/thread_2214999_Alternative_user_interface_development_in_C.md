---
title: "Alternative user interface development in C"
date: 2014-04-04
forum: Programming Talk
---

### Post by dargaud2 on 2014-04-04
Hello all,
I've been programming user interfaces for decades using a proprietary system (LabWindows/CVI), which is compatible with Linux but difficult to distribute. I've long wanted to learn some native open-source Linux user interface development, but:
- I've tried QT tutorials and I've a hard time groking it. Its philosophy is alien to me. Also I'd strongly prefer to use C, but QT is C++ only, adding to the confusion.
- I don't fancy using GTK apps, so I'd rather avoid that too !

My question is what alternatives are there ? I've read about some 'meta user interfaces' that compile to whatever the system has (QT, GTK, Windows, Mac...) but I don't remember the names offhand. I guess some are even available in multiple languages, including scripts, which would be good.

Suggestions ?

---

### Post by EddyDreizehn on 2014-04-04
Hi ... 

I believe, best, fastest and simplest way to write GUI in linux is with Python Tkinter. Its the default GUI, so you can use this fore windows too. 
For C development exists "ncurses" - a simple text based UI for console. But if you write this as a bash script, you are faster. In bash is "ncurses" named as "dialog". 

I hope, its helpfull... 

:guitar:

---

### Post by dargaud2 on 2014-04-04
Thanks. I've been reading about GUI, in particular [here]("https://en.wikipedia.org/wiki/List_of_widget_toolkits") and it looks like for C the options are GTK+, LessTiff (truly ancient) and IUP (never heard of it).

---

