---
title: "[Python]TypeError: unhashable type: 'list'"
date: 2011-05-30
forum: Programming Talk
---

### Post by juancarlospaco on 2011-05-30
v is wind speed int()
i got this:

```
    if v < 1:
        mar = "Calma"
    elif v < 5:
        mar = "Olas chicas, sin espuma"
    elif v < 11:
        mar = "Crestas de ola, sin romper"
    elif v < 19:
        mar = "Olas chicas, crestas rompientes."
    elif v < 19:
        mar = "Olas medianas, crestas rompientes."
    elif v < 28:
        mar = "Olas grandes, crestas rompientes."
    elif v < 49:
        mar = "Olas grandes rompientes, con poca espuma."
    elif v < 61:
        mar = "Olas grandes rompientes con mucha espuma."
    elif v < 74:
        mar = "Olas muy grandes rompientes con mucha espuma."
    elif v < 88:
        mar = "Olas gigantes rompientes con mucha espuma."
    elif v < 102:
        mar = "Olas gigantes rompientes, visibilidad reducida"
    elif v > 103:
        mar = "Olas enormes rompientes, visibilidad casi nula!"
    else:
        mar = "?"
    print mar

```

I want to make it more elegant, more one-liner, 
consider those are range of numbers, ignore the strings, so i try:

```
    dict =  {range(0, 1): "Calma", range(1, 5): "Olas chicas, sin espuma", range(5, 11): "Crestas de ola, sin romper" }
    mar = dict[v]
    print mar
```

but it gives the Error:

```
TypeError: unhashable type: 'list'
```

Any Help ?

---

### Post by StephenF on 2011-05-30
Dictionary keys can't be mutable objects.

The alternative constructor dict.fromkeys will allow you to have multiple keys with the same target.

```

class WindDict(dict):
    def __init__(self, seq):
        for keys, target in seq:
            d = dict.fromkeys(keys, target)
            self.update(d)

            
    def __getitem__(self, i):
        if i > 103:
            return "Olas enormes rompientes, visibilidad casi nula!"
        else:
            try:
                return dict.__getitem__(self, i)
            except KeyError:
                return "?"

            
w = WindDict(((range(0, 1), "Calma"),
              (range(1, 5), "Olas chicas, sin espuma"),
              (range(5, 11), "Crestas de ola, sin romper")))

              
print w[4]

```

---

### Post by TwoEars on 2011-05-30
Well, the clue is in the traceback, as always. The range function returns a list - lists can't be made hashable (unique items to act as the index in your dict), for example -

```

>>> dict = {[3,3]:"hi"}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'

```

Now, why isn't this allowed? It's because lists are mutable - that means they can be changed. Let's say I have -
```

list_1 = [1]
list_2 = [1,2]

```
Then let us say that the following is okay syntax -
```

dict = {list_1: "Hi number 1!", list_2: "Hi number 2!"}

```

What would then happen if I ran 
```

list_1.append(2)

```
? The dict would go insane; if I gave [1,2] as an input, what would happen? Does it return "Hi number 1!", or "Hi number 2!"?

Instead, use the dict() function on a list of tuples where the tuple is of format (key, value), for example - 
```
>>> statement_list = []
>>> for x in range(11):
...     if x < 1:
...             statement_list.append((x, "Calma"))
...     elif x < 5:
...             statement_list.append((x, "Olas chicas, sin espuma"))
...     else:
...             statement_list.append((x, "Crestas de ola, sin romper"))
...
>>> statement_list
[(0, 'Calma'), (1, 'Olas chicas, sin espuma'), (2, 'Olas chicas, sin espuma'), (3, 'Olas chicas, sin espuma'), (4, 'Olas
 chicas, sin espuma'), (5, 'Crestas de ola, sin romper'), (6, 'Crestas de ola, sin romper'), (7, 'Crestas de ola, sin ro
mper'), (8, 'Crestas de ola, sin romper'), (9, 'Crestas de ola, sin romper'), (10, 'Crestas de ola, sin romper')]
>>> statement_dict = dict(statement_list)
>>> statement_dict
{0: 'Calma', 1: 'Olas chicas, sin espuma', 2: 'Olas chicas, sin espuma', 3: 'Olas chicas, sin espuma', 4: 'Olas chicas,
sin espuma', 5: 'Crestas de ola, sin romper', 6: 'Crestas de ola, sin romper', 7: 'Crestas de ola, sin romper', 8: 'Cres
tas de ola, sin romper', 9: 'Crestas de ola, sin romper', 10: 'Crestas de ola, sin romper'}

```

This isn't much nicer, I admit. So, what can we do instead? Well, how about this - we test if given variable x is smaller than the dict key, for example -

```

>>> statement_dict = dict([(1,"Calma"), (5,"Olas chicas, sin espuma"), (11,"Crestas de ola, sin romper")])
>>> statement_dict
{1: 'Calma', 11: 'Crestas de ola, sin romper', 5: 'Olas chicas, sin espuma'}
>>> for x in xrange(11):
...     for key in sorted(statement_dict.keys()):
...             # use sorted to ensure smallest first
...             if x < key:
...                     print statement_dict[key]
...                     break
...
Calma
Olas chicas, sin espuma
Olas chicas, sin espuma
Olas chicas, sin espuma
Olas chicas, sin espuma
Crestas de ola, sin romper
Crestas de ola, sin romper
Crestas de ola, sin romper
Crestas de ola, sin romper
Crestas de ola, sin romper
Crestas de ola, sin romper

```

I hope this helps.

---

### Post by juancarlospaco on 2011-05-30
> **StephenF said:**
> Dictionary keys can't be mutable objects.

The alternative constructor dict.fromkeys will allow you to have multiple keys with the same target.

```

class WindDict(dict):
    def __init__(self, seq):
        for keys, target in seq:
            d = dict.fromkeys(keys, target)
            self.update(d)

            
    def __getitem__(self, i):
        if i > 103:
            return "Olas enormes rompientes, visibilidad casi nula!"
        else:
            try:
                return dict.__getitem__(self, i)
            except KeyError:
                return "?"

            
w = WindDict(((range(0, 1), "Calma"),
              (range(1, 5), "Olas chicas, sin espuma"),
              (range(5, 11), "Crestas de ola, sin romper")))

              
print w[4]

```

This one is the only that has worked for me, thank you very much!!   &#664;&#8255;&#664;

So i make a windict.py module and in the Main app:

```

import windict

mar = w[v]
print mar

```

---

