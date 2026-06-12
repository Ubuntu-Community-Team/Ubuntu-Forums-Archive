---
title: "Linked Lists, merging and sorting"
date: 2010-04-09
forum: Programming Talk
---

### Post by bartre on 2010-04-09
Hi, i'm working on a program that will manipulate 2 linked lists.
i need to take the two lists, and do 4 things to them
find all values, with no duplicates (i.e. 1 2 3 + 3 4 = 1 2 3 4)
find all values present in both lists (i.e. 1 2 3  + 3 4  = 3)
find all values exclusive to the first list(i.e. 1 2 3 + 3 4 = 1 2)
find all values exclusive to the 2nd list( i.e. 1 2 3  + 3 4 = 4)

the problem is, i don't know how to combine the two lists, either while keeping organization, or reorganizing afterwards.
as of right now, i used the .addAll() method to add all values from the linked lists to a new linked list, unfortunately, it doesn't sort or check for duplicates.

can anyone help me with this?

EDIT:
forgot, i'm using java for this program

---

### Post by MadCow108 on 2010-04-09
which language?

the operations you are looking for are:
1. splice or merge
2. intersection
3. and 4. difference (3+4 = symmetric difference)

maybe that helps searching

edit sorry don't know java to well :/

---

### Post by bartre on 2010-04-09
well, i figured out how to sort em.
but now i've got one last problem.
i need to remove duplicates.
my idea at the moment is to use an iterator, and read the value stored at each location, and check if the indexOf() and lastIndexOf() methods return the same value, and if not, remove lastIndexOf() and check again.
does anyone know how to check the value at each loacation?

---

### Post by jon zendatta on 2010-04-10
Is it possible to use Unix sort & uniq commands? 
something like:
```
sort file | uniq
```

---

### Post by ja660k on 2010-04-10
not like many languages java has a brilliant API
[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

search for LinkedList
itll give you all kinds of methods.

doing the req where you have to get common values out, would look something like
psuedocode
```

results[]
k = 0

for i in list1 {
    val = list1.get i 
    for j in list2 {
        if val equals list2.get j {
            results[k] = list2.get j {
            k ++
        }
    }
}
print results[]

```
obviously there is better ways of doing this. what this is doing is saying check each element in list b against the first in list a, then again for the second in list a 

... mega inefficient
if listA has 5 elements and B has 9
it will loop 5^9 times

okay for small files, i guess

---

### Post by CptPicard on 2010-04-10
Sounds like homework from data structures and algorithms 101.

Hint: Sorting is a powerful tool. A *lot* of key comparison algorithms are actually bounded by the time it takes to sort the keys, and if you do the sorting, you've solved a big part of the problem.

Common values can be found in linear time after both lists are sorted by just iterating over them in tandem; otherwise it is a quadratic algorithm.

---

### Post by Some Penguin on 2010-04-10
Oh, it definitely sounds like homework.

*shrug*  It's trivial if you don't need to preserve the original ordering, to do each of those tasks in linear time.  You just use a much more appropriate structure than linked lists and it'll do all the work for you.

You don't specify if you need to preserve the original ordering, or for that matter, the original quantity -- if one list has the same value multiple times, do you need to preserve that?

---

### Post by CptPicard on 2010-04-11
> **Some Penguin said:**
> You just use a much more appropriate structure than linked lists and it'll do all the work for you.


Or, just simply sort the list. No need to change data structures. Of course, ordering is the underlying issue there as well...

---

