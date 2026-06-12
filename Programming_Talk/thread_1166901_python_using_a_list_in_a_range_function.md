---
title: "python: using a list in a range function"
date: 2009-05-22
forum: Programming Talk
---

### Post by benj1 on 2009-05-22
ok from what i know of lists this may be impossible, but it just seems like the sort of thing you should be able to do.

this is essentially what id like to do:-

```
arg='1:5'
for entries in range(map(int, arg.split(':'))):
    print entries
```

except you can't use a list for a range.

i know i can do:-

```
arg='1:5'
a, b = map(int, arg.split(':'))
for entries in range(a,b):
    print entries
```

but hey call me a perfectionist.

any ideas???

---

### Post by smartbei on 2009-05-22
How about forgoing the range?
```

for entries in map(int, arg.split(':')):
    print entries

```
Should work great :-).

EDIT: Sorry. re-read your post and got what you meant.

Here is what you want:
```

arg='1:5'
for entries in range(*map(int, arg.split(':'))):
    print entries

```
Notice the asterisk? What it tells python is to expand the list and treat it as arguments to the function.

---

### Post by sujoy on 2009-05-22
> except you can't use a list for a range.

well you can iterate over a list directly.
```
for number in numbers:
    # so stuff
```

but really though, i didnt quite get what you are trying to accomplish here

---

### Post by smartbei on 2009-05-22
I didn't at first either - see my post above though for the solution... :-)

---

### Post by sujoy on 2009-05-22
> **smartbei said:**
> I didn't at first either - see my post above though for the solution... :-)

ah yes, i missed the point completely ):P

---

### Post by benj1 on 2009-05-22
> **smartbei said:**
> How about forgoing the range?
```

for entries in map(int, arg.split(':')):
    print entries

```
Should work great :-).

EDIT: Sorry. re-read your post and got what you meant.

Here is what you want:
```

arg='1:5'
for entries in range(*map(int, arg.split(':'))):
    print entries

```
Notice the asterisk? What it tells python is to expand the list and treat it as arguments to the function.

cool that works thanks

@ sujoy 
that wouldn't work, it would just print entries 1 & 5, where i want 1,2,3,4,5

---

### Post by benj1 on 2009-05-22
just out of curiosity is there any documentation for what else '*' does.

google isn't being helpful.

---

### Post by unutbu on 2009-05-22
I think the critical fact regarding * and ** is this:
Whenever you see *args, it implies args had better be a tuple or list.
Whenever you see **kwargs, kwargs had better be a dict.

Old-style python has a built-in function called apply ([http://pyref.infogami.com/apply](http://pyref.infogami.com/apply))
so that you could call a function with arbitary arguments like this:
```

apply(function, args, keywords)
```

where args is a list and keywords is a dictionary.

For example,
```

apply(function, [1,2,3], {'verbose':True})
```

is equivalent to
```

function(1,2,3,verbose=True)
```

New-style python uses * and ** instead:
```

function(*[1,2,3],**{'verbose':True}) 
```

is also equivalent to 
```

function(1,2,3,verbose=True)
```

Here is some demonstration code:
[PHP]
#!/usr/bin/env python
def f(*a):
   print a
# (1, 2, 3)
   print type(a)
# <type 'tuple'>
f(1, 2, 3)

def g(**a):
   print a
# {'y': 2, 'x': 1, 'z': 3}
   print type(a)
# <type 'dict'>
g(x=1, y=2, z=3)

def h(*largs,**kwargs):
   print largs
# ()
   print kwargs
# {'debug': False}
h(debug=False)

matrix=[[1,2,3],[4,5,6],[7,8,9]]
print(matrix)
# [[1, 2, 3], 
#  [4, 5, 6], 
#  [7, 8, 9]]

# The * can be used to transpose a matrix!
print(zip(*matrix))
# [(1, 4, 7), 
#  (2, 5, 8), 
#  (3, 6, 9)]

[/PHP]

You can find some "official" documentation on the * and ** here:
[http://docs.python.org/reference/expressions.html#calls](http://docs.python.org/reference/expressions.html#calls)
[http://docs.python.org/tutorial/controlflow.html#more-on-defining-functions](http://docs.python.org/tutorial/controlflow.html#more-on-defining-functions)

---

### Post by benj1 on 2009-05-22
thankyou, thats great:)

---

