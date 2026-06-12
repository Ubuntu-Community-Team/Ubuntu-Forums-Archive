---
title: "how to search a two dimensional array"
date: 2009-07-29
forum: Programming Talk
---

### Post by mkrahmeh on 2009-07-29
hi
just wondering whether there is an efficient, non-trivial algorithm for searching a 2-d array, other than iterating through all elements..
its an integer array and unsorted.

i am surprised that googling around gave no answer but the trivial method 
```
for (int i = 0;..)
for (int j = 0;..)
if (arr[i][j] == val)
etc..
```:!:

---

### Post by Paul Miller on 2009-07-29
Unless you know something further about the elements of the array, there is no more efficient method of searching than simply iterating through every element.  Think about it: unless there's some relationship that the elements have to the subscripts that tells you you can stop searching early, every time you do this search, you may have to look at every element of your array.

---

### Post by giggins on 2009-07-29
If you're using an associative array, a [trie]("http://en.wikipedia.org/wiki/Trie") may be helpful. Pretty fast for dictionary type searches, like automatic word completion. But as previously suggested, without knowing more about the data being stored in the multi-dimensional array, its pretty difficult to suggest a better way of searching.

---

### Post by mkrahmeh on 2009-07-29
> **Paul Miller said:**
> Unless you know something further about the elements of the array, there is no more efficient method of searching than simply iterating through every element.  Think about it: unless there's some relationship that the elements have to the subscripts that tells you you can stop searching early, every time you do this search, you may have to look at every element of your array.

makes sense

however, i think its the same for one dimensional arrays, unless they are sorted, we cant do much other than the trivial iteration

just thought there might be a guru out there who has a magic answer :)

---

### Post by emustrangler on 2009-07-29
Well, to state the obvious, if your searching the same array many times, you could make a second sorted array to do the searching in and a second array that relates the indexes of the sorted array to the indexes of the non-sorted.

---

### Post by unknownPoster on 2009-07-29
If you're going to be doing multiple searches on this array, it might benefit you to also sort it on the first pass in order to increase the speed and efficiency of subsequent searches.

---

### Post by shel-hall on 2009-07-29
Like many programming problems of this type, "it depends."

If the data changes often and is completely unpredictable, the trivial, but slow, method you outlined is probably best.  It has the advantages of simplicity, reliability, and ease of maintenance, too.

If the data changes infrequently, it might be advantageous to keep a sorted version of the data in a single dimension, with additional, unsearched dimensions maintaining pointers to the original data.  It depends on the application as to whether the memory and time overhead is worth it.

-Shel

---

### Post by hyperAura on 2009-07-30
well said by shel-hall cant say anything more..:)

---

### Post by NovaAesa on 2009-07-30
Because it's an integer array, you can use radix sort to sort it initially (radix sort works in O(n)). All subsequent sorts, you can just use a modified binary search to search the 2D array (should be able to take O(log(n)) time).

---

### Post by dribeas on 2009-07-30
> **NovaAesa said:**
> Because it's an integer array, you can use radix sort to sort it initially (radix sort works in O(n)). All subsequent sorts, you can just use a modified binary search to search the 2D array (should be able to take O(log(n)) time).

Radix sort or any other sorting algorithm out there: quicksort (o introsort) that are usually available in libraries. The theoretical limit of radix sort hides the fact that there is a constant 'k' that represent the key size that must be at least 'log n' in size to hold all 'n' possible values. So while O(*k*n) sounds great, the fact is that 'k >= log n' and thus it does not beat the O(n log n) of mergesort (theoretical limits), and then again empirically quicksort/introsort are faster than that.

---

### Post by NovaAesa on 2009-07-31
> **dribeas said:**
> Radix sort or any other sorting algorithm out there: quicksort (o introsort) that are usually available in libraries. The theoretical limit of radix sort hides the fact that there is a constant 'k' that represent the key size that must be at least 'log n' in size to hold all 'n' possible values. So while O(*k*n) sounds great, the fact is that 'k >= log n' and thus it does not beat the O(n log n) of mergesort (theoretical limits), and then again empirically quicksort/introsort are faster than that.
Yeah, that is most likely the case. I have only been doing algorithmics (2nd year course at uni) for a few weeks now and we haven't gotten to the fine details yet.

---

