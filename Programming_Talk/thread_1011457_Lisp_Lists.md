---
title: "Lisp Lists"
date: 2008-12-14
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-12-14
how do you check if a variable is a list

---

### Post by Tuna-Fish on 2008-12-14
In what lisp?

---

### Post by Mr.Macdonald on 2008-12-14
Common Lisp

---

### Post by wtwood on 2008-12-14
The predicate **listp** returns **t** if its argument is the empty list or a *cons* and **nil** otherwise:
```
* (defvar *v2* (list 1))

*V2*
* (defvar *v1* 1)

*V1*
* (listp *v1*)

NIL
* (listp *v2*)

T
* (listp '())

T
*
```
The first two lines set the variables ***v1*** to the number 1 and the variable ***v2*** to a list containing one thing, the number 1.  The next two lines show that *v1* is not a list and *v2* is a list.  The last line shows that the empty list, written either **'()** or **nil**, is a list.

---

