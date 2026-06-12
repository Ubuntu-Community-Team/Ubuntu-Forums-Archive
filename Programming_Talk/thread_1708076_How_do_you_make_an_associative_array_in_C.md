---
title: "How do you make an associative array in C?"
date: 2011-03-16
forum: Programming Talk
---

### Post by Pithikos on 2011-03-16
I know the theory: "Hash the value you want to store and use the hash-th place in the array to store it".

That gives me some problems though. I have a hash function that hashes any string to a number between 1 and 20,158,268,676. So for example:

```
"Athens" -> 8407130567
"Sparta" -> 597153027
```Now if I follow the theory I would need an array of size at least 8407130567 to save my values. Then I would save with:

```
array[8407130567]="Athens"
array[597153027]="Sparta"
```That ofcourse is not practical as it needs an enormous array. So how do we implement this? Is there some flaw in my thinking?

---

### Post by LemursDontExist on 2011-03-16
While in theory it would be best to have an array as large as your space of all possible hashes, generally you choose a fixed length for the hash array, then map the hashes to indices in the array, and deal with collisions if they happen.  

So, one possible approach is to choose the array to be of size s, take all your hash values modulo s so that the index is in range, then instead of storing just the values, store a linked list of pointers to key-value pairs, and when you want to do a lookup, first lookup by hash key, and then compare the looked up keys to your key until you get a match.

Obviously, the larger s is, the less often you'll have collisions, which will speed up lookup times, but cost memory.

For more info, check out the [wiki page]("http://en.wikipedia.org/wiki/Hash_table#Collision_resolution").

---

### Post by Tony Flury on 2011-03-16
why not have a binary tree or your hash's ? Relatively cheap to search and insert, and is as sparesley populated as you need it to be.

---

### Post by Pithikos on 2011-03-16
> **Tony Flury said:**
> why not have a binary tree or your hash's ? Relatively cheap to search and insert, and is as sparesley populated as you need it to be.

Well I never implemented a binary tree before so I am unsure if I will manage. Should it be implemented as a linked list where each node points to 2 other nodes?

---

### Post by DuneSoldier on 2011-03-16
I'd probably just use a map, with the hash being a key.

[http://en.wikipedia.org/wiki/Std::map](http://en.wikipedia.org/wiki/Std::map))

*Whoops didn't realize this was for C and not C++.

---

### Post by ziekfiguur on 2011-03-16
> **DuneSoldier said:**
> I'd probably just use a map, with the hash being a key.
The question was about C, not C++

I agree with Tony, a binary tree would probably be best. 
For a simple tutorial on how to implement one, se here [http://www.ehow.com/how_2056293_create-binary-tree-c.html]("http://www.ehow.com/how_2056293_create-binary-tree-c.html")

---

### Post by AlGorism on 2011-03-16
```
array[8407130567]="Athens"
array[597153027]="Sparta"
```

With this algorithm, you'll need an array with the size 20,158,268,676 for the worst case. So, it'd be really ridiculous. Try binary tree.

---

### Post by Some Penguin on 2011-03-17
> **Pithikos said:**
> That ofcourse is not practical as it needs an enormous array. So how do we implement this? Is there some flaw in my thinking?

Yes.  Choose your hash size; let each space in the hash array be a pointer to a linked list (either the values themselves, if equality testing is slow pair of hash and value, if equality testing is expensive, since comparing hash values is a faster first pass); and simply do the obvious modulo arithmetic.

---

### Post by johnl on 2011-03-17
> **Pithikos said:**
> 
```
array[8407130567]="Athens"
array[597153027]="Sparta"
```That ofcourse is not practical as it needs an enormous array. So how do we implement this? Is there some flaw in my thinking?

Choose your array size first, and perform all hash calculations modulo array_size.

When the number of items in your hashtable reaches a certain limit (75% is a common percentage), you grow your hashtable (usually by creating a new larger hash table, re-hashing all the elements in your original into the new, and then discarding the old).  Similarly, when the load in your table drops below a certain percentage (e.g 25%), shrink the hashtable in a similar manner.

---

### Post by MadCow108 on 2011-03-18
> **johnl said:**
> Choose your array size first, and perform all hash calculations modulo array_size.

When the number of items in your hashtable reaches a certain limit (75% is a common percentage), you grow your hashtable (usually by creating a new larger hash table, re-hashing all the elements in your original into the new, and then discarding the old).  Similarly, when the load in your table drops below a certain percentage (e.g 25%), shrink the hashtable in a similar manner.

you forgot to mention the most important part of this method: collision handling

here are a few implementations you could use (along with a detailed description of the container):
[http://en.wikipedia.org/wiki/Hash_table#Implementations](http://en.wikipedia.org/wiki/Hash_table#Implementations)

---

