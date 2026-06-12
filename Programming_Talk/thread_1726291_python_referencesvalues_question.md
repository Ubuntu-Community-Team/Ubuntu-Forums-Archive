---
title: "python references/values question"
date: 2011-04-10
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-04-10
I was wondering how to stop python from making a reference to value of a list. For example, 

a = list1[0]
b = list1[4]

so then if I do

list1[0] = b
list1[4] = a

this doesn't switch the values, does it? to do that i reverted to something like:
list[0], list[4] = list[4], list[0]

I know that to make a new copy of a *list]* i do x = list[1][:]. Is there a way to do this for integers or values of a list?

---

### Post by DaithiF on 2011-04-11
> **flyingsliverfin said:**
> 
this doesn't switch the values, does it?
yes it does:

```
>>> list1= [ 10, 20, 30, 40, 50 ]
>>> a = list1[0]
>>> b = list1[4]
>>> list1[0] = b
>>> list1[4] = a
>>> list1
[50, 20, 30, 40, 10]

```

---

