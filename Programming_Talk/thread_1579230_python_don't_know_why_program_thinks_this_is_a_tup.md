---
title: "python: don't know why program thinks this is a tuple"
date: 2010-09-21
forum: Programming Talk
---

### Post by daweefolk on 2010-09-21
I'm making a maze program. each room has a description to help you out. In order to track your room, I used this code to try and make a list to track the x/y position
```
x-and-y=[] #from what i read, creates an empty list
x-and-y=1,1 #then shouldn't this add 1 and 1 to the [0] and [1] values?
```
later on in the code, i try to edit the x-and-y[1] for when you go south
```
if userinput=="s":#user says south
  x-and-y[1]=x-and-y[1]-1#the value tracking y position SHOULD go down by one
```
when running the program, the output tells me 'tuple' object does not support item assignment
From what i read online, the code i used should have created a modifiable list, not a tuple.
I'm sure it's a stupid, simple solution, but what did I do wrong?

---

### Post by schauerlich on 2010-09-21
Python variables are dynamically typed. This means that just because you put a list in there initially, it does not mean it can't be changed to be something else. Python tuple literals such as '(a,b)' don't require parentheses except for precedence, so '1,1' creates a tuple (1,1) and assigns it to x-and-y. If you add brackets around the '1,1', you should get your desired result.

```
>>> foo = []
>>> foo = 1, 1
>>> foo
(1, 1)
>>> type(foo)
<type 'tuple'>
>>> foo = []
>>> foo = [1,1]
>>> foo
[1, 1]
>>> type(foo)
<type 'list'>

```

You can also use the append and insert methods of lists.

EDIT: you can also use tuple unpacking to get a similar result, if your list already has enough elements:

```
>>> foo = [None, None]
>>> foo[0], foo[1] = 1, 1
>>> foo
[1, 1]
```

But you probably don't need to worry about that right now...

---

### Post by Bachstelze on 2010-09-21
Also, it's a good idea to avoid hyphens in variable names. It works in Python, but not in other languages. Just use underscores.

---

### Post by daweefolk on 2010-09-21
Oh yeah, I completely forgot about python dynamically changing things. Looked at my code, at some point i had referenced it with parentheses rather than brackets. changed one line, tested the code included in said line, and it worked perfectly. 
heh then I realised I somehow messed up my north/south/east/west as I drew out the map in my head. it was rotated 90 degrees and flipped horizontally in the game. whoops.

---

### Post by schauerlich on 2010-09-21
> **Bachstelze said:**
> Also, it's a good idea to avoid hyphens in variable names. It works in Python, but not in other languages. Just use underscores.

I didn't even notice that... lisp is messing with my brain.

---

