---
title: "C++: Looking for efficient way to zero-out integer vector or array"
date: 2008-02-20
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-02-20
I need to create either an array of constant size dynamically or use a vector to hold some data used by a function in my C++ program.  I plan to make the vector or array a class variable so that I only have to allocate it once per program load (performance matters).  Is there a way to get a vector of integers all initialized to 0 besides declaring the vector and calling a function to set each index to 0 manually?  I am thinking that there must be some built-in performance-optimized routine similar to the copy? function in Java to do this.  I am already using the Boost template library so maybe there is a function in there for this, although I did not see it.  The zero-vector container does not actually hold anything so that's not what I am looking for.

---

### Post by dwhitney67 on 2008-02-20
For an array, you can choose to use either of these methods:

[PHP]int array[100] = { 0 };[/PHP]

or

[PHP]int array[100];
memset( array, 0, sizeof array );[/PHP]

I'm not sure what you are asking about concerning the vector.  Please elaborate more and perhaps I can help.

---

### Post by Lux Perpetua on 2008-02-20
One of the vector constructors lets you specify the initial value of its elements, which you can use to initialize everything to zero. (See here: [http://www.cppreference.com/cppvector/vector_constructors.html](http://www.cppreference.com/cppvector/vector_constructors.html), the third constructor.) I would expect that constructor to be optimized as much as possible.

---

### Post by Jucato on 2008-02-20
I thought that by default, all elements of a vector are set to 0. At least that's what my C++ told me (Deitel & Deitel, C++ How to Program 5th ed.)

---

### Post by pedro_orange on 2008-02-20
> **Jucato said:**
> I thought that by default, all elements of a vector are set to 0. At least that's what my C++ told me (Deitel & Deitel, C++ How to Program 5th ed.)

This is correct. Build yourself a test program to prove said theory.

---

