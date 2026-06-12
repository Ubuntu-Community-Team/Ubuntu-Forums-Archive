---
title: "An idea for matrix on C++"
date: 2009-02-10
forum: Programming Talk
---

### Post by Benzaa on 2009-02-10
Hi,

Im creating a matrix class, well actually Im copying one that I found. Just changing some of the things that I dont like and adding some features that I will need.

Like overloading the operator () so I can have access to an element of the matrix, something like this:

A(1,2);

But now, I was wondering, how could I overload the operator = to set the value of an element in the matrix, something like this:

A(1,2) = 3;

Any ideas?

---

### Post by geirha on 2009-02-10
Just make the () operator return a reference& to the value in the matrix, then A(1,2)= 3; will automagically work. :)
```
T& matrix::operator() (int row, int col){
    ...
```

---

### Post by Benzaa on 2009-02-10
Thanks gierha,

Actually I thought about that just after writing the post :D

I just need to create a double reference for the function ()

T& matrix::operator ()(unsigned, unsigned);        (1)
T matrix::operator ()(unsigned, unsigned) const;   (2)


But again, thanks for the fast reply.

---

### Post by dribeas on 2009-02-10
> **Benzaa said:**
> Thanks gierha,

Actually I thought about that just after writing the post :D

I just need to create a double reference for the function ()

T& matrix::operator ()(unsigned, unsigned);        (1)
T matrix::operator ()(unsigned, unsigned) const;   (2)


But again, thanks for the fast reply.

Note that at any rate, that has nothing to do with the operator=. operator= would be for assigning a value to the whole matrix (not that it makes too much sense).

---

### Post by WW on 2009-02-11
> **Benzaa said:**
> 

Im creating a matrix class, well actually Im copying one that I found. Just changing some of the things that I dont like and adding some features that I will need.

You might find [Blitz++]("http://www.oonumerics.org/blitz/") interesting.

---

### Post by monkeyking on 2009-02-11
> **Benzaa said:**
> Hi,

Im creating a matrix class, well actually Im copying one that I found. Just changing some of the things that I dont like and adding some features that I will need.


Are you doing this to learn these things,
or do you just want something that works?

---

