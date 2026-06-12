---
title: "[SOLVED] C++ pointers to objects and object as method argument"
date: 2008-12-23
forum: Programming Talk
---

### Post by gmclachl on 2008-12-23
I have been told it is bad to pass in a pointer as a method argument and you should try to do it by reference instead, but I am a bit confused as to how. 

If I define an Object Foo with a constructor of Foo(const Bar&)

and then do something like 

Bar* b = new Bar();
Foo f = new Foo(b&);

Then it will fail, because b is a pointer to the object and I am trying to pass by reference. 

If I do 

Bar b; 
Foo f = new Foo(b);

then it will happily work 

G

---

### Post by gmclachl on 2008-12-23
Actually never mind I was being silly.  

George

---

### Post by dwhitney67 on 2008-12-23
Yep, the syntax errors in the OP show that.

Please mark your thread as being solved.

---

