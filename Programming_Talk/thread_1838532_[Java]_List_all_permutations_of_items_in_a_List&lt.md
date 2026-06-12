---
title: "[Java] List all permutations of items in a List&lt;T&gt;"
date: 2011-09-03
forum: Programming Talk
---

### Post by KdotJ on 2011-09-03
Hey all, 
First off, I think permutations is the correct term (maybe combinations). Anyways, the title of this thread explains what I'm after. However, I'm wanting to get all possibilities... I'll explain.... 

```

// list of 3 items
[1, 2, 3]

// all possibilities
1
1, 2
1, 3
1, 2, 3
1, 3, 2
2
2, 1
2, 3
2, 1, 3
2, 3, 1
3
3, 1
3, 2
3, 1, 2
3, 2, 1

```

I know that I could work it all out with a bunch of for loops, but I just wondered if anyone knew of a more convenient way to do this.

Thanks

---

### Post by ofnuts on 2011-09-03
Plenty of info there: [http://en.wikipedia.org/wiki/Permutation](http://en.wikipedia.org/wiki/Permutation)

---

### Post by PaulM1985 on 2011-09-04
I think the term you are looking for is permutations rather than combinations.  Combinations are subsets where the order doesn't matter, so from your example, {1, 3} and {3, 1} would be classed as two copies of the same combination.  In permutations, order does matter.

I am not fully aware of an standard way for doing exactly what you want.  When getting a permutation most example functions take two arguments, a list of items and the number of items in the permutations.

You could iterate from 1 to [length of list] and get a list of permutations at each iteration.

Paul

---

### Post by ofnuts on 2011-09-04
Recursive implementation. To obtain the permutations of a list:

- iterate elements
- for each element get the permutations of the list without that element (recursive call)
- the permutations for that element are these sub-permutations, prefixed by the element, plus the empty permutation (important!)

Python implementation, I moved some technical stuff to other functions to keep the basic algorithm clear.
```

#! /usr/bin/python
# -*- coding: iso-8859-15 -*-

# Make a copy of the list without the given element
def sublist(l,elt):
    s=list(l)
    s.remove(elt)
    return s

# Prefix list with element
def prefix(pref,l):
    r=[pref]
    r.extend(l)
    return r

def permutations(l):
    results=[]
    if l:
        for elt in l:
            subperms=permutations(sublist(l,elt))
            for sub in subperms:
                results.append(prefix(elt,sub))
    results.append([])
    print 'Permutations for %s: %s' % (l,results)
    return results

print '------------------------------'
p= permutations([1,2,3])
print '>>>>>'
print 'Count: %s' % len(p)
for e in p:
    print e

```Yields:
```

Count: 16
[1, 2, 3]
[1, 2]
[1, 3, 2]
[1, 3]
[1]
[2, 1, 3]
[2, 1]
[2, 3, 1]
[2, 3]
[2]
[3, 1, 2]
[3, 1]
[3, 2, 1]
[3, 2]
[3]
[]

```And yes, the empty list is a possible permutation... not difficult to remove from the final result if needed.

Algorithm is brute force and I don't dare checking its actual computational complexity :) And yes it relentlessly recomputes the same sub-permutations several times

---

### Post by KdotJ on 2011-09-04
Thanks for the help guys, and thanks for that python code, it helps me understand the process easier. Asfor the performance and efficiency, I'm not overly bothered as the maximum amount of elements I'll have will be 5. 

Thanks again

---

### Post by Shin_Gouki2501 on 2011-09-04
In Scala ( which runs on the JVM/ Java) see: [www.scala-lang.org](www.scala-lang.org)
you can do this for example:
scala> val l=List(1,2,3)

scala> l.permutations.foreach( println)
List(1, 2, 3)
List(1, 3, 2)
List(2, 1, 3)
List(2, 3, 1)
List(3, 1, 2)
List(3, 2, 1)

In Clojure a LISP running on the JVM you could do like this:
(defn all-permutations [things]
  (if (= 1 (count things))
    (list things)
    (for [head things
          tail (all-permutations (disj (set things) head))]
      (do
        (cons head tail)))))

(all-permutations '(1 2 3))
((1 2 3) (1 3 2) (2 1 3) (2 3 1) (3 1 2) (3 2 1))

---

