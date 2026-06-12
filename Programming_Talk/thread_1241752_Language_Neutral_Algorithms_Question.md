---
title: "Language Neutral Algorithms Question"
date: 2009-08-16
forum: Programming Talk
---

### Post by andrew222 on 2009-08-16
If we had an application and we are running low on memory and we needed to use a sorting algorithm and a searching algorithm,  which ones would be the best to use in this scenario?

---

### Post by Finalfantasykid on 2009-08-16
Some form of merge sort would probably be good since it's Space Complexity is O(n), and is pretty fast.

However if you are really really low on RAM, then you could potentially write a sorting algorithm that only looks at two elements at a time, the rest of the elements being inside of a file, which would be updated as the algorithm goes along.  This would be a very slow algorithm, but would use extremely small amounts of ram.

So if you are not concerned about how fast the algorithm works, then you might want to consider using your harddrive in place of ram.

---

### Post by Npl on 2009-08-16
space-complexity of O(n) is horrible!
heapsort is using O(1) and the venerable quicksort uses O(log(n)) if you recurse in the smaller branch first.

In fact, you can pretty much drop the O notation.
heapsort will only use space for a few loop-variables,
quicksort will need space for ld(N) (logarithm of base 2) Entries
mergesort needs space for N (or N/2 if you optimize it a bit) Entries.

---

### Post by jpkotta on 2009-08-16
Have a look at [mmap()]("http://en.wikipedia.org/wiki/Mmap").

---

### Post by soltanis on 2009-08-16
If your only concern is memory, you should consider doing a bubble sort, since it requires at most only enough memory to hold the list to be sorted, plus three extra placeholders (for comparison, then swapping).

Of course, bubble sort is incredibly slow and inefficient. Quicksort might also work out in this case (but will require a little more memory).

---

### Post by Lux Perpetua on 2009-08-17
> **soltanis said:**
> If your only concern is memory, you should consider doing a bubble sort, since it requires at most only enough memory to hold the list to be sorted, plus three extra placeholders (for comparison, then swapping).

Of course, bubble sort is incredibly slow and inefficient. Quicksort might also work out in this case (but will require a little more memory).Even if memory were so important that an O(n^2) algorithm might conceivably be preferable to a fast O(n*log(n)) algorithm for the sake of a few bytes, bubble sort would still only barely edge out heap sort. First of all, since the memory requirements for swapping and comparison depend on the type of the array being sorted and are going to be the same for all (comparison-based) sorting algorithms, let's ignore those. Then by my reckoning, bubble sort needs two local variables (loop counters) as opposed to three for heap sort. (There's a counter keeping track of how big the current heap is, and fixing the heap after an insertion or dequeueing takes a couple more pointers or indices for bookkeeping.)

More realistically, the vast speed superiority of heap sort over bubble sort would probably far outweigh those few bytes.

---

