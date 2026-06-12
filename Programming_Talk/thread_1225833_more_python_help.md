---
title: "more python help"
date: 2009-07-29
forum: Programming Talk
---

### Post by Flynn555 on 2009-07-29
trying to initialize a list of lists in python
that has R rows and C columns

originally tried this 
```
M=[[0]*C]*R
```

but when i use that i cant access a given element 

i.e.
the line:
```
M[1][1] = 3 
```

makes the following changes to the list of lists

```
M = [[0, 3, 0, 0],
     [0, 3, 0, 0],
     [0, 3, 0, 0],
     [0, 3, 0, 0]]
```

ive tried to initialize it manually by the following:

```
i = 0
j = 0
M = []
while i < R:
     row = []
     while j < C:
        row.append(0)
        j+=1
     M.append(row)
     i+=1
```

but i get the same result.

i know its a result of each sublist having the same id

```
>>>print id(M[0][1])
135721132
>>>print id(M[1][1])
135721132
```
 

anyone know what i'm doing wrong?

---

### Post by monraaf on 2009-07-29
Try this:

[PHP]
M=[[0]*C for x in range(R)]
[/PHP]

---

### Post by unutbu on 2009-07-29
I think this does what you want:
[PHP]#!/usr/bin/env python
R=2
C=3
M=[[0 for i in range(C)] for j in range(R)]
print(M)
# [[0, 0, 0], [0, 0, 0]]
M[1][1]=3
print(M)
# [[0, 0, 0], [0, 3, 0]][/PHP]

When you use    
```

alist=[0]*C
M=[ alist ]*R 
```

you get R copies of the very same alist. So when you
change an element in alist, M gets changed in R places.

---

