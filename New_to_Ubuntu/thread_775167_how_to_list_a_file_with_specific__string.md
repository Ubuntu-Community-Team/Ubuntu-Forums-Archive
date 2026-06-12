---
title: "how to list a file with specific  string"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by born2003 on 2008-04-29
Hi 

I want to list a file with string "r" and "d" in the file name. I have tried the following command but it didn't work

ls [rd]*

Plz help

---

### Post by aheckler on 2008-04-29
in the directory try:

```
ls | egrep 'r|d'
```

---

### Post by Monicker on 2008-04-29
Is the order significant? Does the letters have to be right next to each other?

---

### Post by ashikahamed on 2008-04-29
Try 'grep' with 'ls'.
For example
ls | grep "[rd]"

---

### Post by Monicker on 2008-04-29
> **ashikahamed said:**
> Try 'grep' with 'ls'.
For example
ls | grep "[rd]"

[rd] can match if only one of the 2 letters is present.  I am not sure if he needs to match on both specifically, or just one of them.

---

