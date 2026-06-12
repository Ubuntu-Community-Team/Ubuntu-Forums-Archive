---
title: "Javascript Interview Questions"
date: 2009-06-19
forum: Programming Talk
---

### Post by SuperMike on 2009-06-19
I have an upcoming interview about Javascript. Do you know these answers?

1. How many simultaneous connections can an XHTML web page have back to the server for getting things?

2. How many simultaneous XMLHttpRequest connections can a web page have back to the server for getting things?

3. Can XMLHttpRequest be used sync as well as async?

4. Which of the following OO properties does Javascript have?

   A. class, object (and the difference between the two)
   B. instantiation
   C. method (as opposed to, say, a C function)
   D. class/static method
   E. static/class initializer
   F. constructor
   G. destructor/finalizer
   H. superclass or base class
   I. subclass or derived class
   J. inheritance
   K. encapsulation
   L. multiple inheritance
   M. delegation/forwarding
   N. composition/aggregation
   O. abstract class
   P. method overriding
   Q. method overloading (and difference from overriding)
   R. polymorphism
   S. method visibility (e.g. public/private/other)

---

### Post by Reiger on 2009-06-19
> **SuperMike said:**
> I have an upcoming interview about Javascript. Do you know these answers?

1. How many simultaneous connections can an XHTML web page have back to the server for getting things?

This depends. If you are on Windows you are (usually) stuck on two connections to the same domain; otherwise it sort of depends on the browser. Most browsers implement a `slot' system: there are at max N open connections with a maximum of M per domain.

> 2. How many simultaneous XMLHttpRequest connections can a web page have back to the server for getting things?

3. Can XMLHttpRequest be used sync as well as async?

Of course. Anything that supports async connections can be made to support sync'ed connections by using a construct that blocks until an operation has either failed or succeeded completely. Consider the following mock example:

```

var lock = false;
var response = false;
function sync(action) {
  lock = true;
  action();
  while(true) {
    if(check(response) !== false)
     break;
  }
  lock = false;
}
function check(response) {
  /* implement code to check if the response is finished, store in a boolean called responseOK */
  return responseOK;
}

```
This ensures that sync() will block until response has been loaded. You can of course embellish this as you wish. So it will block any further code execution till the previous action has been completed, essentially enforcing a synchronized program.

> 
4. Which of the following OO properties does Javascript have?

   A. class, object (and the difference between the two)
   B. instantiation
   C. method (as opposed to, say, a C function)
   D. class/static method
   E. static/class initializer
   F. constructor
   G. destructor/finalizer
   H. superclass or base class
   I. subclass or derived class
   J. inheritance
   K. encapsulation
   L. multiple inheritance
   M. delegation/forwarding
   N. composition/aggregation
   O. abstract class
   P. method overriding
   Q. method overloading (and difference from overriding)
   R. polymorphism
   S. method visibility (e.g. public/private/other)

Get rid of the Java implementation of Objects first. JavaScript treats objects and functions rather differently: owing to the influence of Scheme you get to play with functions as if they are objects and vice versa; more importantly: you override objects on an ad-hoc basis and/or using the prototype construct.

---

### Post by SuperMike on 2009-06-19
Hey, thanks, Reiger.

---

