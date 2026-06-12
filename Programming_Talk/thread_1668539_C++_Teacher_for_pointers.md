---
title: "C++ Teacher for pointers"
date: 2011-01-16
forum: Programming Talk
---

### Post by Pagn on 2011-01-16
Hello,
I have a question. Does anybody would like to teach me about pointers? Because that's where i was confuse. I've read many tutorial and books on pointers and still don't figure it out. If someone help me, i will reward them with 5 USD. 
 
Thanks in advance.

---

### Post by unknownPoster on 2011-01-16
[http://www.cplusplus.com/doc/tutorial/pointers/](http://www.cplusplus.com/doc/tutorial/pointers/)

The above is the best tutorial I've found online for tutorials. That being said, I feel the best way to learn is to practice. A fairly straight forward way to learn how to use pointers would be to implement a singly linked-list with insert, remove, and an "iterate" functions. By iterate I mean something that will allow you to step through the list and print the elements or some similar functionality.

---

### Post by unknownPoster on 2011-01-16
[http://www.cplusplus.com/doc/tutorial/pointers/](http://www.cplusplus.com/doc/tutorial/pointers/)

The above is the best tutorial I've found online for tutorials. That  being said, I feel the best way to learn is to practice. A fairly  straight forward way to learn how to use pointers would be to implement a  singly linked-list with insert, remove, and an "iterate" functions. By  iterate I mean something that will allow you to step through the list  and print the elements or some similar functionality.

---

### Post by worksofcraft on 2011-01-16
> **Pagn said:**
> Hello,
I have a question. Does anybody would like to teach me about pointers? Because that's where i was confuse. I've read many tutorial and books on pointers and still don't figure it out. If someone help me, i will reward them with 5 USD. 
 
Thanks in advance.

Lol... If those links don't work I'll help you for free.

To understand pointers you need to first know how computer memory is accessed: think of it as one big array of memory registers and each one has it's own numerical address that uniquely identifies that storage cell.

A pointer is simply one of those storage cells that contains the address of another storage cell: The one it is pointing to. A pointer can even point to it self.

What do you want to know next?

---

### Post by CptPicard on 2011-01-16
Typically, pointers also carry type information of the kind of data type that resides in the pointed-to memory address (or begins there to be more exact; the memory size required is known from how big the datatype in question is). So for example an int * is the memory address, beginning where there is an integer being stored.

Void pointers are the exception to this -- they carry no type information; you'll have to know what to "cast" them to in order to make use of them.

---

### Post by MadCow108 on 2011-01-16
> **CptPicard said:**
> Typically, pointers also carry type information of the kind of data type that resides in the pointed-to memory address (or begins there to be more exact; the memory size required is known from how big the datatype in question is). So for example an int * is the memory address, beginning where there is an integer being stored.

Void pointers are the exception to this -- they carry no type information; you'll have to know what to "cast" them to in order to make use of them.

to clarify this a bit:
a pointer itself does not carry any type information. It is just a number representing a memory address. You cannot determine the type of the data in the memory by examining the pointer alone.

The only difference in pointers of different "type" is their behaviour under addition and subtraction.
This behaviour is added by the compiler for pure convenience.

int *a;
a + 1;
is equivalent to
void * a;
a + sizeof(int);

---

### Post by CptPicard on 2011-01-16
Fair clarification; pointers of course do not, in the data sense, carry type information of the pointed-to memory location. But this of course holds for everything in C -- all types are just compile-time labels.

---

