---
title: "Python -- Efficient Matching Algorithm"
date: 2010-12-29
forum: Programming Talk
---

### Post by llanitedave on 2010-12-29
I'm faced with a little puzzle on a project I have at the moment using Python 3.1:

I've got a large collection of objects, several thousand of them.  Each object is a member of the same class, and has the same list of attributes, but their values may vary independently from one another.

I need to create tuples of complimentary pairs from the collection.  Not every object will necessarily have a compliment, but I need to collect those that do.  The criteria for determining a complimentary match is not a problem, but performance in finding the matches might be.

Here's the idea I have so far:
0. Start with a list of objects.
1. Get attributes of first object.
4. Step through list, comparing each subsequent object.
5. If complimentary attributes exist, remove both objects from list.
6. Start over with next object.

A vague idea that I should use sets to determine whether an item has or has not already been matched is floating around in my head, but that would require looping through the same items every time before checking whether they are in the set.  Another alternative was to recreate the list each time with the removed items not present, but that seems a lot of overhead.
Is there an efficient way to do this that minimizes the amount of looping required?

---

### Post by schauerlich on 2010-12-29
Your solution is O(n^2) - for each item on the list, it must iterate through every remaining value on the list. If possible, you should use a python dictionary, with the keys being the attributes you're comparing, and the values a list of all of the complementary objects. Go through the list and append each item to the correct value of the dictionary. That way, you only go through the list once and do two lookups and one insertion/append per item, which I believe are all O(1).

```
class Foo:
    def __init__(self, n):
        self.n = n

    def __repr__(self):
        return str(self.n)

def main():
    l = [Foo(1), Foo(2), Foo(3), Foo(3), Foo(2), Foo(3), Foo(10)]
    d = {}

    for obj in l:
        if obj.n in d:
            d[obj.n].append(obj)
        else:
            d[obj.n] = [obj]

    print d

main()

# ==> {1: [1], 2: [2, 2], 3: [3, 3, 3], 10: [10]}

```

---

### Post by MadCow108 on 2010-12-29
same approach as schauerlich but slightly faster:
```

import collections
def dostuff(l):
  d = collections.defaultdict(list)
  for obj in l:
     d[obj.n].append(obj)
  return d

print dostuff([Foo(1), Foo(2), Foo(3), Foo(3), Foo(2), Foo(3), Foo(10)])

```

---

### Post by llanitedave on 2010-12-29
Thanks folks.  I knew there was an elegant way to do it, but my brain is not elegant.  This looks like the right direction to try.

---

