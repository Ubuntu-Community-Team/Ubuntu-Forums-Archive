---
title: "display elements in a random order"
date: 2010-08-01
forum: Programming Talk
---

### Post by kartabosh on 2010-08-01
hi,
i was wondering if someone knows how to display all the elements in a structure / list / map whatever in a random order
i use c++

---

### Post by Jacobian on 2010-08-03
You might try sorting your data with a comparison function that randomly returns true or false.

Here are some functions that may be helpful:

sort:
[http://www.cplusplus.com/reference/algorithm/sort/](http://www.cplusplus.com/reference/algorithm/sort/)

rand:
[http://www.cplusplus.com/reference/clibrary/cstdlib/rand/](http://www.cplusplus.com/reference/clibrary/cstdlib/rand/)

Another approach might be to generate an index array. First, shuffle the index values until the array is sufficiently random, then retrieve your elements in the now-random order specified by the index array.

---

### Post by kartabosh on 2010-08-03
so far i have the algorithm that shuffles
returns 0 1 2 3 in a random order 
i have to somehow link those to the answers
i'm thinking something like an array that holds the question, answer and points for answer like a multidimentional array but i dont know how to do that yet

---

### Post by Arndt on 2010-08-04
> **Jacobian said:**
> You might try sorting your data with a comparison function that randomly returns true or false.



Note that some (many?) sorting function implementations expect the comparison function to be consistent. I know that qsort can be made to crash if the comparison function isn't consistent.

---

### Post by MadCow108 on 2010-08-04
no need to make your comparison do weird stuff, just use the shuffle algorithm:
[http://www.cplusplus.com/reference/algorithm/random_shuffle/](http://www.cplusplus.com/reference/algorithm/random_shuffle/)
of course that only works with random access iterators

for lists you'll have to do it yourself

and maps you cannot shuffle because the map is an sorted structure by definition.

But you for displaying you could just iterate to random positions (e.g. by making a vector of all iterators and shuffle that with the algorithm), this works for all containers

---

### Post by interval1066 on 2010-08-04
Copy your map and list elements to a vector and shuffle all you want.

---

