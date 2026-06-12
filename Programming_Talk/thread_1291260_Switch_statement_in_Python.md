---
title: "Switch statement in Python?"
date: 2009-10-14
forum: Programming Talk
---

### Post by jsschreck on 2009-10-14
I am comparing a list of lists to itself to construct a particular matrix using Python. The overall construction gets really slow once my matrix starts to grow. The list contains combinations of something like [ [0,1,2], [0,1,2], [0,1,2] ] ... etc. So the combo routine would return things like [0,0,0], [0,0,1], ..., [2,2,2]. To compare the list to itself, I wrote two for loops that iterate over i and j. I am trying to make the following general statement more efficient:

Start by letting term = 1
[PHP]
if  i[0] == j[0]:
   term = term * 1
else:
   term = term * 0 
if  i[1] == j[1]:
   term = term * 1
else:
   term = term * 0 
[/PHP]

You can see that I leave out the i[2] == j[2] term. In general, my matrix grows when you keep appending more and more if statements like i[3] = j[3], i[4] =j[4], etc. while leaving out the last case (so what is happening is the list of combos grows from, for example, [ [0,1,2], [0,1,2], [0,1,2] ] to [ [0,1,2], [0,1,2], [0,1,2], [0,1,2], [0,1,2] ]. In this case, we would leave out the i[5] == j[5], but all others would contain the if/else statements. ) 

If you follow, the term then becomes, for example, something like term = 0 * 1 * 0 * 0, ... this is wasteful since I dont need to multiply term by zero more than once. In my example, if i[0] != j[0] (which means term = term * 0), how can I write what amounts to a GoTo statement and skip over the remaining cases? I looked into using a switch statement using dictionaries, but admittedly, got confused since I am a relatively new to Python. Also, the examples I was able to look at handled if/elif/else statements, whereas I have multiple if/then statements that share the common number 'term'. Any help / suggestions would be greatly appreciated!

---

### Post by benj1 on 2009-10-14
well there isn't a goto but continue might be of help

```
for x in [1,2,3,4]:
   if x == 1: 
      #do stuff#
      continue #starts loop with x == 2
   #do stuff#
```

sorry i cant be of more help, im not entirely sure what youre trying to do

---

### Post by diesch on 2009-10-14
Maybe you could give a concrete example for what you want to do. It sounds a bit confusing to me.

---

### Post by engla on 2009-10-14
> **jsschreck said:**
> 
If you follow, the term then becomes, for example, something like term = 0 * 1 * 0 * 0, ... this is wasteful since I dont need to multiply term by zero more than once. In my example, if i[0] != j[0] (which means term = term * 0), how can I write what amounts to a GoTo statement and skip over the remaining cases? I looked into using a switch statement using dictionaries, but admittedly, got confused since I am a relatively new to Python. Also, the examples I was able to look at handled if/elif/else statements, whereas I have multiple if/then statements that share the common number 'term'. Any help / suggestions would be greatly appreciated!
The goto statement you are seeking is called return. Write the code in a function and return early when the work is done early.

---

### Post by Can+~ on 2009-10-14
Why not use numpy matrices?

[PHP]import numpy as np

mata =  np.matrix("1 2; 3 4")

matb =  np.matrix("1 2; 1 2")

print mata == matb[/PHP]

Numpy does exactly as Matlab or R does, by returning the compared matrix:

```
[[ True  True]
 [False False]]
```

---

### Post by jsschreck on 2009-10-14
Ok, this is more specifically what I am doing. First, define my list comparison,

[PHP]
def combinations( L ):
    N = len( L )
    if N == 0:
        return []
    elif N == 1:
        return [
        L[0][i:i+1]
        for i in xrange( 0, len( L[0] ) )
    ]
    else:
        return [
            L[0][i:i+1] + subcomb
            for i in xrange( 0, len( L[0] ) )
            for subcomb in combinations( L[1:] )
        ][/PHP]

Next, give it a call: bb = combo.combinations( [[0,1,2], [0,1,2], [0,1,2]] ) 

Essentially what I am doing is using the if statements to utilize Dirac Deltas;

[PHP]
N = 27
u = sparse.lil_matrix((N,N))
m = 0 
for i in bb:
    n = 0 
    for j in bb:
          term = 1
          if  i[0] == j[0]: 
               term = term * 1 
          else: 
               term = term * 0  
          if  i[1] == j[1]: 
               term = term * 1 
          else: 
               term = term * 0

          u[m,n] = u[m,n] + term
          n += 1
     m += 1
