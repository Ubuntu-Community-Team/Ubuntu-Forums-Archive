---
title: "PyGTK text"
date: 2006-07-04
forum: Programming Talk
---

### Post by Ubuntuud on 2006-07-04
Hi,
I'm working on a webpage generator. It wasn't graphical at first, but I started working on it. I found an excellent tutorial, but I don't know how to insert the most basic, text. How do you insert text like in the attached screenshot?

(The "Uw systeem is up-to-date" etc.)

---

### Post by Daverz on 2006-07-04
Is this the sort of thing that you are looking for?

[http://www.pygtk.org/pygtk2tutorial/sec-TextBuffers.html#id3121630](http://www.pygtk.org/pygtk2tutorial/sec-TextBuffers.html#id3121630)

---

### Post by Ubuntuud on 2006-07-04
I don't know actualy. Isn't there a normal widget to contain text? Text buffers are much to hard for my program, I think I'll use labels. Thanks anyway!

---

### Post by Daverz on 2006-07-04
Yeah, just plain labels should work fine for presenting text that's not editable.
You use also HTML-like markup in labels using either set_markup() or set_use_markup() and set_text().

[http://pygtk.org/pygtk2reference/pango-markup-language.html](http://pygtk.org/pygtk2reference/pango-markup-language.html)

---

### Post by Ubuntuud on 2006-07-04
OK. Thanks again!

---

