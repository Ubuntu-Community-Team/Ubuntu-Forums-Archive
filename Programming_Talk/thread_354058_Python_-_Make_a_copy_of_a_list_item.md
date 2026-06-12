---
title: "Python - Make a copy of a list item"
date: 2007-02-05
forum: Programming Talk
---

### Post by ironfistchamp on 2007-02-05
Hey all

Yeah it's me again. I got another question. I don't even know if this is possible, but I would have thought it would be. Anyway here goes.

I have a list of lists. I have a second empty list. If I do this:

```


emptyList.append(list_of_lists[1])

#and then

emptyList[0][0] = "THE NEW VALUE"


```

Then it ends up getting changed in both lists. This is what I want. I want to be able to change it in one and for it to stay the same in the original list. Is it possible to append a copy to the list?

If anyone could help me figure this out that would be great. 

Thanks

Ironfistchamp

EDIT:

Aha found the answer. Using the copy module I use the deepcopy() function to clone the variable.

---

