---
title: "Help debugging some basic python."
date: 2011-10-05
forum: Programming Talk
---

### Post by Beauxesprits13 on 2011-10-05
why is this:
[PHP]
    #where gap = -2
    for x in range(1, len(matrix[0])):
        matrix[0][x] = matrix[0][x-1] + gap

    print matrix[/PHP]returning:

> [0, -2, -4, -6, -8], 
[0, -2, -4, -6, -8], 
[0, -2, -4, -6, -8]instead of:

> [0, -2, -4, -6, -8],
[0, 0, 0, 0, 0],
[0, 0, 0, 0, 0]...ectIt has been frustrating me for some time as I have been trying to iterate over x items in the zero-th nested list yet it iterates over x items in all lists.

---

### Post by ofnuts on 2011-10-05
> **Beauxesprits13 said:**
> 
It has been frustrating me for some time as I have been trying to iterate over x items in the zero-th nested list yet it iterates over x items in all lists.Works for me:

```

>>> gap=-2
>>> matrix=[[0,0,0,0,0],[0,0,0,0,0],[0,0,0,0,0]]
>>> 
>>> for x in range(1, len(matrix[0])):
...     matrix[0][x] = matrix[0][x-1] + gap
... 
>>> print matrix
[[0, -2, -4, -6, -8], [0, 0, 0, 0, 0], [0, 0, 0, 0, 0]]

```

But since your "matrix" has a two dimensions, the output should have two levels of brackets, so I suspect that you code is not really doing "print matrix" and prints the first line repeatedly.

---

### Post by nvteighen on 2011-10-05
All I can say is that probably, *print matrix* is misindented...

EDIT: Anyway, that's a quite weird way to iterate over the list; you could use xrange(len(matrix[0]) and not substracting 1 to x for accessing the matrix's item.

---

### Post by Beauxesprits13 on 2011-10-07
Thanks for helping out. i think the problem was this line:

[PHP][[0]*(len(X)+1)]*(len(Y)+1)[/PHP]

that i used to build my original matrix and then substitute values into. does this mean that python remembers the origanal equality of the rows in the matrix from [[0]*x]*y?

Ffrom memory i was printing with:  for row in matrix: print row

---

### Post by Tony Flury on 2011-10-07
> **Beauxesprits13 said:**
> Thanks for helping out. i think the problem was this line:

[PHP][[0]*(len(X)+1)]*(len(Y)+1)[/PHP]

Ffrom memory i was printing with:  for row in matrix: print row

Yes what that does is create multiple references to a single object namely [0,0,0,0,0] (assuming len(X) = 3)

so when you change anything in matrix[1] you are changing the same object as matrix[0] since each row in your matrix is the same.

you need to populate your matrix explicitly (like ofnuts did) or do it another way - but using the * operator to create n copies of an object will actually create n copies of the referece to the object - and you will see the behaviour you see here.

Look up the difference between shallow and deepcopy for instance.

---

