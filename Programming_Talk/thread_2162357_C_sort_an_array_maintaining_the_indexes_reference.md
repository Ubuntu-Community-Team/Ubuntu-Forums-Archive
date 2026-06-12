---
title: "C: sort an array maintaining the indexes reference"
date: 2013-07-14
forum: Programming Talk
---

### Post by erotavlas on 2013-07-14
Hi,

suppose I have three arrays a1, a2 and a3 of the same size in which the elements are linked. The link means that if an element in the first array a1 changes position then also the corresponding elements in the other arrays a2, a3 change position. If an element of the second array a2 changes position then only the corresponding element of the array a3 changes position. 
For instance
a1 a2 a3 
0   1   2
1   1   3
1   0   4
0   2   5

first step
a1 a2 a3 
0   1   2
0   2   5
1   1   3
1   0   4

second step
a1 a2 a3 
0   1   2
0   2   5
1   0   4
1   1   3

In fact I have to sort both the first two arrays in consecutive order. First, I sort the array a1 and then I reorder the elements of the second array a2 and third array a3. Then, I sort the array a2 and I reorder the elements of the third array.
If I use the standard quick sort function provided by the C library I lost the indexes reference before and after the sort. Is there a way to achieve this by using standard function or I have to write by hand the sorting algorithm?

Thank you

---

### Post by trent.josephsen on 2013-07-14
No, there's no standard function that will work for you. You could potentially make qsort work with a careful choice of data structures, but I think that would be more work than writing your own sort function, and it's probably not in the spirit of the assignment to do it that way in the first place.

---

### Post by ofnuts on 2013-07-14
Why don't you use a single array of aggregates?

---

### Post by trent.josephsen on 2013-07-14
Because it's a homework problem and the CS prof won't let him change the parameters.

---

### Post by erotavlas on 2013-07-15
Yes, it's an homework. When I have done it, I will post the solution.
Best Regards

---

### Post by ofnuts on 2013-07-15
So create a 4th array, fill it with array[i]=i, sort it using qsort() with a function that, to compare two integers, use them as indices in the first array  and compare the contents. This will give you an array of indices in the 3 original arrays sorted according to the contents of the first array.

---

