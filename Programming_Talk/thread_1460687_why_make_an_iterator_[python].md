---
title: "why make an iterator? [python]"
date: 2010-04-23
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-04-23
```

myterator = iter([111, 667, 73])
for item in myterator:
    print item

```

does the exact same thing as 

```

triterator = [111,667,73]
for item in triterator:
    print item

```

So why would I want to use the first one?

---

### Post by Bachstelze on 2010-04-23
You don't. You want to use an iterator if you need to add iteration support to a custom class.

---

### Post by OgreProgrammer on 2010-04-23
Ah, I see. 

Like a new type of list, dist, tuple or set. 

That makes sense. I am no where near doing that!

Thanks.

---

### Post by Bachstelze on 2010-04-23
Quick example. Of course it's way overkill to use a class for this, but it shows the concept:

```
firas@momiji ~ % cat geom.py
class GeometricSequence(object):

    def __init__(self, first_term=1, ratio=2):
        self.first_term = first_term
        self.ratio = ratio
        self.iterator = GeomSequenceIterator(self.first_term, self.ratio)

    def __iter__(self):
        return self.iterator


class GeomSequenceIterator(object):

    def __init__(self, first_term, ratio):
        self.first_term = first_term
        self.ratio = ratio
        self.current_term = self.first_term

    def __iter__(self):
        return self

    def __next__(self):
        old_term = self.current_term
        self.current_term *= self.ratio
        return old_term

myseq = GeometricSequence(2, 3)

# Print all the terms strictly less than 100
for i in myseq:
    if i >= 100:
        break
    print(i)

firas@momiji ~ % python3 geom.py
2
6
18
54

```

---

### Post by Bachstelze on 2010-04-23
> **OgreProgrammer said:**
> 
Like a new type of list, dist, tuple or set. 


More like if you want to add iteration support to a class that normally doesn't support it, like a thread or a socket, or if you want to create a brand new class that supports iteration. If what you want is just an improved list with additional methods, you can just make your class inherit from the list class, which already supports iteration, so you won't need to implement it yourself.

---

### Post by OgreProgrammer on 2010-04-23
Oh ok. That makes good sense. 

For such a simple thing I appreciate you taking time to show me an example. Thanks again.

---

