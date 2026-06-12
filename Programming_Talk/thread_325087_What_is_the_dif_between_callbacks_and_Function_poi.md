---
title: "What is the dif between callbacks and Function pointers?"
date: 2006-12-25
forum: Programming Talk
---

### Post by systemintheglitch on 2006-12-25
I am really curious, anyone care to elaborate?

---

### Post by slavik on 2006-12-26
the reason these two would seem the same (although not really) is because C does not have references, so you cannot send a reference.

let's say I write a function called 'monitor' and you want to have monitor call your function or alert you when something happens.

the argument you pass to my function is a callback (on the abstract level) ... in the technical level, it is a function pointer, or if you use C++, it can be a function reference.

a function pointer is simply a pointer to an address where you find the function. a callback is something that (for exmaple) I would ask you to provide once something happens, you give me a callback. think of it as a 'callback number' (using the phone system). callback is the actual function ...

in short:
callback - the abstract
function pointer - the technical, not always used for callbacks.

for example, in C++, you can have the generic sort function sort your new weird data type (class/struct) or even regular data types according to your own comparison. but to do this, sort requires a compare function from you so you give it a function pointer (in C++ it is a reference, but the idea is to illustrate).

---

