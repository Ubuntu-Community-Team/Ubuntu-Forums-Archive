---
title: "Python issue: appending lists to other lists creates unwanted references"
date: 2008-04-22
forum: Programming Talk
---

### Post by meanburrito920 on 2008-04-22
my code runs something like the following:


```

a_list = [0,0]
list_of = []
while True:
    #do something to a_list here
    list_of.append(l)


```

the problem is that since I am appending a_list to list_of, it thinks that every time a_list changes it should change all previous versions of a_list to the current value of a_list, so at the end of the loop list_of ends up being a list of 'a_list's that is x 'a_lists's long. I want it to forget the reference to l after it is appended and simply store the values, but I'm not exactly sure how to go about this. Any suggestions?

---

### Post by nanotube on 2008-04-22
> **meanburrito920 said:**
> my code runs something like the following:


```

l = [0,0]
list_of = []
while True:
    #do something to l here
    list_of.append(l)


```

the problem is that since I am appending l to list_of, it thinks that every time l changes it should change all previous versions of l to the current value of l, so at the end of the loop list_of ends up being a list of 'l's that is x 'l's long. I want it to forget the reference to l after it is appended and simply store the values, but I'm not exactly sure how to go about this. Any suggestions?

yea, for your last line, use
```
list_of.append(l[:])
```

edit: a bit of explanation: all objects in python are passed by reference; this includes lists. (even integers and strings, technically... but when you assign a new value, it creates a new object, that's why it looks like integers and strings are passed by value)
so what you need to do is create a deep copy of the object, if you want it to be stored as a copy. for a list, the syntax [:] means create a full slice of the list, so it's equivalent to using copy.deepcopy(l), but more concise.

---

### Post by meanburrito920 on 2008-04-22
thanks

---

