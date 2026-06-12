---
title: "[C++] Dynamic Array reference"
date: 2010-03-03
forum: Programming Talk
---

### Post by blooddrunk on 2010-03-03
Hi! I've got a questions about C++. How does one pass a dynamic array to functions by reference so that it can be manipulated? 10x

---

### Post by MadCow108 on 2010-03-03
in case dynamic array = vector
just add the & operator to the function declaration. This means pass by reference.

int func(vector<type> & vec)

or (less recommended) pass a pointer to the vector
int func(vector<type> * vec)

in case its a c style array (not recommended):
they are decay into pointers when passed to a function. And pointers are a kind of reference.
Just make sure to also have a way to determine the size of the array, as sizeof won"t work anymore

---

### Post by blooddrunk on 2010-03-03
Thanks you

---

