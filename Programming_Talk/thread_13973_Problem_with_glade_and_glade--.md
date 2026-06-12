---
title: "Problem with glade and glade--"
date: 2005-02-03
forum: Programming Talk
---

### Post by nburns on 2005-02-03
I'm trying to use glade to build a couple of small windows, and I'm getting an error when I try to build the c++ code.  The error says something along the lines of "error running glade--"

I installed gtkmm and libglademm.  I don't seem to have glade-- installed though.  Which package pulls this in?

Any ideas?

---

### Post by az on 2005-02-04
Do you have libglade2-dev? (glade-gnome-2)










Carbs rock!

---

### Post by Roptaty on 2005-02-04
Try installing "glademm".

---

### Post by nburns on 2005-02-04
I installed the following:
glade-common-2
glade-gnome-2
libglade2-0
libglade2-dev
libglademm2.0-1c102
libglademm2.0-dev

---

### Post by nburns on 2005-02-04
Well.. I guess it helps if you actually install glademm and not the lib's for it.  I didn't see it in the repositories so it didn't get installed.

After downloading / compiling / installing everything seems to be working.

---

### Post by murrayc on 2005-05-15
> Well.. I guess it helps if you actually install glademm and not the lib's for it.

libglademm has nothing to do with glademm. And generating source code is usually not what you want.

---

