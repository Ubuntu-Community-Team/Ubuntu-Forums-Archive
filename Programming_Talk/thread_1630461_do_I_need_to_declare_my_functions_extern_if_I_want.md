---
title: "do I need to declare my functions extern if I want them to be available to many c fil"
date: 2010-11-25
forum: Programming Talk
---

### Post by jamesbon on 2010-11-25
Do I need to declare my functions extern if I want to be able to use them in many C files.
Consider following example
I have  three files declarations.h graph.c and stack.c .
I am making a program which would implement Breadth First Search.
So graph.c defines a graph and stack.c has some functions which which when called can create a stack as I want.
I want to call functions declared in stack.c from the file graph.c.
For this do I need to declare the functions in stack.c as extern?
Or what do I need to do so that the functions in stack.c are available to graph.c .
The main() is defined only in graph.c.
I am yet developing this sort of library so there may be instances that one file of c is calling functions from another file.But main will be present only at one place.

---

### Post by spjackson on 2010-11-25
> **jamesbon said:**
> Do I need to declare my functions extern if I want to be able to use them in many C files.
Consider following example
I have  three files declarations.h graph.c and stack.c .
I am making a program which would implement Breadth First Search.
So graph.c defines a graph and stack.c has some functions which which when called can create a stack as I want.
I want to call functions declared in stack.c from the file graph.c.
For this do I need to declare the functions in stack.c as extern?
Or what do I need to do so that the functions in stack.c are available to graph.c .
The main() is defined only in graph.c.
I am yet developing this sort of library so there may be instances that one file of c is calling functions from another file.But main will be present only at one place.
Unless explicitly declared as static, all functions in C are extern. You could put the reserved word "extern" before each function prototype in your headers, but it is just noise and not common practice.

---

### Post by Arndt on 2010-11-25
> **spjackson said:**
> Unless explicitly declared as static, all functions in C are extern. You could put the reserved word "extern" before each function prototype in your headers, but it is just noise and not common practice.

I think it is common practice, but if it indeed is unnecessary, I'm not protesting.

---

### Post by Tony Flury on 2010-11-25
> **jamesbon said:**
> Do I need to declare my functions extern if I want to be able to use them in many C files.
Consider following example
I have  three files declarations.h graph.c and stack.c .
I am making a program which would implement Breadth First Search.
So graph.c defines a graph and stack.c has some functions which which when called can create a stack as I want.
I want to call functions declared in stack.c from the file graph.c.
For this do I need to declare the functions in stack.c as extern?
Or what do I need to do so that the functions in stack.c are available to graph.c .
The main() is defined only in graph.c.
I am yet developing this sort of library so there may be instances that one file of c is calling functions from another file.But main will be present only at one place.

The "normal" way of doing this is to define a "stack.h" header which contains declarations (but not the definitions) of your functions in "stack.c". "graph.c" then includes "stack.h" and you let the linker do the rest.

---

### Post by nvteighen on 2010-11-25
extern is only required for cross-module variables, because variables are considered module-scoped by default, while functions are considered to have cross-module scope by default... Maybe this could be considered an incoherence in the C language, but it's pretty practical.

Using extern for functions won't fire a compiler error or warning, but it has no effect. I'd recommend you avoid it so your code isn't cluttered with stuff that actually doesn't do anything... but again, it's your choice.

---

### Post by jamesbon on 2010-11-26
Ok guys thanks for the answers I learned a bit new things.

---

