---
title: "How to remove a function from a loop?"
date: 2009-10-14
forum: Programming Talk
---

### Post by banana_head on 2009-10-14
So I have a function that I wrote as a definition, U3V3.py (attached) that builds a sparse matrix, and is called when specifying 6 parameters, 5 are numbers, one is a 2D array. The array is called from the attached file called combo.py. The 5 numbers are actually functions of a variable, call it T. I then call this function while looping over T. This matrix can grow very large, and these are the cases I am interested in (hence sparse). An example could be written as:
[PHP]import U3V3
import combo
from scipy import linalg
from numpy import dot 
from scipy.linalg import eigvals 

q=3
L=3 
N=q**L
bb = combo.combinations( [[0,1,2],[0,1,2],[0,1,2]] )
for T in range(N):
     tt = T * 10
     a = 1.0**(tt)
     b = 0.9**(tt)
     c = 0.8**(tt)
     d = 0.7**(tt) 
     e = 0.6**(tt)

     u = U3V3.u3(a,b,c,d,e,bb)
     v = U3V3.v3(a,b,c,d,e,bb)
     tot = dot(u,v)
     tot = tot.todense()

     print vals 

[/PHP]
So you wont have to call a sparse eigenvalue routine, I let tot go to a dense matrix so we can use the eig routine within scipy. 

What I really would like to know is whether I can somehow call u and v outside the loop so that I only need to build the matrices once. For very large matrices, calling the matrix each time I change a,b,c,d,e within the loop really slows down the overall code. It seems that I would want to try to represent u and v symbolically, but I am trying to do this by calling as few modules as possible (for example, I dont want to call SymPy or something else). Is this possible? 

Thanks for having a look!

---

