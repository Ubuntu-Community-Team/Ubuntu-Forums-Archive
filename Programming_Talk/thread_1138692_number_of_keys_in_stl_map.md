---
title: "number of keys in stl map"
date: 2009-04-26
forum: Programming Talk
---

### Post by monkeyking on 2009-04-26
this is a very basic question, but I really cant find the information.

How do I get the number of keys in a std::map in c++.

Not the value associated with a given key,
but the number of uniq keys.


Maybe I should use something else that a std::map if I just want to keep track of unique elements?


thanks in advance

---

### Post by Naddiseo on 2009-04-26
[http://www.cplusplus.com/reference/stl/map/size/](http://www.cplusplus.com/reference/stl/map/size/)

[http://www.cplusplus.com/reference/stl/map/count/](http://www.cplusplus.com/reference/stl/map/count/) 
"Because map containers do not allow for duplicate keys..."

---

### Post by monkeyking on 2009-04-26
Thanks but this is not what I'm looking for,

size gives you the number of elements in total,
count tells me how many elements with a given key.

What I want is the number of keys.

---

### Post by Namtabmai on 2009-04-26
A map provides a one-to-one mapping doesn't it? And with keys having to be unique, how would the number of elements differ from the number of values?

---

### Post by dwhitney67 on 2009-04-26
> **monkeyking said:**
> ...
size gives you the number of elements in total,
count tells me how many elements with a given key.
...

Yes, this is correct.  And the problem is?  The number of unique keys equals the size of the map.

Now, if you are using a multimap, then it is a different story.  I do not believe there is any easy way to discern how many keys are unique, other than my checking the count of each possible key to see if there is one or more entries associated with it.

---

