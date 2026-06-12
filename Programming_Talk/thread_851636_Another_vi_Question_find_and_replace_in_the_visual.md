---
title: "Another vi Question: find and replace in the visual selection"
date: 2008-07-06
forum: Programming Talk
---

### Post by DBQ on 2008-07-06
Hi everybody again.  I have another vi/vim question. Is there a way to visually select a block of code, and then do find/replace within the selection?  Having to find/specify line numbers every time gets annoying as well, and wastes time (esp. when you need to do things like this often).

Thank you all.

---

### Post by odyniec on 2008-07-07
Select the lines in visual mode, then enter :s/text/replacement/g

---

