---
title: "[Python] Shorten Conditions"
date: 2008-06-11
forum: Programming Talk
---

### Post by regomodo on 2008-06-11
`

---

### Post by nvteighen on 2008-06-11
The condition, in a shorter notation, is:

if ((a == p) && (a == q))

So, you can reduce it to if(p == q), as it's the only way that "a" can meet both conditions simultaneously.

---

### Post by imdano on 2008-06-11
What if (p == q) but (p != a)?

---

### Post by nvteighen on 2008-06-11
> **imdano said:**
> What if (p == q) but (p != a)?
Then (a != q) also, and the if-block is not executed.

---

### Post by imdano on 2008-06-11
I must not be understanding what you want him to do.  If you change the if statement to just "if (p == q)", how are you determining if p/q are also equal to a?  If a = 6, p = 7, and q = 7, the reduced if statement is true but the result wouldn't match original one.

edit: I think in python you can do ```
if a == b == c:
```Is that what you mean?

---

### Post by dmm1285 on 2008-06-11
try this:
```

if (abs(pos[0][0] - pos[1][0]) == (abs(pos[3][0] - pos[2][0])) and abs(pos[2][1] - pos[1][1]))):
```

---

### Post by imdano on 2008-06-11
> **dmm1285 said:**
> try this:
```

if (abs(pos[0][0] - pos[1][0]) == (abs(pos[3][0] - pos[2][0])) and abs(pos[2][1] - pos[1][1]))):
```That will evaluate either to False, or the value of abs(pos[2][1] - pos[1][1]).  I think this will work though:
```
if abs(pos[0][0] - pos[1][0]) == abs(pos[3][0] - pos[2][0]) == abs(pos[2][1] - pos[1][1]):
```

---

### Post by molotov00 on 2008-06-11
You have:
if a ==b and a==c

Python DOES support
if a==b==c

...which is logically identical to what you have now. It'll be faster because Python doesn't have to calcuate 'a' twice ;)

Although your code looks complex, the actual logic is simple (and can't be made simpler). It's the method calls that make it look longer.

---

### Post by mike_g on 2008-06-11
> The condition, in a shorter notation, is:

if ((a == p) && (a == q))

So, you can reduce it to if(p == q), as it's the only way that "a" can meet both conditions simultaneously.
But then how do you know that 'a' equals either 'p' or 'q'? 
Edit: >_< just read the rest of the posts.

Personally I'd move some calculations out of the statement:
```
a = abs(pos[0][0] - pos[1][0])
p = abs(pos[3][0] - pos[2][0])
q = abs(pos[2][1] - pos[1][1])
if (a == p) and (a == q):
```

---

### Post by nvteighen on 2008-06-11
> **imdano said:**
> I must not be understanding what you want him to do.  If you change the if statement to just "if (p == q)", how are you determining if p/q are also equal to a?  If a = 6, p = 7, and q = 7, the reduced if statement is true but the result wouldn't match original one.

> **mike_g said:**
> But then how do you know that 'a' equals either 'p' or 'q'? 
Edit: >_< just read the rest of the posts.


Shame on me! Excuse today's horrible performance of mine :oops:

---

### Post by regomodo on 2008-06-11
`

---

### Post by Can+~ on 2008-06-11
You're using something[n][a], and I'm guessing the [a] is either X or Y, right?

Why don't implement a coordinate class?

[PHP]class Shape:
    x = 0
    y = 0

    def something(self):
        pass

class Rectangle(Shape):
    pass[/PHP]

So now, every object holds their x and y. This approach also makes each object able to calculate something related as a method, or make all shapes have a certain property.

---

### Post by regomodo on 2008-06-11
`

---

### Post by regomodo on 2008-06-13
`

---

### Post by matja on 2008-06-13
> **regomodo said:**
> I've finished my masters!!!

Congratulations!

---

