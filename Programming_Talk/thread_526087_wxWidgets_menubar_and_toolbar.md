---
title: "wxWidgets menubar and toolbar"
date: 2007-08-15
forum: Programming Talk
---

### Post by aquavitae on 2007-08-15
Does anyone know if theres a way to share menu and tool items in wxWidgets?  I have a lot of commands, and it seems very clumsy to have to type the text, icon description, etc twice for each one.

---

### Post by dscherry on 2007-08-15
You can store the text/command/icon stuff in a list (or lists if you prefer).  Then use loops to load the menu and tool widgets with the data from the list.

Dan

---

### Post by aquavitae on 2007-08-16
> **dscherry said:**
> You can store the text/command/icon stuff in a list (or lists if you prefer).  Then use loops to load the menu and tool widgets with the data from the list.

DanNot a bad idea, but I was wondering if there was anything like QAction in Qt.  I've recently switched from using Qt to wxWidgets (cos of the licence) and so far I wish I'd started earlier, but there are a few things I still prefer in Qt.  Maybe I should just write my own class to do it.  Also, is there any framework for editing toolbars, i.e. add/remove buttons for the user?

---

