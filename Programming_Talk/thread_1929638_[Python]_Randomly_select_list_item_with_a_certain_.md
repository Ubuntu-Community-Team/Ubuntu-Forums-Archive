---
title: "[Python] Randomly select list item with a certain probability"
date: 2012-02-22
forum: Programming Talk
---

### Post by blazemore on 2012-02-22
I can't seem to get my head round this, although I'm sure it's fairly simple.

I have a list of tuples like this: (c, p) where p is a number between 0 and 1.

I need to return an item from this list, where an item's chance of being selected is equal to p.

So if I had a list like this:
[
(a, 0.1)
(b, 0.5)
(c, 0.5)
]

it could return any of them, but b and c are equally likely, and 5 times more likely than a.

Sorry if I haven't explained this very well.

For context, this is part of a genetic algorithm I am writing.

---

### Post by Bachstelze on 2012-02-22
Th

---

### Post by blazemore on 2012-02-22
> **Bachstelze said:**
> Th

Thanks, that fixed it.

;)

---

### Post by Bachstelze on 2012-02-22
```
firas@av104151 ~ % cat prob.py 
import random

l = [('a', 1), ('b', 5), ('c', 5)]

def randitem(l):

    # Make the probabilities add up to 1, preserving ratios
    s = sum([b for (a,b) in l])
    l2 = []
    for (a,b) in l:
        l2.append((a, b/s))

    r = random.random()
    for (a,b) in l2:
        if r < b:
            return a
        else:
            r -= b

# test
res = {'a':0, 'b':0, 'c':0}
for i in range(10000):
    res[randitem(l)] += 1

print('a: %s (%s%%)' % (res['a'], res['a']/100))
print('b: %s (%s%%)' % (res['b'], res['b']/100))
print('c: %s (%s%%)' % (res['c'], res['c']/100))

firas@av104151 ~ % python3 prob.py 
a: 895 (8.95%)
b: 4521 (45.21%)
c: 4584 (45.84%)

```

---

### Post by Bachstelze on 2012-02-22
Just in case it wasn't clear the first time. ;)

---

### Post by surfer on 2012-02-22
a different approach; i do not normalize the probabilities to 1 (which would probably be the better idea...). this is not well tested!

```
#!/usr/bin/python


import random


class RandomChoice(object):
    '''
    '''
    
    def __init__(self, lst):
        '''
        lst: the list in the form [ (element, relative_probability) ]
        '''
        
        self.lst = lst
        
        self.limits = []
        p_sum = 0
        for item in lst:
            p_sum += item[1]
            self.limits.append(p_sum)
        print self.limits
        self.p_max = p_sum
        
        
    def _get_index(self, rnd):
        '''
        Given the radnom number rnd (0<=rnd<p_max), return the list index.
        '''
        last = 0.0
        for (i, p) in enumerate(self.limits):
            if last <= rnd < p:
                return i
            last = p

    def get(self):
        '''
        '''
        rnd = random.uniform(0, self.p_max)
        i   = self._get_index(rnd)
        return self.lst[i]




# test:

lst = [
('a', 0.1),
('b', 0.5),
('c', 0.5)
]

rc = RandomChoice(lst)

for i in xrange(100):
    print rc.get()

```


and, yes 'Th' is much more concise!

---