u = sparse.csr_matrix(u) [/PHP]

There are actually even more if statements that I removed to make this more simple. You can convince yourself with my bb combo definition that as you add more and more [0,1,2]'s, the matrix grows rapidly (which is why I am using sparse since then nearly all elements will be zero).  Call the number of [0,1,2]'s in combo L. Then I will use L-1 if statements as the matrix grows. So if L = 5 ([[0,1,2], [0,1,2], [0,1,2], [0,1,2], [0,1,2]]), then I need to check when i[0] = j[0], ..., i[3] = j[3] and we leave out the last one.

---

### Post by dwhitney67 on 2009-10-14
Based on the OP's original query to make the series of if-elses more efficient, would this not work?
```

...
        term = 0

        if (i[0] == j[0]) and (i[1] == j[1]):
            term = 1

...

```

P.S.  Unless the rules of mathematics have changed in the last 5 minutes, any whole-number N multiplied by 1 is N.  Similarly, any whole-number N multiplied by 0 is 0.  :P

---

### Post by Can+~ on 2009-10-14
I don't even know what this algorithm tries to achieve, you're comparing a matrix to it's own, and get each time that a "i" and "j" sub-list contains the same elements?

```
[
[0, 0, 1]
[0, 0, 2]
[0, 1, 0]
[0, 1, 1]
[0, 1, 2]
[0, 2, 0]
...
]
```

The only element that would yield 1 would be... itself, so you're basically filling a matrix with something that would look like:

```

  0  1  2  ...
0 1, 0, 0  ...
1 0, 1, 0  ...
2 0, 0, 1  ...
3 .  .  .  ...
```

As those are the elements on which "i" and "j" will be pointing to the same element. (If I got the algorithm right).

You can get the identity matrix with (again, numpy):

[PHP]>>> numpy.eye(10)
array([[ 1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  1.,  0.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  1.,  0.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  0.,  1.,  0.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  0.,  0.,  1.,  0.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  1.,  0.,  0.],
       [ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  1.,  0.],
       [ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  1.]])[/PHP]

---

### Post by jsschreck on 2009-10-14
What I posted is just a piece of a broader routine that I need to fill a matrix that is supposed to describe certain physical systems. The rest of the routine that I did not include is fine, the part that I posted is my version of a Dirac Delta written in terms of if statements. What the algorithm does is, to use one piece as an example, it will start with one of the combos, take [0, 0, 0] and compare it to all combinations of [0,1,2], which includes [0,0,0], [0,0,1], ..., [2,2,2]. Then [0,0,1] to [0,0,0], ..., [2,2,2], etc. Each time there is a comparison test, I get a matrix element. Eventually you fill out a matrix:
 [PHP]
               0    1  .....                    2
               0    0   .... ..                 2
               0    0    .    ....              2
0 0 0          *     *    ......                * 
1 0 0          *     *   .....                  *
.              .     .                          .
.              .     .                          .
.              .     .                              
2 2 2          *     *                          *
[/PHP]
So if you look at the row 0 0 0. i[0] = 0, i[1] = 0, i[2] = 0. You compare this to the each of the columns of 0,1,2, with the first being 000, then 100, ... 222 (these are the j[0], j[1], and j[2]'s). Each time a comparison is done, you get a matrix element (*).

For the case above, you get the following matrix explicitly: 

[PHP]
[[ 1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.  0.  0.  0.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0   0.  0.  0.  0.  0.  0.  1.  1.  1.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.]
 [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  1.  1.  1.]]
[/PHP]

---

### Post by jpkotta on 2009-10-15
There is no reason to multiply by zero or one.  This speeds it up by an order of magnitude for me.  I assume that u is initialized to all zeros.  

```

for m,i in enumerate(bb):
    for n,j in enumerate(bb):
        if i[0] == j[0] and i[1] == j[1]:
            u[m,n] = 1

```

Edit: Also, it looks like u will always be symmetric, so you only need to do half of it.  Maybe there is a symmetric sparse matrix type already in scipy.

---

### Post by jsschreck on 2009-10-15
jpkotta, your suggestion definitely makes my routine faster, even with all the additional if statements that exist but that I did not post on this forum. Thank you! Additionally, thanks to all the rest of the folks that posted their suggestions.

---

