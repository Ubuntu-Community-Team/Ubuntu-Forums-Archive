---
title: "Pygtk treeview search"
date: 2009-10-18
forum: Programming Talk
---

### Post by poisonkiller on 2009-10-18
Hello!
I'm developing a program in python + gtk and I've hit a problem. Here's what I've got:
A GUI, treeview and entry (otherwise known as a textbox).
The treeview has a treemodel like this:
```

Parent1
-------Parent3
--------------Row1
--------------Row2
--------------Row3
Parent2
-------Parent4
--------------Parent6
---------------------Row5
-------Parent5
--------------Row4
```
My objective is to make a program, that filters the treeview according to the text entered in the entry.
For example, if I were to type "5" in the entry (without quotes), it would look like this:
```

Parent2
-------Parent4
--------------Parent6
---------------------Row5
```
Or if I typed "2":
```

Parent1
-------Parent3
--------------Row2
```
I've tried treefilter, but using it I can only make "Row"s invisible, not "Parent"s.
Any suggestions?

EDIT: Nevermind, figured it out.

---

