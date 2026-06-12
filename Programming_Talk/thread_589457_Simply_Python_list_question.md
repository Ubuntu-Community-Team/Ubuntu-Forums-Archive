---
title: "Simply Python list question"
date: 2007-10-24
forum: Programming Talk
---

### Post by amiga_os on 2007-10-24
Hi, sorry for the dumb question:

In c I can define an array like this:

```
int mylist[40]
```

That will give me 40 blank variables to work with.  How do I do that in Python?  From the docs - and maybe I missed something - I have to do this:

```
mylist = [range(40)]
for i in range(40):
[INDENT]mylist[i] = 0[/INDENT]
```

Python seems so tidy... there must be a better way of doing this.  Can anyone help?

---

### Post by amiga_os on 2007-10-24
And... funnily enough, that code doesn't even work either!

This is a frustratingly simple problem.... but I can't find the right syntax

---

### Post by amiga_os on 2007-10-24
OK...

fiddled more and solved the problem on my own, define the list like this:

```
mylist = [0] * x
```

Where x is the size you want the list to be.

---

### Post by Quikee on 2007-10-24
Is there a reason why you want to predefine 40 places for a variable. Lists in Python are dynamic which means that the size doesn't need to be predefined, which is not true for arrays in C.

If you need predefined array/list because you have to operate on 40 values pre setted to 0 you have to create 40 values and set them to 0, which is also true for C (int mylist[40]; also doesn't create an array with all values set to 0 but an array with all values set to "undefined" value, which is mostly 0). This is just what you did - but be cautious with such usage as it works in your case when using numbers, but if you would do [[]] * 40 you will get a list with 40 empty lists which are all the same instance of the list.

try:
```

a = [ ['a'] ] * 40
a[0].append('b')

```
and you will se what I mean. ;)

---

### Post by pmasiar on 2007-10-24
Yes, there is reason to predefine size. Look what I mean:

[php]
>>> ll = [1] * 40
>>> ll[30]
1
>>> ll[50]

Traceback (most recent call last):
  File "<pyshell#5>", line 1, in -toplevel-
    ll[50]
IndexError: list index out of range
[/php]

You can expand list, but it does not happen automagically. Reaching beyond current list limits is fortunately an error.

---

### Post by dwblas on 2007-10-24
For future reference, the code you posted could use either of the following```
test_1 = []                                                                     
test_2 = []
for j in range(10):
   test_1 += [0]
   test_2.append( 0 )                                                           

##---  change some elements to verify that they are unique
test_1[1] = 1
test_1[3] = 3
print test_1
test_2[2] = 2
test_2[4] = 4
print test_2

##--- you can also use
test_3 = [0] * 10
test_3[5] = 5
test_3[6] = 6
print test_3
```

---

### Post by Smygis on 2007-10-24
> **amiga_os said:**
> Hi, sorry for the dumb question:

In c I can define an array like this:

```
int mylist[40]
```

That will give me 40 blank variables to work with.  How do I do that in Python?  From the docs - and maybe I missed something - I have to do this:

```
mylist = [range(40)]
for i in range(40):
[INDENT]mylist[i] = 0[/INDENT]
```

Python seems so tidy... there must be a better way of doing this.  Can anyone help?

```
myList = [0 for i in xrange(40)]
```

:popcorn:

---

### Post by thumper on 2007-10-24
My question would be different.

Why do you think you need a list with 40 zeros in it?

---

### Post by pmasiar on 2007-10-25
To allocate space for 40 elements?

---

### Post by ankursethi on 2007-10-25
Yes, but can't elements be added to the list as the need arises? I think this question could be solved better in context of the problem.

Anyway, I suppose list comprehensions are the way to go.
myList = [0 for i in range(40)]
(Is there a better way to do this?)

---

### Post by pmasiar on 2007-10-25
> **ankursethi said:**
> (Is there a better way to do this?)

I like much more above mentioned my_list = [0] * 40. Less fluff IMHO :-)

---

### Post by hecato on 2007-10-25
Should I ask if there exist a performance difference?? (blame me :P)

```
[0] * 40
[0,0] * 20
[0,0,0,0] * 10
[0,0,0,0,0]*10
```
OK the last is my fail I dont remember 5*?=40... o yes
```
[0,0,0,0,0]*8
```

---

### Post by pmasiar on 2007-10-25
Why would anyone using Python bothered with possible (and negligible) difference between [0] * 40 and [0,0] * 20? My first reaction was: first option is more obvious, so, preferable.

---

### Post by nanotube on 2007-10-26
> **pmasiar said:**
> To allocate space for 40 elements?

to allocate space for 40 elements, why not just
```
mylist = range(40)
```
allocating space doesn't necessitate setting elements to 0...

---

### Post by pmasiar on 2007-10-26
IMHO OP wanted also to initialize values in list to 0. Maybe not :-/

---

