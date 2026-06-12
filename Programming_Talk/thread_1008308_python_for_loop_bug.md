---
title: "python for loop bug"
date: 2008-12-11
forum: Programming Talk
---

### Post by Mars8082686 on 2008-12-11
I'm trying to get a list to be numbered [0-3][0-3]. The following *should* work:
```
>>> for x in range(4):
...   for y in range(4):
...     img[x][y]=str(x)+str(y)
... 
>>> print img
```


but it gives me:
[['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33']]


Why is x not incrementing? When I just print out x and y it gives me what I want:
```
>>> for x in range(4):
...   for y in range(4):
...     print x,y
... 
```
0 0
0 1
0 2
0 3
1 0
1 1
1 2
1 3
2 0
2 1
2 2
2 3
3 0
3 1
3 2
3 3

I'm probably missing something basic in python. (I'm somewhat new to it).

Thanks.

---

### Post by Wybiral on 2008-12-11
Are you posting all of your code?

---

### Post by Mars8082686 on 2008-12-11
Yea, It's not part of a larger program.

Here's my exact test session:

```

~ mars$ python
Python 2.5 (r25:51918, Sep 19 2006, 08:49:13) 
[GCC 4.0.1 (Apple Computer, Inc. build 5341)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> img = [['']*4]*4
>>> for x in range(4):
...   for y in range(4):
...     img[x][y]=str(x)+str(y)
... 
>>> print img
[['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33']]
>>> quit()
~ mars

```

---

### Post by nvteighen on 2008-12-11
This may be related to Python call-by-reference policy, that is, that you pass everywhere the location to some object that's being incremented subsequently in all slots... but it's really weird... it should work that way, at least all other similar programming languages would yield that correctly...

---

### Post by unutbu on 2008-12-11
```
img = [['']*4]*4
```

is not the same as 
```

img = [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
```


The first version makes a list of the form
```

[A,A,A,A]
```

each A = ['', '', '', ''] and each A is the exact same object.

The second version makes a list of the form
```

[A,B,C,D] 
```

with each A,B,C,D being distinct objects.

So in the first version, when you alter elements of A, you alter the element in four places.

[PHP]
#!/usr/bin/env python

img = [['']*4]*4
print img
for x in range(4):
    for y in range(4):
        img[x][y]=str(x)+str(y)
        print img

# [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '', '', ''], ['00', '', '', ''], ['00', '', '', ''], ['00', '', '', '']]
# [['00', '01', '', ''], ['00', '01', '', ''], ['00', '01', '', ''], ['00', '01', '', '']]
# [['00', '01', '02', ''], ['00', '01', '02', ''], ['00', '01', '02', ''], ['00', '01', '02', '']]
# [['00', '01', '02', '03'], ['00', '01', '02', '03'], ['00', '01', '02', '03'], ['00', '01', '02', '03']]
# [['10', '01', '02', '03'], ['10', '01', '02', '03'], ['10', '01', '02', '03'], ['10', '01', '02', '03']]
# [['10', '11', '02', '03'], ['10', '11', '02', '03'], ['10', '11', '02', '03'], ['10', '11', '02', '03']]
# [['10', '11', '12', '03'], ['10', '11', '12', '03'], ['10', '11', '12', '03'], ['10', '11', '12', '03']]
# [['10', '11', '12', '13'], ['10', '11', '12', '13'], ['10', '11', '12', '13'], ['10', '11', '12', '13']]
# [['20', '11', '12', '13'], ['20', '11', '12', '13'], ['20', '11', '12', '13'], ['20', '11', '12', '13']]
# [['20', '21', '12', '13'], ['20', '21', '12', '13'], ['20', '21', '12', '13'], ['20', '21', '12', '13']]
# [['20', '21', '22', '13'], ['20', '21', '22', '13'], ['20', '21', '22', '13'], ['20', '21', '22', '13']]
# [['20', '21', '22', '23'], ['20', '21', '22', '23'], ['20', '21', '22', '23'], ['20', '21', '22', '23']]
# [['30', '21', '22', '23'], ['30', '21', '22', '23'], ['30', '21', '22', '23'], ['30', '21', '22', '23']]
# [['30', '31', '22', '23'], ['30', '31', '22', '23'], ['30', '31', '22', '23'], ['30', '31', '22', '23']]
# [['30', '31', '32', '23'], ['30', '31', '32', '23'], ['30', '31', '32', '23'], ['30', '31', '32', '23']]
# [['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33'], ['30', '31', '32', '33']]


