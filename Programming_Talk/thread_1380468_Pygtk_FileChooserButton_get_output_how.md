---
title: "Pygtk FileChooserButton get output how?"
date: 2010-01-13
forum: Programming Talk
---

### Post by J V on 2010-01-13
I need some simple code (very simple) to just get the value thats in the filechooserbutton, something like get_value would be perfect but it apparently doesn't exist, so how do I get the file location chosen?

On a side note, I need <releaseinfo> to show up in the help pages and for them to be indexed, how to?

---

### Post by diesch on 2010-01-13
gtk.FileChooserButton implements the gtk.FileChooser interface so you can use get_filename(), get_uri(), ...

---

### Post by J V on 2010-01-14
Thanks!

APGUI v 0.2! :P

---

