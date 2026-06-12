---
title: "Hash Tables and Collisions Question"
date: 2010-01-29
forum: Programming Talk
---

### Post by firefly2442 on 2010-01-29
I have a question about Hash Tables ([Quick Tutorial for those who forgot]("http://www.sparknotes.com/cs/searching/hashtables/section1.html")).

Let's say I want to hash all the files on my computers.  For example, let's say I have 1 million files.  Now I want to pick a hash algorithm and a size that makes it extremely unlikely that there is a collision ([Collision info on Wikipedia]("http://en.wikipedia.org/wiki/Hash_collision")).  The Wikipedia article states:

> When hash functions and fingerprints are used to identify similar data, such as homologous DNA sequences or similar audio files, the functions are designed so as to maximize the probability of collision between distinct but similar data. Checksums, on the other hand, are designed to minimize the probability of collisions between similar inputs, without regard for collisions between very different inputs.

In the case when I'm dealing with my files, does it matter what type of hash function I use? ([Different hash functions list on Wikipedia]("http://en.wikipedia.org/wiki/List_of_hash_functions"))  Obviously the length or size of the hash matters and the hash probably won't deliver a completely uniform distribution of hash values across the range right?

In terms of the probability of a collision I found two links that talk about it. ([First link]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/6330927813/m/821008399831"), [Second link is very good but long]("http://valerieaurora.org/monkey.html"))

Is file hashing really random?  I would imagine there might be a high amount of similarity between files which would increase the chance of a collision?

Any thoughts would be appreciated.  Thanks. :)

---

### Post by MadCow108 on 2010-01-29
that depends on whats in your files. I guess for a normal computer the files are rather random.
But the only way to know is to test it.
Read all your files and check the distribution or use different hashs and check the collisions.
But the results my be different at later time and on other computers.

Optimal hashing is a very complicated business, are you really sure its worth the time spent?
Otherwise just use a good all round function.

and if you need worst case performance, don't use hash tables but some kind of balanced tree.

---

