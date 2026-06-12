---
title: "Fill in matrix with possible combinations?"
date: 2011-07-06
forum: Programming Talk
---

### Post by camper365 on 2011-07-06
I have a matrix that I would like to fill in with possible combinations of numbers.  Basically, if I have a 9x9 matrix I want to fill in in with all of the possible arrangements of numbers from 0-81.  How would I do that?  I tried looking up permutation matrices, but I don't really understand them.

---

### Post by Bachstelze on 2011-07-06
What you're saying is way too vague.  I think an example, with a 2x2 matrix if necessary, would help understand what you want.

---

### Post by schauerlich on 2011-07-06
For all possible arrangements of the numbers 0-81, you'd need at least 82 * 82! bytes. I'm going to go ahead and say you don't have that much memory.

What is it you're trying to do?

---

### Post by camper365 on 2011-07-06
> **schauerlich said:**
> For all possible arrangements of the numbers 0-81, you'd need at least 82 * 82! bytes. I'm going to go ahead and say you don't have that much memory.

What is it you're trying to do?

I don't need all of the combinations at once. I just need to run a test on all of the different combinations.  After I run the test, I can delete the matrix to try the next combination.
In a 2x2 matrix, I want the numbers 1,2,3, and 4 to be in all of their possible positions so that it would be a unique matrix.

---

### Post by Arndt on 2011-07-06
> **schauerlich said:**
> For all possible arrangements of the numbers 0-81, you'd need at least 82 * 82! bytes. I'm going to go ahead and say you don't have that much memory.

What is it you're trying to do?

In particular, you need a bigger matrix than 9x9. I think the numbers 1-81 are meant.

---

### Post by Arndt on 2011-07-06
> **camper365 said:**
> I don't need all of the combinations at once. I just need to run a test on all of the different combinations.  After I run the test, I can delete the matrix to try the next combination.
In a 2x2 matrix, I want the numbers 1,2,3, and 4 to be in all of their possible positions so that it would be a unique matrix.

There are 81! permutations. That's about 6e120. Even if the test takes one clock cycle, doing it for all permutations will take around 10^110 seconds.

---

### Post by schauerlich on 2011-07-06
> **camper365 said:**
> I don't need all of the combinations at once. I just need to run a test on all of the different combinations.  After I run the test, I can delete the matrix to try the next combination.
In a 2x2 matrix, I want the numbers 1,2,3, and 4 to be in all of their possible positions so that it would be a unique matrix.

What language is this? Many languages have this in the standard library. For example, C++ has [next_permutation](http://www.cplusplus.com/reference/algorithm/next_permutation/), python has [itertools.permutations](http://docs.python.org/library/itertools.html#itertools.permutations), etc.

I agree with Arndt, though. Iterating through 81! permutations will not happen in this lifetime. What is it you're trying to accomplish with the permutations and tests?

---

### Post by ve4cib on 2011-07-06
You realize there are (9*9)! different permutations of those numbers, right?  According to my Python interpreter, that number comes out as:

```

>>> math.factorial(9*9)
5797126020747367985879734231578109105412357244731625958745865049716390179693892056256184534249745940480000000000000000000L

```

which is a staggeringly huge number.  Put another way, 52! (the number of ways of arranging a deck of cards) is greater than the number of stars in the galaxy.  By several orders of magnitude.  And 81! is several orders of magnitude bigger than that.

But, in order to do this the easiest way would probably be to use a 1-dimensional array of length 81 (9 * 9).  Fill the array with the numbers 1-81 (or 0-80, or however you want), and use a permutation successor generating function* to create the successor to each permutation.  That way you only need one array of fixed size, and minimal processing to generate each new permutation.  (There are many algorithms to generate permutation successors.  Some quick research on combinatorial algorithms will give you some.)

For every permutation you generate you simply print out the array as if it were a matrix.  Every 9th element starts a new row.

For kicks, here's a Python implementation using n=3 instead of n=9, along with the output*.  (I'm using Python's itertools.permutations function as the generator.)

```

#!/usr/bin/python

import itertools

# the size of the square matrix
n = 3

perms = itertools.permutations(range(n**2))

count = 0
for p in perms:
    l = list(p)
    
    # print out the array as a matrix
    count = count+1
    print 'Matrix #',count
    for i in range(n):
        for j in range(n):
            print "%2d"%l[i * n + j],
        print
    print

```

Output (note there are 9! matrices generated):
```

$ time python permmatrix.py > out.txt
real	0m4.800s
user	0m4.490s
sys	0m0.130s

```

*The resulting text file is over 15MB in size, and contains 362880 3x3 matrices.  Compressed as a bz2 it's still over 1MB.  In order to upload it I've had to 7zip it, and put that into a bz2 (Ubuntu Forums does not appear to allow 7zip attachments).

This should give you some size of the immense scale of the project you're proposing.

---

