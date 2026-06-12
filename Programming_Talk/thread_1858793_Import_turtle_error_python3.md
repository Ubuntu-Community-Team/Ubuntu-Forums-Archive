---
title: "Import turtle *error* python3"
date: 2011-10-13
forum: Programming Talk
---

### Post by TylerWen on 2011-10-13
yesterday when attempting to do some cs problems i was asked to import turtle (for the first time) when I entered import turtle it gave me the error in the screen shot.. however (also shown in the screenshot) import turtle works fine for python 2.7... just not for the one i need to use (python3.2.2)... someone please help me.

much appreciated,

Tyler


[[IMG]http://img269.imageshack.us/img269/5755/screenshotpfs.th.png[/IMG]]("http://imageshack.us/photo/my-images/269/screenshotpfs.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")[IMG]http://imageshack.us/photo/my-images/269/screenshotpfs.png/[/IMG]

---

### Post by MadCow108 on 2011-10-13
you local python3 installation does not include the tk extensions.
Did you compile it yourself?
if yes you probably mmissed seome build dependencies and it did not compile the extensions.
Check the output of the configure script for references to tk/tkinter

or install python3 from a correct package and use that.

---

