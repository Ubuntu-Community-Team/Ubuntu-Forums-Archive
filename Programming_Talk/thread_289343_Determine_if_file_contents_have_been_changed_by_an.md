---
title: "Determine if file contents have been changed by another program"
date: 2006-10-30
forum: Programming Talk
---

### Post by cwaldbieser on 2006-10-30
I have noticed how some editors have the ability to detect if another program modifies a file that is open in the editor (e.g. kate).

I am writing a program in python that will generate some files, and I would like the user to be able to launch an editor from the application to do some editing (I don't care what editor they use-- it will be configurable).  When they save changes to a file through their editor, I would like my app to be able to recognize that the file has changed and reload the relevant part(s).

Is polling the file timestamp the best way to do this?  Or is there some better technique?

Thanks.

---

### Post by yabbadabbadont on 2006-10-30
I don't have the specifics, but you should probably read up on gamin, fam, and inotify.

---

### Post by po0f on 2006-10-30
cwaldbieser,

Is [this](http://www.gnome.org/~veillard/gamin/) what you're looking for?  It also has [Python bindings](http://www.gnome.org/~veillard/gamin/python.html).

---

### Post by cwaldbieser on 2006-10-30
> **po0f said:**
> cwaldbieser,

Is [this](http://www.gnome.org/~veillard/gamin/) what you're looking for?  It also has [Python bindings](http://www.gnome.org/~veillard/gamin/python.html).

This looks like it could work.  Thanks.

---

### Post by cwaldbieser on 2006-10-30
> **yabbadabbadont said:**
> I don't have the specifics, but you should probably read up on gamin, fam, and inotify.

I will read up on these.  Thank you.

---

