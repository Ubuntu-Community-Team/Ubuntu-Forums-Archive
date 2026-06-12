---
title: "PREFIX vs. DPREFIX"
date: 2009-04-05
forum: Packaging and Compiling Programs
---

### Post by toopi on 2009-04-05
Edit:  Sorry.  Wrong forum.  Please move to "Programming Talk".

I've seen the usage of DPREFIX in the place of PREFIX when compiling programs.  However, I couldn't find the info stating their differences.  Are they interchangeable?

---

### Post by toopi on 2009-04-11
Nevermind.  I think I've found the answer.
```
 -DPREFIX 
```
is the same as
```
 -D -PREFIX 
```

That's why -DPREFIX doesn't exist in the man page lol.

---

