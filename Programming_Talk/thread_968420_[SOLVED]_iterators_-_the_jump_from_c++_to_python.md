---
title: "[SOLVED] iterators - the jump from c++ to python"
date: 2008-11-02
forum: Programming Talk
---

### Post by glok_twen on 2008-11-02
hi. i am writing a simple loop through a list in python. i'd like to conduct some processing on each element. and, in doing so, i need to reference other elements in the collection. in c++ i'd have used a vector and passed around an iterator, then used iterator arithmetic to reference the other members of the vector.

doing this same thing in python seems to be different. here is the code:

```
for aThing in thingList:
    if (check(aThing)==true):
        print "true for: "+aThing.tostring()
```

the trick is that when i perform the check function, i need to reference other elements in the list. how is this done in python (in a way that is not a memory hog, eg that might mean passing the thingList by value)?

---

### Post by CptPicard on 2008-11-02
> **glok_twen said:**
> 
the trick is that when i perform the check function, i need to reference other elements in the list. how is this done in python (in a way that is not a memory hog, eg that might mean passing the thingList by value)?

Forget C++ semantics and just pass the list, in Python everything is passed "by reference" :)

---

### Post by snova on 2008-11-02
Reference counting ensures this already. As long as the function doesn't modify the list, you should be able to pass it without using any more memory than it takes to store a pointer (and a few other things).

If you had to modify it, put the list in a class and pass the object around. Objects are always passed by reference (I think).

Edit: CptPicard beat me to it. :)

---

### Post by CptPicard on 2008-11-02
snova, what are you talking about? :)

```

>>> mylist = [1, 2, 3]
>>> def modlist(aList):
...     aList[0] = "Foo"
...
>>> modlist(mylist)
>>> print mylist
['Foo', 2, 3]

```

One really needs to just think in terms of "bindings" in Python. First, mylist is bound to a new list object. Then we pass this list to the function modlist, where name aList is bound to the *same* object. Then we alter the list, and as mylist still refers to the one and only list, we see the changes.

---

### Post by snova on 2008-11-02
I wasn't completely sure whether lists were always passed by reference. Now I am.

---

