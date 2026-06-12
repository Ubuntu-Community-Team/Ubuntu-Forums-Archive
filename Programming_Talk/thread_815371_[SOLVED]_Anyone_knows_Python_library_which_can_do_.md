---
title: "[SOLVED] Anyone knows Python library which can do  HttpGet?   [ and couple of other t"
date: 2008-06-01
forum: Programming Talk
---

### Post by dempl_dempl on 2008-06-01
Dear folks,

 I've decided to give  Python a chance [ only to show that C++ is better  , just kidding :)  ]   , hence I've decided to do a small project in it , because that's the best way to become a good friend with any programming language . 

For that purpose I'll need this:

 (1) Some HTTP library  for Python.  I don't need  anything fancy , I only need Get command .

 (2) A string grid widget with progress bars,  like the one you can find in Adept Manager , or in Firefox download window.  
It doesn't matter for which GUI framework is built ( heh, I'm just starting the project :)  ) . I guess that it would be an advantage if ht  GUI would use  a "native" interface . 


I realize that I could find this with Yahoo in a few days, but I believe it's easier just to ask someone with experience :)  .


Cheers!

---

### Post by Can+~ on 2008-06-01
1. [FONT="Courier New"]httplib[/FONT] : [httplib GET / POST example](http://docs.python.org/lib/httplib-examples.html)

2. I didn't get what you want, something like the GTK ColView/TreeView?

---

### Post by dempl_dempl on 2008-06-01
(1)Thanks. 

(2)Nope, a (table, StringGrid ) grid, which can , instead of text, display a progress bar in some of it's cells. You know, I would like to show progress for multiple downloads. You can see that in Opera , Firefox , and AdeptManager.

Anyway , I've just realized that I can use the gtk.Table() thingie, so nevermind the second question :)  .

---

### Post by kknd on 2008-06-01
> **dempl_dempl said:**
> 

(2)Nope, a (table, StringGrid ) grid, which can , instead of text, display a progress bar in some of it's cells.

GtkTreeView can do that.

---

### Post by dempl_dempl on 2008-06-01
Thanks, I'll look into it.

---

### Post by Can+~ on 2008-06-01
It's kinda hard making a treeview in GTK, I'll upload a sort of template I made. (Comes with the .py and a window made with glade3).

---

