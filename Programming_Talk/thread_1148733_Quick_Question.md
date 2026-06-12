---
title: "Quick Question"
date: 2009-05-04
forum: Programming Talk
---

### Post by Ohmaley on 2009-05-04
What function or coding should I use if I wanted to pull out the number of times an element appears in a liste and [COLOR=Red]each[/COLOR] of its emplacments?

lets say i have this:

Liste= ['a','p','p','l','e']

x = raw_input('what letters to search?: ')  #i type in 'p'

Liste.count(x) = 2

Liste.index(x) = 1   # only shows me first emplacement, but i want both?

thanks for your interest!

---

### Post by kestrel1 on 2009-05-04
Is this using Calc?

---

### Post by simeon87 on 2009-05-04
I haven't found a standard function but I guess you could use:

```

for i, v in enumerate([1,1,2,3]):
    if v == 1:
        print "index", i

```

---

### Post by Ohmaley on 2009-05-04
What do you mean by Calc?

simeon87, I'm having a hard time getting your coding to work. it simply reads index 1 each time

---

### Post by Can+~ on 2009-05-04
This looks like a job for YIELD!

[PHP]def repetitions(liste, match):
    for count,element in enumerate(liste):
        if element == match:
            yield count

for index in repetitions("apple", 'p'):
    print index,[/PHP]

It will work with any iterable type, as long as you match it with the right type.

And I don't know why you're using a [ list ] of 'c'haracters, when that's pretty much a "string".

---

### Post by Ohmaley on 2009-05-04
works wonder

---

### Post by kestrel1 on 2009-05-04
> **Ohmaley said:**
> What do you mean by Calc?

simeon87, I'm having a hard time getting your coding to work. it simply reads index 1 each time
Sorry, just noticed the forum we are in. Silly me. Forget I was even here :)

---

### Post by Can+~ on 2009-05-04
> **kestrel1 said:**
> Sorry, just noticed the forum we are in. Silly me. Forget I was even here :)

You sacrilegious, how dare you doubt the power of the all seeing python? Your punishment will be for whip in xrange(10).

:lolflag:

---

### Post by CptPicard on 2009-05-04
```

sum([1 for x in "apple" if x == 'p'])

len([x for x in "apple" if x == 'p'])

```

---

### Post by benj1 on 2009-05-04
> **Can+~ said:**
> You sacrilegious, how dare you doubt the power of the all seeing python? Your punishment will be for whip in xrange(10).

:lolflag:

unless its python 3:)

---

### Post by kestrel1 on 2009-05-05
> **benj1 said:**
> unless its python 3:)
I can feel the python constricting as I type :lolflag:

---

