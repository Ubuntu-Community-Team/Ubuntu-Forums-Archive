---
title: "Quickly encapsulate rather than inherit???"
date: 2009-11-05
forum: Programming Talk
---

### Post by ksadil on 2009-11-05
Just looking at the quickly wiki, could someone please elaborate on what the following statement means:

classes encapsulate windows and dialogs (rather than inherit) 

The  file seems to inherit from gtk.window rather than encapsulate in my testing, the following code was created by quickly:

class KaspWindow(gtk.Window):
    __gtype_name__ = "KaspWindow"

so I am a little confused.

Kim

---

