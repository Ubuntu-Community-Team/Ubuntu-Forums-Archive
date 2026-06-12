---
title: "Arrays and Pointers - C++"
date: 2012-11-17
forum: Programming Talk
---

### Post by dep0 on 2012-11-17
Is it valid to say in c/c++ that the name of an array is a pointer?
I already know that this is valid 
```
int c[10];
&c[0]==c;
```From this can i assume that the name of an array is a pointer?

---

### Post by Vaphell on 2012-11-17
in some context it behaves like one, but not always
check the difference between *sizeof(c)* and *sizeof(&c[0])*

---

### Post by Bachstelze on 2012-11-17
> **dep0 said:**
> Is it valid to say in c/c++ that the name of an array is a pointer?


Make up your mind, C or C++? In C, no. In C++, I don't know.

---

### Post by MadCow108 on 2012-11-17
> **dep0 said:**
> Is it valid to say in c/c++ that the name of an array is a pointer?
I already know that this is valid 
```
int c[10];
&c[0]==c;
```From this can i assume that the name of an array is a pointer?

arrays and pointers are different types. But both types represent a very similar concept, except arrays have the additional notion of the size of memory pointed to.
It is very important to remember that arrays decays into a pointer on a change of stack frame.
That means as soon as you are in a different frame the size information is lost
e.g. 

```

main()
{
  int c[10]
  assert(sizeof(c == sizeof(int) * 10));
  f(c);
}

f(int a[])
{
  assert(sizeof(a == sizeof(int*)));
  // a is now a pointer to the array in the previous stack frame!!
  // [] syntax here is just "syntactic sugar", int * a is the exact same thing
}

```

---

### Post by trent.josephsen on 2012-11-18
> **MadCow108 said:**
> 
```

  assert(sizeof(c == sizeof(int) * 10));

  assert(sizeof(a == sizeof(int*)));

```

Careless mistake, I'm sure, but both of those evaluate to assert(sizeof(int)). Actually maybe in C++ it's sizeof(bool)... correct me if I'm wrong.

---

