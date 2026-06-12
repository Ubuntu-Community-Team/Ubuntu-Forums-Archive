---
title: "Efficient Distance Formula"
date: 2009-05-09
forum: Programming Talk
---

### Post by unready%20cincinnatus on 2009-05-09
I ran into a black box java method that computes the square of the distance between two points about 33% faster than 

```
int dist = (x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2);
```

Does anyone have any idea of what the implementation might be?  Or where I could start looking for efficient algorithms?

---

### Post by Arndt on 2009-05-09
> **unready%20cincinnatus said:**
> I ran into a black box java method that computes the square of the distance between two points about 33% faster than 

```
int dist = (x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2);
```

Does anyone have any idea of what the implementation might be?  Or where I could start looking for efficient algorithms?

Perhaps doing

```
int d1 = x1-x2;
int d2 = y1-y2;
int dist = d1*d1 + d2*d2;

```
is faster?

---

### Post by MeLight on 2009-05-09
have you tried:

[PHP]int dx = (x1 - x2);
int dy = (y1 - y2);
double dist = sqrt(dx*dx + dy*dy);[/PHP]

That way you only calculate the deltas once and not twice, although I'm not sure it's such a great improvement

---

### Post by gmatt on 2009-05-09
> **unready%20cincinnatus said:**
> I ran into a black box java method that computes the square of the distance between two points about 33% faster than 

```
int dist = (x1 - x2) * (x1 - x2) + (y1 - y2) * (y1 - y2);
```

Does anyone have any idea of what the implementation might be?  Or where I could start looking for efficient algorithms?

If you want to optimize this by hand then do what the previous two posts suggested, with calculating the deltas just once. 

You can also try the equivalent formula 

```

int dist = x1*x1 -2*x1*x2 +x2*x2 + y1*y1-2*y1*y2+y2*y2;

```

but because most processors can compute addition faster than multiplication, this will almost surely run slower. The only way that this formula would run faster if x1-x2 and y1-y2 are very very large.

If that doesn't work you can insert Assembly code that will compute this and greatly improve the performance. The performance gain for this 1 line of code can go up anywhere from 10%-90%. C/C++ is notoriously bad  at optimizing multiplications/divisions/mods. If you look at high performance code, most of that code uses >> and << shift operators to multiply and divide, since the C compiler almost never finds these optimizations.

---

### Post by hessiess on 2009-05-09
I came across a interesting implementation of square root which was used in Quake-3 which is suppose to be faster, see [http://www.codemaestro.com/reviews/9](http://www.codemaestro.com/reviews/9).

---

### Post by unready%20cincinnatus on 2009-05-11
Thanks to everyone who replied.  Precomputing the differences helped quite a bit, and I might look to try the bitwise modifications if the opportunity presents itself.  

I have to say, I was expecting there'd be some academic research into something like this.  Wasn't expecting the Quake III engine to be the state of the art in the field.

---

### Post by gmatt on 2009-05-12
> **unready%20cincinnatus said:**
> Thanks to everyone who replied.  Precomputing the differences helped quite a bit, and I might look to try the bitwise modifications if the opportunity presents itself.  

I have to say, I was expecting there'd be some academic research into something like this.  Wasn't expecting the Quake III engine to be the state of the art in the field.

Actually, what the Quake engine uses is whats called Newton's method which was discovered by Sir Isaac Newtown in 1669. So I think he beats the Quake Engine to the punch by a few years ;) 

The fact is, Academic research strives to research general problems, whereas this is simply a practical problem. Not to downplay its importance. Almost all useful research stems from a practical question, and evolves over time into general theories. Take for example the Fast Fourier Transform. Cooley-Turkey take credit for what computer scientists affectionately call the FFT, but in reality it was first discovered by Gauss who was a great mathematician and used this same algorithm so that he could speed up his calculations by hand! Gauss was motivated by the practical question of being able to accurately predict the positions of stars in the sky at some time in the future, which was itself motivated by sailors who needed to be able to use stars to navigate the open oceans. Indeed, I hope you can see how a practical question can lead to invaluable research.

I was also going to suggest Newton's method to you, but since you wanted to compute the squared distance Newton's method would not provide much of a speed up (Newton's method computes the square root, it is an iterative method that converges quadratically; you learn Newton's method in any first year calc course and you learn it in more detail if you care to study scientifc (numeric) computing, which is an extremely useful field, and almost entirely mathematical.)

---

