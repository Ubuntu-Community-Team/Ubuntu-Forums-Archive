---
title: "Anjuta problem"
date: 2007-06-06
forum: Programming Talk
---

### Post by Thinh on 2007-06-06
I am using the Anjuta, i had some background in C++ but have been away for some time now.
I install feisty and anjuta that comes with automatix2 for some reason i cannot compile the hello world  code follow the wizard. i know the code is correct because i tested on netbeans.  I get error message saying cannot find gnome-config and also sometime i get the error message saying need glib and i try looking for it and end up not know which one to pick there no file software that has that name. Any help would cool, newbie guy

thinh

---

### Post by Eviltelm on 2007-06-07
Try this:

```
$ sudo apt-get install build-essential
```

---

### Post by PointSource on 2007-06-07
I think that the phrase glib refers to libglib2.0, search for that using your package manager. It wouldn't hurt to install all the packages that search finds. Also, Anjuta likes to have the packages automake and autoconf, not included with build-essential I don't think.

---

