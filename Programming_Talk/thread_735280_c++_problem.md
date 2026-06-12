---
title: "c++ problem"
date: 2008-03-25
forum: Programming Talk
---

### Post by StOoZ on 2008-03-25
Ok, I'll start with this , that this is not Homework nor something that has to do with education, I found it on the web (q #1):
[http://my.safaribooksonline.com/0672322234/ch08lev1sec8]("http://my.safaribooksonline.com/0672322234/ch08lev1sec8")
from a book im reading about C++.
now Im having troubles with question #1 there, I can figure out ,how the function can know, how much times it has been called, if I can only pass it one value (or two,with overloading,but none for the amount of calls)

any idea,or leads? (not looking for a solution).

---

### Post by lloyd_b on 2008-03-25
> **StOoZ said:**
> Ok, I'll start with this , that this is not Homework nor something that has to do with education, I found it on the web (q #1):
[http://my.safaribooksonline.com/0672322234/ch08lev1sec8]("http://my.safaribooksonline.com/0672322234/ch08lev1sec8")
from a book im reading about C++.
now Im having troubles with question #1 there, I can figure out ,how the function can know, how much times it has been called, if I can only pass it one value (or two,with overloading,but none for the amount of calls)

any idea,or leads? (not looking for a solution).

The magic word is "static" :)

Lloyd B.

---

### Post by StOoZ on 2008-03-25
hmm weired, the book didnt cover static variables yet... :(

---

### Post by lloyd_b on 2008-03-25
> **StOoZ said:**
> hmm weired, the book didnt cover static variables yet... :(

(Be advised, I'm an old-school C programmer, with only limited experience with C++).

There has to be a counter variable *somewhere*.  Since the exercise is about "writing a function", I'm assuming that to mean that the function must be complete within itself, and not rely on any external data other than the pointer to a string and the integer "command" value.

Given those restrictions, the static counter is the only solution I see (and it is a trivially easy solution to implement).

Lloyd B.

---

### Post by escapee on 2008-03-26
Well for a hint, the solution for passing either one or two arguments is can be done very easily without any overloading, though you may have to search Google on how to use the technique if you don't have a subscription to the site.  It names the idea, but doesn't say how to implement it.  

Aside from that, static or global variables would aid you well...of course I am not condoning the usage of global variables for things such as this, just stating it is possible :)

---

