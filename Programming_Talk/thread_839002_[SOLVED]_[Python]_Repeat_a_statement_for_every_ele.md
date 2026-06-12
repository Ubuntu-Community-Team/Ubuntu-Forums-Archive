---
title: "[SOLVED] [Python] Repeat a statement for every element in a list"
date: 2008-06-24
forum: Programming Talk
---

### Post by -grubby on 2008-06-24
I was wondering, is there a way to detect every element in a list and then run statements for each element? Case in point: In my IRC bot, the channels to join on startup are in a list. However, I have to use the join(chan[#]) for each channel manually. I'd like to be able for ti to autodetect every element in the list and then run a statement on it. If you need more clarification, I'd gladly post it

---

### Post by Phenax on 2008-06-24
Don't know if this is what you're asking for (or if it's the best way in Python):

[php]
for i in range(0, len(chan)):
  join(chan[i])
[/php]

---

### Post by -grubby on 2008-06-24
Thank you very much. That worked. Howver, I discovered a different method:

[php]
for chan in chan :
    join(chan) 
[/php]

Thanks anyways!

---

### Post by LaRoza on 2008-06-24
Some more ways:

```

>>> me = [2,3,4]
>>> you = [x * x for x in me]
>>> print you
[4, 9, 16]
>>> 

>>> def square(x):
...     return x * x
... 
>>> you = map(square,me)
>>> print you
[4, 9, 16]
>>> 

```

```

for i in chan :
    join(i) 
#OR
map(join,chan)

```

---

