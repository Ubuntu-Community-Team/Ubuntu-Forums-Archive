---
title: "[SOLVED] 3 variables equation"
date: 2008-12-05
forum: Programming Talk
---

### Post by StOoZ on 2008-12-05
yes this is homework , and NO im not looking for a solution , just for some points.

im trying to solve this for the last couple of hours , to no avail.
any idea how to do the following (NOT SOLUTION!!!!!) :
equation : Ax + By + Cz = D 
read A , B , C , D , and N , and find all the solutions in the range of :
-N<= x,y,z <=N

for example : if x = k , y = f , z = m , so if 
-N<= k,f,m <=N
so one of the solutions is : (k,f,m).



thanks!

---

### Post by nvteighen on 2008-12-05
Usually you need n equations to solve a system for n variables... So, I guess you have 3 equations or otherwise, you'll have to use parametrical values.

Have you looked at [Gaussian elimination]("http://en.wikipedia.org/wiki/Gaussian_elimination")?

---

### Post by aashay on 2008-12-05
3 nested for loops?

---

### Post by pp. on 2008-12-05
What do you mean by

> **StOoZ said:**
> 
-N<= x,y,z <=N

---

### Post by cszikszoy on 2008-12-05
> **pp. said:**
> What do you mean by

Pretty sure that means find all solutions where x, y, and z are between +- N

---

### Post by pp. on 2008-12-05
> **cszikszoy said:**
> Pretty sure that means find all solutions where x, y, and z are between +- N

Ah. That would be

(-N <= x <= N) v (-N <= y <= N) v (-N <= z <= N)

I guess. 

For the problem to make any kind of sense, I also would guess that for x, y and z we have to consider natural numbers only?

For smallish values of N I would be tempted to do a brute force approach. Simply create all combinations of x,y,z and run each triplet through the equation.

---

### Post by slavik on 2008-12-05
in this situation (since we know the range) brute force is the only option.

---

### Post by StOoZ on 2008-12-05
ok the problem was solved , thanks a lot!!
I just tried over and over again.
):P

---

### Post by WitchCraft on 2008-12-05
You have 4 variables, a,b,c,d:

ax +by +cz = d

this is ax + by + cz -d = 0
which is a plane.
This means the solution is something from analytic geometry (vectors).

You either need 3 equations (if d is given), or then you parametrize with t, where the number of variables minus the number of equations equals the degrees of free"doom".

Now assuming you have:
1x + 1y + 1z =  2
4x + 2y + 1z =  7
1x - 1y + 1z = -2


so you get the coefficient's matrix:
x      y      z     |    d
------------------- |---------    
1      1      1     |    2
4      2      1     |    7
1     -1      1     |   -2

-----------------------------


yo shall now substitute by row 2 = row 2 - (4/1) * row 1 
and row 3 = row 3 - (1/1) * row 1

then row 3 = row 3 - (-1/[row2 y from last step]) * row 2


this leavs you with a triangular matrix:
x      y      z     |    d
------------------- |---------    
1      1      1     |    2
0      2      3     |    1
0      0      3     |   -3

-----------------------------

now you can do backward substitution:
3z = -3 --> z
use the value obtained  for z from row3 in row 2 --> y
now use z & y from the two previous rows to solve for z in the first row.

Doing this in a computer program shouldn't be that difficult, just remember to use double and not int, because you're doing divisions...
):P


if you have one or more rows of zeros, or one line being a multiple of the other, then the system is unsolvable...

- exactly one solution for rank (koefficient matrix)= rank(extended coefficient matrix)
- infinite solutions for rank(coefficient matrix ) = rank(extended coefficient matrix)
- no solution if rank(coefficient matrix) < rank(extended coefficient matrix)

Now copy paste the rank function from somewhere from the internet...
(and look at how it works)


also x[i] = det(A[i])/det(A)
wikipedia, cramer's rule



now assume a parametrization:
4x + 2y + (a+2) z = a
2x + 2y + (a+1) z = 2a
5x + 4y - (a^2-a-2)z = 3a -1

now set up the extended coefficient matrix:

x      y      z      |    d
---------------------|---------    
4      2a    a+2     |    a
2      2a    a+1     |   2a
4      4a  -a^2+a+2  |   3a-1

-----------------------------

now subtract the first row (2/4) times from the second row and so forth


now this leaves:
x      y      z      |    d
---------------------|---------    
4      2a    a+2     |    a
0      2a     a      |   2a
0      0  a*(a+1)    |   a-1

-----------------------------

so for a = -1 follows, rank(A) = rank(B) = 2
so you have infinite solutions

for a = 0 you have rank(A) = 1 and rank(B) = 2

so there exist no solutions for a = 0.

in every other case, you've got exactly one solution.
Done.
now check whether all solutions are in the range!  implement! :lolflag:

---

