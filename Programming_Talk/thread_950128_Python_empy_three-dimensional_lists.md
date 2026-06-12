---
title: "Python empy three-dimensional lists"
date: 2008-10-16
forum: Programming Talk
---

### Post by Gannin on 2008-10-16
How does one create an empty three-dimensional list in Python?  I know to create a regular empty list you would type:

```
x = []
```

But typing:

```
x = [][][]
```

Creates an error.  Any ideas?

---

### Post by jimi_hendrix on 2008-10-16
i havnt had to do this in a while but shouldnt it go and am known to post misinformation when its past 9:00 but i think its this ```
x = [[][][]]
```

---

### Post by Gannin on 2008-10-16
Unfortunately it doesn't like that either.

---

### Post by mssever on 2008-10-16
> **Gannin said:**
> How does one create an empty three-dimensional list in Python?  I know to create a regular empty list you would type:

```
x = []
```But typing:

```
x = [][][]
```Creates an error.  Any ideas?
Try ```
x = [[], [], []]
```But there really isn't any reason to do this in Python. Python != Java.

EDIT: Clarification: Just create an empty list (x = []) and append whatever data you want. Or use a list comprehension if appropriate. In fact, the only reason to create an empty list in the first place is so you can call list methods, such as append().

---

### Post by pmasiar on 2008-10-16
You can create a list of lists, but simpler is to use a dictionary which key is a tuple.

```

x3d = {}
x3d[x, y, z] = 1

```

---

### Post by Gannin on 2008-10-16
Yes Python isn't Java.  That doesn't mean you shouldn't be able to have dynamic three-dimensional arrays that can hold objects.

I basically want a memory cube so that I can say:

```
cube[x][y][z] = someObject
```

---

### Post by mssever on 2008-10-16
When I use multidimensional arrays/lists (which isn't all that often), I build them dynamically. E.g., for a two dimentional structure, I build a row, append it to the main object, and repeat. Of course, this probably wouldn't work so well for sparse data.

Here's another example, from the [Python documentation]("http://docs.python.org/library/stdtypes.html#sequence-types-str-unicode-list-tuple-buffer-xrange"): ```
x = [[] for i in range(3)]
```Which suggests this, by extension, though it suffers from poor readability, so there's probably a better way to do things: ```
x = [[[] for i in range(3)] for j in range(3)]
```

---

### Post by Gannin on 2008-10-16
> **pmasiar said:**
> You can create a list of lists, but simpler is to use a dictionary which key is a tuple.

```

x3d = {}
x3d[x, y, z] = 1

```

This looks like it's on the right track.  It looks like it's nicely dynamic.  If you already had a size in mind for the array, say 100 x 100 x 100, I guess the only way to initialize this structure to make sure each element was present would be to run it through a for loop.  Something like:

```

x = {}
for loop in range(100): x[loop, loop, loop] = 0

```

---

### Post by Can+~ on 2008-10-17
> **Gannin said:**
> Yes Python isn't Java.  That doesn't mean you shouldn't be able to have dynamic three-dimensional arrays that can hold objects.

I basically want a memory cube so that I can say:

```
cube[x][y][z] = someObject
```

That's a weird way to access a point in a cube (if that's what you want to do), since you'll need the x and y to get to z.

A more logical approach would be to have a tuple for that

[PHP]point = (x, y, z)[/PHP]

Or, define a new class point, which would be neater, and more Object Oriented:

[PHP]class point3d:
    def __init__(self, x=0, y=0, z=0):
        self.x = x
        self.y = y
        self.z = z

apoint = point3d(2, 4, 7)
another_point = point3d(x=2, z=1)

print apoint.x[/PHP]

edit: well, by memory "cube" I got your idea, it wasn't 3d at all.

[PHP]
cube = [[[2]]]

print cube[0][0][0] # outputs 2
[/PHP]

and remember that python uses linked lists instead of "arrays" (as in, contiguous bytes of data with random access), you can use import array for the real deal.

---

### Post by Gannin on 2008-10-17
An array module eh?  Now I'm going to have to look that up :P.

---

### Post by Quikee on 2008-10-17
With [numerical python]("http://numpy.sourceforge.net/numdoc/HTML/numdoc.htm#pgfId-35605") you can do:

[PHP]import Numeric

a = Numeric.zeros((5,5,5)) # creates a 5 times 5 times 5, 3D array
a[0][0][0] = 1
print a[/PHP]

---

### Post by Gannin on 2008-10-17
I noticed that the array module only handles integers and text and if you want to create a multidimensional array of objects, as alluded to above, you have to use the Numeric module's array object.

---

### Post by NovaAesa on 2008-10-17
I would suggest having a dictionary with 3-tuples (vectors of 3 dimensions, not 3 vectors) as they keys. You will thank yourself in the long run, or at least I did when I had to use n-dimensional data structures in Python :P

---

### Post by CurlyNY on 2009-08-19
This isn't aesthetically pleasing, but I just implemented the following:
    vals = []
    for i in range(len(phidict)):
        vals.append([])
        for j in range(len(yeardict)):
            vals[i].append([])
            for k in range(7):
                vals[i][j].append([])


For my code, phidict and yeardict were dictionaries over a bunch of strings and I was interested in getting a three-d list of dimension len(phidict) by len(yeardict) by 7.  This allowed me to use append to populate the lists vals[i][j][k].

Perhaps not the best python solution, but for a c-coder like myself, it did the trick.

hth

---

### Post by Gannin on 2009-08-19
It looks good to me.  Thanks for the input :).

---

### Post by Can+~ on 2009-08-19
> **CurlyNY said:**
> This isn't aesthetically pleasing, but I just implemented the following:
[PHP]    vals = []
    for i in range(len(phidict)):
        vals.append([])
        for j in range(len(yeardict)):
            vals[i].append([])
            for k in range(7):
                vals[i][j].append([])[/PHP]

Perhaps not the best python solution, but for a c-coder like myself, it did the trick.

Yeah, no kidding, I could smell C programmer from here.

Btw, what is that supposed to be? yeardict? timedate module not good enough?

---

### Post by Polygon on 2009-08-20
curlyNY has got it right. I have recently tried to do this and you can't just declare 2d lists like that, you have to iterate through them.

---

