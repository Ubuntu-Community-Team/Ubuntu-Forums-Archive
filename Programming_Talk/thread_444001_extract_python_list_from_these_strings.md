---
title: "extract python list from these strings?"
date: 2007-05-14
forum: Programming Talk
---

### Post by loell on 2007-05-14
hi , 

 how do i extract these numbers as list in python?
 ie:

 12-10-20
  34-90-67
  56-38-41

 each line is a single list.

 thanks in advance :)

---

### Post by ghostdog74 on 2007-05-15
you can use split(). the result is a list. you can store the list as a variable where necessary
eg
```

>>> "12-10-20".split("-")
['12', '10', '20']
>>> 

```

---

### Post by loell on 2007-05-15
oh thanks, i didn't know about the split thing :)

---

