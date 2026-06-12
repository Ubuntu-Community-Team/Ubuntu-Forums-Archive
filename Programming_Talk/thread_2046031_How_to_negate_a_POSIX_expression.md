---
title: "How to negate a POSIX expression?"
date: 2012-08-22
forum: Programming Talk
---

### Post by Paddy Landau on 2012-08-22
Suppose I want a POSIX ERE (Extended Regular Expression) to find all strings beginning with "gout". That's easy:
```
^gout
```But how do I negate this, to find all strings *not* starting with "gout"? I have been Googling for ages and I cannot find the answer.

---

### Post by cortman on 2012-08-22
I forget if this is POSIX compliant or not but

```
^[^gout]
```

Would do the trick.

EDIT: [It is]("http://www.boost.org/doc/libs/1_44_0/libs/regex/doc/html/boost_regex/syntax/basic_extended.html").

---

### Post by Paddy Landau on 2012-08-22
> **cortman said:**
> I forget if this is POSIX compliant or not but

```
^[^gout]
```Would do the trick.
No… That says that the *first* character may not be any of *g*, *o*, *u* or *t*. Thus, "bout" would be (correctly) allowed whereas "grab" would be (incorrectly) rejected.

---

### Post by diesch on 2012-08-22
There is no simple way to do this with POSIX ERE. One way would be

```
^([^g]|g[^o]|go[^u]|gou[^t])
```

---

### Post by ofnuts on 2012-08-22
> **diesch said:**
> There is no simple way to do this with POSIX ERE. One way would be

```
^([^g]|g[^o]|go[^u]|gou[^t])
```

This explains why grep has a -v option, and perl a  **"!~**" operator :)

---

