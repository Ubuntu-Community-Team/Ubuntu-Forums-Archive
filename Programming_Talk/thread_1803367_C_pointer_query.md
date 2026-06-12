---
title: "C pointer query"
date: 2011-07-13
forum: Programming Talk
---

### Post by Grenage on 2011-07-13
I've started looking at C simply for dabbling with during downtime, but I've hit a bit of a snag when it comes to understanding pointers.  I'm hoping that someone here might be able to correct my interpretation.

```
int *p
int x
```

Now by my understanding, *p* contains the memory address of whatever it's pointing to, and **p* references the data stored within that memory address.  *x* is a simple variable, and *&x* would return the memory address of x.

```
p = &x;
scanf( "%d", &x );
printf( "%d\n", *p );
```

The second line is what I'm having trouble understanding; why is it *&x* rather than *x*?  Surely doing it this way would be changing the memory address of *x*, rather than its contents.  Obviously it does not, but I don't quite see why.

---

### Post by slavik on 2011-07-13
scanf takes the address, not the value of the variable.

---

### Post by Bachstelze on 2011-07-13
To elaborate: if scanf took the actual variable as parameter, it would not be able to modify it, because it would receive a copy of it. In C, all function parameters are passed by value, meaning that calling f(x) when x has a value of 5 is strictly equivalent to calling f(5). Since obviously it is impossible to change the value of 5 in the second example, it follows that it is also impossible to change the value of x in the first.

So what you do is calling f(&x). Then f can change the value of whatever is at address &x. It cannot change the address but that's fine, we don't need it to. You should read more about this, it is crucial that you understand it if you want to do C. [http://en.wikipedia.org/wiki/Evaluation_strategy](http://en.wikipedia.org/wiki/Evaluation_strategy)

---

### Post by Grenage on 2011-07-13
That's great, thank you both; especially for the elaboration.  I think I understand what you're saying, but I'll have a read just to make sure.

---

