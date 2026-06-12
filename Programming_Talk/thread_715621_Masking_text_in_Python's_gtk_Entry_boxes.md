---
title: "Masking text in Python's gtk Entry boxes"
date: 2008-03-05
forum: Programming Talk
---

### Post by aashay on 2008-03-05
I'm using an 'Entry' box to accept a password from the user. Is there a simple way to mask the password as it is being entered without affecting the result of the get_text function?

---

### Post by imdano on 2008-03-05
You can use set_visibility and set_invisible_char to do this.

See: [http://pygtk.org/docs/pygtk/class-gtkentry.html#method-gtkentry--set-visibility](http://pygtk.org/docs/pygtk/class-gtkentry.html#method-gtkentry--set-visibility)

---

### Post by aashay on 2008-03-05
Thanks.
I had added the set_invisible_char function but without the set_visible one, it wasn't doing anything.

---

