---
title: "Copying arrays in Java"
date: 2009-11-11
forum: Programming Talk
---

### Post by dwally89 on 2009-11-11
Hi,

I have a two dimension array that stores objects.
How do I copy these objects over to a new array?

I want to copy the objects themselves, and not the references to the objects.

e.g. Say I have an array cardLocation[13][25], that is of type Card, and I want to copy all the objects of it over to an array tempArray[13][25], how would I do this?

Thanks

---

### Post by u2ix on 2009-11-11
you may use the clone() method.

```
tempArray[13][25] = cardLocation[13][25].clone();
```

so you create a equal object

---

### Post by dwally89 on 2009-11-11
Thanks.
I actually already knew about the clone method, but I just realised I didn't apply it in all the needed places.

Thanks again

---

### Post by Ruhe on 2009-11-11
Use **System.arraycopy**, Luke ;)

---

### Post by dwally89 on 2009-11-11
What's the difference between System.arraycopy and .clone()?

(.clone() seemed to work for me)

---

### Post by Ruhe on 2009-11-11
> **dwally89 said:**
> What's the difference between System.arraycopy and .clone()?

(.clone() seemed to work for me)

Interesting question.
I thought that array.clone() returns deep copy of array,
so if you clone array, which consists of cloneable elements, then all the elements will be cloned. 
But it seems, this is not true. Both methods just copy elements from one array to another.

Anyway it's useful to know about such method. 

By the way, System.arraycopy is used a lot in java.util.ArrayList

---

### Post by dwally89 on 2009-11-11
So what's the difference then?

---

### Post by 0cton on 2009-11-11
clone() is meant to make a copy of an object , note that you must do your own clone method for your own objects.
arraycopy() is a method that takes to arrays and copies the values from one to another, I imagine it is doing it for each index i am not sure :P

---

### Post by dwally89 on 2009-11-11
Hmm...

I used clone and it worked, even though I didn't make my own clone method...

---

### Post by Ruhe on 2009-11-11
[Checkout this]("http://java.sun.com/docs/books/jls/third_edition/html/arrays.html#10.7") section of java language specification. Look at the example with cloning array of integers.

This is what I was talking about.

PS: but it doesn't clone array of my own cloneable objects. I can't understand this.

---

