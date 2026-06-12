---
title: "Escape characters in variable"
date: 2009-07-01
forum: Programming Talk
---

### Post by wesg on 2009-07-01
I'm writing a bash script that retrieves data from the web in the form of webpage source code. The problem I seem to be having is that putting the text into a variable fails because of the many quotation marks, # signs and other programming marks that are inside the text.

How can I store this type of variable safely and continue to operate on it?

---

### Post by Yuzem on 2009-07-01
It should work, try this:
```
var=$(wget -U firefox -qO - google.com)
```
It works for me.

---

