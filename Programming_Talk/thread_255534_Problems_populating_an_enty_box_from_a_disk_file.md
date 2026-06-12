---
title: "Problems populating an enty box from a disk file"
date: 2006-09-11
forum: Programming Talk
---

### Post by theDentist on 2006-09-11
Can anyone help me,  I'm trying to fill an entry box with text from a disk file.  No matter what I use, fgets(), fgetc() or fscanf(), I always have the same problem.  It works perfectly up to 16 characters but if the string is more, I get the following error message in the terminal:

(files:5311): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

Any ideas
Peter
          :(

---

### Post by scto on 2006-09-11
hi,

there a function to convert strings do utf8.
in c++ like so:
label->set_text(Glib::locale_to_utf8(output.str()));

regards
scto

---

### Post by scto on 2006-09-11
and here's the link if you program in c

[http://www.gtk.org/api/2.6/glib/glib-Character-Set-Conversion.html](http://www.gtk.org/api/2.6/glib/glib-Character-Set-Conversion.html)

regards
tom

---

### Post by theDentist on 2006-09-12
Thanks for the advice        :) 

Peter

---

