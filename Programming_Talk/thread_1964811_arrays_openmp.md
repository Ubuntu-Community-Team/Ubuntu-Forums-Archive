---
title: "arrays_openmp"
date: 2012-04-24
forum: Programming Talk
---

### Post by chmcy on 2012-04-24
hello, i am writing a program in openmp and i've got a 2D array. i want to make some calculations and the elements of each column depend from the elements of the previous column. i just want to make all the values of each column to be executed together. Is that code right? thank u

for(i=0;i<N;i++)
#pragma omp parallel for
for(j=0;j<N;j++)
array[j][i]=...

---

### Post by 11jmb on 2012-04-24
That is correct syntax, but is there a reason that you are parallelizing the inner loop, and not the outer?

---

### Post by chmcy on 2012-04-24
i believe its better .. do i have to parallelize both of them or the first one?

---

### Post by 11jmb on 2012-04-24
If the socratic method worked over internet forums, I would ask why you believed it was better, but it doesn't, so I'll just tell you :)

There is an overhead that is incurred whenever you branch and join threads. Suppose N is 1000. With the "#pragma omp parallel for" inside your first loop, your program will branch and join 1000 times. Outside the outermost loop, it will only branch and join once.

There is sometimes a compelling reason to branch/join inside a loop because it works better with the shared memory, but in general it is better to put your "#pragma omp parallel for" outside the first loop

---

### Post by 11jmb on 2012-04-24
I believe the buzzword here is "dispatch overhead", but don't quote me on that. It's been a while since I've written any openmp

Remember that when you have a nested loop inside a parallel loop, each thread will need a local counter for the nested loop, so your improved code would be:

```

#pragma omp parallel for private(j)
for(i=0;i<N;i++)
    for(j=0;j<N;j++)
        array[j][i]=...

```

---

### Post by chmcy on 2012-04-25
that was a very nice explanation! thank u so much! :)

---

