---
title: "linearly dependent columns in MATLAB"
date: 2012-05-04
forum: Programming Talk
---

### Post by .vogue on 2012-05-04
Hello everybody,
Any idea on how to find the indices of linearly dependent columns in MATLAB?

---

### Post by Zugzwang on 2012-05-04
Program the following idea as a script:

```

Iterate over all pairs (c1,c2) of columns
  Find the best value x such that x*c1 = c2
  Then compute |x*c1 - c2|. It is it below epsilon, print out that c1 is lin. dep. to c2

```

You also have to find a suitable value for epsilon. Using the MATLAB help, you can surely implement the idea above in no time.

---

### Post by .vogue on 2012-05-04
Any idea on how to find the threshold / epsilon value?

---

### Post by Zugzwang on 2012-05-04
> **.vogue said:**
> Any idea on how to find the threshold / epsilon value?

It is application-dependent and depends on the numeric stability of the operations that you used to get this matrix.

---

### Post by PaulM1985 on 2012-05-04
> **Zugzwang said:**
> Program the following idea as a script:

```

Iterate over all pairs (c1,c2) of columns
  Find the best value x such that x*c1 = c2
  Then compute |x*c1 - c2|. It is it below epsilon, print out that c1 is lin. dep. to c2

```

You also have to find a suitable value for epsilon. Using the MATLAB help, you can surely implement the idea above in no time.

This is only going to find columns that are linearly dependent on one other column.  If you have:
```

0 1 1
1 0 1
0 0 0

```
By the above psuedocode these would be linearly independent, which is false, column 3 is dependent on 1 and 2.

Paul

---

### Post by Zugzwang on 2012-05-04
> **PaulM1985 said:**
> This is only going to find columns that are linearly dependent on one other column. 


This is how I understood the question. Because otherwise, there is no unique answer, and the OP would have asked for *one* possible solution. Anyway, for that case, a quick google search reveals this possible answer: [http://www.math.ucdavis.edu/~daddel/Math22al_S02/LABS/LAB7/lab7_Winter03/node14.html](http://www.math.ucdavis.edu/~daddel/Math22al_S02/LABS/LAB7/lab7_Winter03/node14.html)

---

### Post by 3Miro on 2012-05-04
The question is poorly stated. A set of vectors is either linearly dependent or linearly independent and property carries to the entire set, not just a bunch of vectors. There is no criteria that can say "this vector is linearly dependent and this one is not".

If you have a set of vectors, you can ask if another vector is dependent or independent from the set, however, if you start with a set in the first place, there is no way to distinguish between the vectors inside.

The best that you can do is to use the fact that the columns of the vectors are already ordered. You can just check one by one, if vector i+1 is independent from the first i vectors.

Since this looks like a homework problem, I will give no further advice.

---

