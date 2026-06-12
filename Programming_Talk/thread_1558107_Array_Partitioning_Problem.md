---
title: "Array Partitioning Problem"
date: 2010-08-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-21
I have an array of length n which I want to partition into segments.  The segment length and the number of partitions are unbounded (no fixed constraints).  However, I also have a weight function which returns the weight of a given segment and I want to maximize (or possibly minimize) the sum of weights of all the segments.  Anyone know how to find the optimal solution or good approximation to this problem?

---

### Post by NovaAesa on 2010-08-21
> **SNYP40A1 said:**
> I want to maximize (or possibly minimize) the sum of weights of all the segments.

Won't the sum of weights of all the segments be constant no matter the partitioning?

---

### Post by teryret on 2010-08-22
Doesn't have to be, for example, consider a weight function that heavily penalizes segments that contain exactly two prime numbers and heavily rewards segments that contain exactly 3.

Edit: Check out hillclimbing and variants, they'll almost certainly be your best bet on this project, genetic algorithms are nifty and all, but they're not better enough to justify violating the KISS principle.

---

### Post by SNYP40A1 on 2010-08-22
Yes, the weights will depend on the array members of each segment.  2D variants of this problem are called "Packaging and Tiling".  One paper mentioned that the 1D case can be easily handled with dynamic programming, but did not give a solution.  There's also a paper called "Efficient Array Partitioning", but they focus mostly on the 2D case and the 1D solution involves sorting the set n choose 2 which would be practically intractable for me.

---

### Post by Lootbox on 2010-08-22
This is indeed a dynamic programming question. Here's an algorithm in pseudo-code that'll solve it:

```
Input: arr (length n array, indices from 1 to n), fn (weight function)
Notation: define arr[a:b] as the sub-array from indices a to b, inclusive

Initialize array A, indices from 0 to n
Initialize set S, empty
A[0] := 0
For i = 1 to n:
[indent]For j = 0 to i-1:
[indent]Insert A[j] + fn(arr[j+1:i]) into S[/indent]
End for loop
A[i] := max(S)
Clear S[/indent]
End for loop.

A[n] contains the optimal weight.

```

This half of the algorithm gives you the numerical value of the optimal weight. You have to trace back over the list in order to determine the actual segmentation. If you'd like me to explain any of the pseudo-code, or detail the second half of the algorithm, let me know.

Dynamic programming is pretty awesome.

[edit] Note that this algorithm assumes you can't have segments of length 0 with a positive score. Of course, this is a perfectly valid assumption. Otherwise there would be no optimal score, since you could have an infinite number of empty segments.

---

