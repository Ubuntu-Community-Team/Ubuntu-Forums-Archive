---
title: "[SOLVED] pygtk - directory chooser dialog???"
date: 2008-11-11
forum: Programming Talk
---

### Post by giuspen on 2008-11-11
at this link
[http://www.pygtk.org/pygtk2tutorial/sec-FileChoosers.html]("http://www.pygtk.org/pygtk2tutorial/sec-FileChoosers.html")
it's very well described how to implement a file chooser dialog.
i expected that there would be an option to select a folder instead than a file, like with zenity, but i found nothing.
anybody can help me to make a directory chooser dialog in pygtk?
(i already made it through zenity and the subprocess module but i would like to use pygtk)

---

### Post by unutbu on 2008-11-11
The gtk.FileSelection widget does what you need. See
[http://www.pygtk.org/pygtk2tutorial/sec-FileSelections.html#fileselfig](http://www.pygtk.org/pygtk2tutorial/sec-FileSelections.html#fileselfig)

---

### Post by Flimm on 2008-11-11
Here's the option you're looking for:
```
chooser.set_action(gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER)
```
Never forget the documentation, here's [the reference for FileChooser](http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html#method-gtkfilechooser--set-action).

---

### Post by giuspen on 2008-11-12
thanks a lot! :KS
giuseppe.

---

### Post by RockDoctor on 2009-12-03
> **Flimm said:**
> Here's the option you're looking for:
```
chooser.set_action(gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER)
```Never forget the documentation, here's [the reference for FileChooser]("http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html#method-gtkfilechooser--set-action").

Thank you. Just what I need, even if it is a year old!  :D

---

### Post by macabro22 on 2011-07-17
Cool! Just what I needed even if its n years old. Thanks a bunch!

---

