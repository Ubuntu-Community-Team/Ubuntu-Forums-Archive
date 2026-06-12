---
title: "python and glade multiple dialogs"
date: 2009-02-15
forum: Programming Talk
---

### Post by n0p on 2009-02-15
I am trying to write application with python and glade-3. But i have one problem, first i have made in glade 2 widgets(dialogs). One widget is mainwindow, and other is aboutdialog. In main window is only one button, and when we click that button, about dialog should appear. My problem is that i don't know how to open that dialog..

.glade, .xml and .py files are in attachment, thx in advance for help..

---

### Post by HydroModeler on 2009-02-15
I haven't had a chance to look at your code, but when I wrote my first few python/glade apps I found the these tutorials to be indispensable.

[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)

There are three tutorials that build off one another.  Hope that helps some.

---

### Post by n0p on 2009-02-15
that is tutorial for glade2, i have searched a lot for my problem, but i couldn't find answers.. i would like if someone could take a look at my code, and help me :D. thx in advance

---

### Post by bruce89 on 2009-02-15
The signal handlers defined in the GtkBuilder file aren't actually implemented.

I don't think autoconnect works in pygtk.

---

### Post by n0p on 2009-02-16
> **bruce89 said:**
> The signal handlers defined in the GtkBuilder file aren't actually implemented.

I don't think autoconnect works in pygtk.

It should be possible, because i did connect them, but there where a lot of problems i think that the problems where there because i didn't done it properly...

---

### Post by n0p on 2009-02-17
anybody? i really have to finish this project soon :D

---

### Post by HydroModeler on 2009-02-17
> **n0p said:**
> that is tutorial for glade2, i have searched a lot for my problem, but i couldn't find answers.. i would like if someone could take a look at my code, and help me :D. thx in advance

I realize that the tutorials are for glade2 but I used them with glade3 and they are not too much different.  The wine application that is shown in the tutorial brings up a dialog when the "add wine" button is clicked.  This is similar to what you are trying to do.

---

### Post by n0p on 2009-02-17
> **HydroModeler said:**
> I realize that the tutorials are for glade2 but I used them with glade3 and they are not too much different.  The wine application that is shown in the tutorial brings up a dialog when the "add wine" button is clicked.  This is similar to what you are trying to do.

I have tried with that example, and i got problem when i run gtk.dialog.run(), if you know how, can you create example for me, thx in advance,..

---

### Post by n0p on 2009-02-20
anybody?

---

### Post by n0p on 2009-02-24
plzzzz

---

