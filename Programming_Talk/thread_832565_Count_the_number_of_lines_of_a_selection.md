---
title: "Count the number of lines of a selection"
date: 2008-06-17
forum: Programming Talk
---

### Post by DBQ on 2008-06-17
Suppose I use the visual mode in vim and I select an N number of lines, is there some way I can make vi count the number of lines I selected?  Anything is appreciated.  Can this even be done in vi?

---

### Post by rzrgenesys187 on 2008-06-17
This isn't exacty what you were looking for but ```
:set number
``` will give you line numbers so you could get the number highlighted from this

---

### Post by DBQ on 2008-06-17
Yes, I am aware of this technique...was hoping there was something better...bu perhaps there is not...

---

### Post by ghostdog74 on 2008-06-17
how did you "select" the lines?

---

### Post by DBQ on 2008-06-17
In the visual mode in vim.  escape then v and then just use the cursor to highlight.

---

### Post by ghostdog74 on 2008-06-17
if you want to just see how many lines you selected, press "y". It will show how many lines yanked. think its good enough?

---

### Post by DBQ on 2008-06-17
Not a bad idea - however, a better is solution is welcome.  Thank You.

---

### Post by geirha on 2008-06-18
```
:set showcmd
```

---

