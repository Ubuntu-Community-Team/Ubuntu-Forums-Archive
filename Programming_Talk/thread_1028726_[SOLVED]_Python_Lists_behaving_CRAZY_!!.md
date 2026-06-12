---
title: "[SOLVED] Python Lists behaving CRAZY !!"
date: 2009-01-02
forum: Programming Talk
---

### Post by jit.sd on 2009-01-02
Hey , 
am having a bit of a problem and I dont know how to get around it . This is the first time I am using python and am having some trouble with lists . 

please have a look at this code 
```

openList = [0,1]
prop = [0,0]

cellList = [prop,prop]
print "part 1"
for x in openList:
        print x,"*",cellList[x]
        p=cellList[x][1]
        g=(cellList[p][0])+1
        cellList[x][0]=g
        print x,"#",cellList[x]

print "part 2"
for x in openList:
        print x," ",cellList[x]

```

I would have expected the Output to be :

```

part 1
0*[0,0]
0#[1,0]
1*[0,0]
1#[2,0]
part 2
0 [1,0]
1 [2,0]

```

But for some reason beyond my comprehension the output comes as :

```

part 1
0 * [0, 0]
0 # [1, 0]
1 * [1, 0]
1 # [2, 0]
part 2
0   [2, 0]
1   [2, 0]

```

Can someone explain why this is so ? 

Am using python 2.5.2 , the one that comes with Ubuntu , Hardy Heron x64. 

Thanks , 
Jit

---

### Post by Tony Flury on 2009-01-02
your code has 
```

cellList = [prop,prop]

```

What this actually does is puts two references to the prop list into cellList - which means when you change one copy of prop, you will change both instances, because they are the same object.

If you do this 
```

cellList =[[0.0][0.0]]

```

your script will do what you expect.

---

### Post by Can+~ on 2009-01-02
[PHP]a = [0, 1]
b = [a, a]

print "original:",b # prints [[0, 1], [0, 1]]

b[0][0] = 1

print "modified:",b # prints [[1, 1], [1, 1]][/PHP]

Python doesn't actually copy the values from one list to another, it stores a reference, so it happens as Tony Flury pointed out.

---

### Post by Wybiral on 2009-01-02
A list is an object. Think about it, you put the same object in the containing list twice, then you modified it and expected the same object to be different just because it was referenced in two different locations. Copy a list if you need two different instances, but remember that they ARE mutable objects.

---

### Post by pmasiar on 2009-01-02
As a beginner, get used to the fact that problem is usually that you do not exactly understand what you asked computer to do - and it alsways obeys without failure, even if you don't know what you asked for.

Wyb explained what happened - uoi used same object twice.

to make (shalow) copy, just use slice of a list:

cell_list = [prop[:], prop[:]]

If you need deeper copy, use deepcopy()

But more likely, if you need more than 1-dimensional list, dictionary with tuples as key is what you want instead:

matrix = {}
matrix[1,2] = 42 # or even another dict

---

### Post by jit.sd on 2009-01-03
Hey guys , 

thanks problem solved . You guys were right , I was copying references when I should have been using copy.deepcopy() 

Its working fine now , thank you :) 

Jit

---

