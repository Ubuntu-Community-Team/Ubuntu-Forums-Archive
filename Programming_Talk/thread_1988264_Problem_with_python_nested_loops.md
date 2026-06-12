---
title: "Problem with python nested loops"
date: 2012-05-27
forum: Programming Talk
---

### Post by TheHimself on 2012-05-27
I've written a code like
```

for i in A:
    for j in B
       [Do something]

```

But surprisingly, the inner loop is run only once (for the "first" element of A). I see this by putting print commands. Both A, and B are sets given by itertools.product. It seems that the inner loop somehow empties the set B!

---

### Post by Bachstelze on 2012-05-27
Are we supposed to guess what the code actually does?

---

### Post by TheHimself on 2012-05-27
Here is what I've done so far.
```

def diffs(n, n_out):  
 if( n<2 or n_out > n): return     
 
 n_in=n-n_out
 iindex_set= itertools.product(set([-1,1]), repeat=n_in)
 oindex_set= itertools.product(set([-1,1]), repeat=n_out)
 m=4-n
 
 diff={}    
 for I in iindex_set:
      print "I=", I
      for J in oindex_set:
           diff[(I,J)]=0
           print "J=", J
           if  sum(I)-sum(J)!=m:  
                 continue 
           polygon=[] 
           print ("Polygon=")
           for i,elem in enumerate(I): 
                 polygon.append(i+1)
                 print i+1
           for j,elem in enumerate(J): 
                 polygon.append(n_out-j+i+1)
                 print n_out-j+i+1
     
```

---

### Post by Bachstelze on 2012-05-27
Iterators are not lists. When you have reached the end of an iterator, you can't "go back".

```
firas@av104151 ~ % cat iter.py 
import itertools

iter = itertools.product([-1, 1], repeat=3)
print "pass 1"
for i in iter:
    print i
print "pass 2"
for i in iter:
    print i
firas@av104151 ~ % python iter.py 
pass 1
(-1, -1, -1)
(-1, -1, 1)
(-1, 1, -1)
(-1, 1, 1)
(1, -1, -1)
(1, -1, 1)
(1, 1, -1)
(1, 1, 1)
pass 2

```

---

### Post by Bachstelze on 2012-05-27
So just make lists out of your iterators:

```
firas@av104151 ~ % cat iter.py   
import itertools

iter = list(itertools.product([-1, 1], repeat=3))
print "pass 1"
for i in iter:
    print i
print "pass 2"
for i in iter:
    print i
firas@av104151 ~ % python iter.py
pass 1
(-1, -1, -1)
(-1, -1, 1)
(-1, 1, -1)
(-1, 1, 1)
(1, -1, -1)
(1, -1, 1)
(1, 1, -1)
(1, 1, 1)
pass 2
(-1, -1, -1)
(-1, -1, 1)
(-1, 1, -1)
(-1, 1, 1)
(1, -1, -1)
(1, -1, 1)
(1, 1, -1)
(1, 1, 1)

```

---

### Post by TheHimself on 2012-05-27
Thanks it worked!! :guitar:

---

