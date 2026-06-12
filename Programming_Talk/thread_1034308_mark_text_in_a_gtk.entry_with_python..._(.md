---
title: "mark text in a gtk.entry with python... :("
date: 2009-01-08
forum: Programming Talk
---

### Post by smif1984 on 2009-01-08
Hi all, 
i've got a gtk.entry widget and i would like to set a different color just  for a part of the text entered. For example i may want to highlight ( bold text or change color) all text before the cursor position. How can i do this in Python

---

### Post by giuspen on 2009-01-08
What you need is pango:

[http://www.pygtk.org/docs/pygtk/pango-markup-language.html]("http://www.pygtk.org/docs/pygtk/pango-markup-language.html")

for an example in python look here:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

Good programming.

---

### Post by smif1984 on 2009-01-08
That's fine, but  it seems that a gtk entry doesn't like so much pango markup..
i'm stuck.. Buon anno e grazie.. :)

---

### Post by giuspen on 2009-01-10
> **smif1984 said:**
> That's fine, but  it seems that a gtk entry doesn't like so much pango markup..
i'm stuck.. Buon anno e grazie.. :)

Buon anno to u! :)
Cheers.

---