img = [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
print img
for x in range(4):
    for y in range(4):
        img[x][y]=str(x)+str(y)
        print img

# [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', ''], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', ''], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', '23'], ['', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', '23'], ['30', '', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', '23'], ['30', '31', '', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', '23'], ['30', '31', '32', '']]
# [['00', '01', '02', '03'], ['10', '11', '12', '13'], ['20', '21', '22', '23'], ['30', '31', '32', '33']]
[/PHP]

---

### Post by Mars8082686 on 2008-12-11
Makes sense. Thanks. 

Is there an easier way to do this, though? 
img = [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
That seems like it could bet somewhat cumbersome.

---

### Post by Wybiral on 2008-12-11
List comprehension:
```

lst = [[str(x) + str(y) for x in range(4)] for y in range(4)]

```

---

### Post by wmcbrine on 2008-12-11
```
img = [[''] * 4, [''] * 4, [''] * 4, [''] * 4]
```

works to initialize the list. Or better:

```
img = [[''] * 4 for i in range(4)]
```

But Wybrial's solution is best, replacing the entire loop. Although I think you were going more for:

```
img = [[str(x) + str(y) for y in range(4)] for x in range(4)]
```

---

### Post by mssever on 2008-12-11
> **Mars8082686 said:**
> Makes sense. Thanks. 

Is there an easier way to do this, though? 
img = [['', '', '', ''], ['', '', '', ''], ['', '', '', ''], ['', '', '', '']]
That seems like it could bet somewhat cumbersome.
Not that I know of, but I can't think of any situations where you'd need something like this in Python. You could easily append() to the list as needed. No need to declare it ahead of time.

---

### Post by pmasiar on 2008-12-11
... and use a dictionary instead of a list of lists (where key is a tuple): img[x,y] = '...'

---

### Post by mssever on 2008-12-11
> **pmasiar said:**
> ... and use a dictionary instead of a list of lists (where key is a tuple): img[x,y] = '...'
Why do I never remember that you can do that? :)

---

### Post by nvteighen on 2008-12-11
> **mssever said:**
> Why do I never remember that you can do that? :)
I always forget dictionaries too... :p

---

### Post by Mars8082686 on 2008-12-11
> **pmasiar said:**
> ... and use a dictionary instead of a list of lists (where key is a tuple): img[x,y] = '...'

It should be a 4 x 4 list. The img var isn't a list of pixels, it's a 4 dimensional list of pygame surfaces (images).

---

### Post by mssever on 2008-12-11
> **Mars8082686 said:**
> It should be a 4 x 4 list. The img var isn't a list of pixels, it's a 4 dimensional list of pygame surfaces (images).
But what's the practical difference between these two:
```
img[w][x][y][z] = foo   # img is a list of lists of lists...
# and
img[w,x,y,z] = foo  #img is a single dictionary
```Either way, you can store and retrieve the same data, but the second is easier to handle in Python.

---

### Post by Mars8082686 on 2008-12-11
> **mssever said:**
> But what's the practical difference between these two:
```
img[w][x][y][z] = foo   # img is a list of lists of lists...
# and
img[w,x,y,z] = foo  #img is a single dictionary
```Either way, you can store and retrieve the same data, but the second is easier to handle in Python.

Maybe I'm missing something. Right now it's a two dimensional list: [['sureface00', 'sureface01', 'sureface02', 'sureface03'], ['sureface10', 'sureface11', 'sureface12', 'sureface13'], ['sureface20', 'sureface21', 'sureface22', 'sureface23'], ['sureface30', 'sureface31', 'sureface32', 'sureface33']]

I'm writing a game where the sprite is a character and it's convenient for my coding for it to be a 2 dimensional list. When I return the image to display on screen, I can just say img[direction][steps] where direction is the direction of the sprite (up, down, left, right) and the steps is the number that it is in in his 4 part walking sequence.

In this case wouldn't a list be more applicable then a dictionary? I'm new to python so I may be wrong.

---

### Post by mssever on 2008-12-11
> **Mars8082686 said:**
> Maybe I'm missing something. Right now it's a two dimensional list: [['sureface00', 'sureface01', 'sureface02', 'sureface03'], ['sureface10', 'sureface11', 'sureface12', 'sureface13'], ['sureface20', 'sureface21', 'sureface22', 'sureface23'], ['sureface30', 'sureface31', 'sureface32', 'sureface33']]

I'm writing a game where the sprite is a character and it's convenient for my coding for it to be a 2 dimensional list. When I return the image to display on screen, I can just say img[direction][steps] where direction is the direction of the sprite (up, down, left, right) and the steps is the number that it is in in his 4 part walking sequence.

In this case wouldn't a list be more applicable then a dictionary? I'm new to python so I may be wrong.
The point is, the practical difference between the two is only syntactical. If you said img[direction,steps] it would work just as well (provided, of course, that you set up img that way in the first place). Try it.

---

### Post by Wybiral on 2008-12-12
> **mssever said:**
> The point is, the practical difference between the two is only syntactical. If you said img[direction,steps] it would work just as well (provided, of course, that you set up img that way in the first place). Try it.

And since you're using tuples as the key, you can pass a pre-existing tuple right into it, such as a position vector:

```

some_dict[position]
# instead of
some_list[position[0]][position[1]]

```

---

