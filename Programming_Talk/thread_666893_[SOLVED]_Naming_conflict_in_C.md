---
title: "[SOLVED] Naming conflict in C"
date: 2008-01-13
forum: Programming Talk
---

### Post by fyplinux on 2008-01-13
Hi,

I heard that C++ introduced the idea of namespace to solve the problem of naming conflict. take an example. Mr.A has a function f(), Mr.B has another function but also named f(), Mr.C **must**import both the code of Mr.A and Mr.B, but he only want f() from Mr.B, there would be an error when compiling as there are two f(), how could Mr.C get the right f()?

Is there any mechanism or general approach to solve such a problem with C programming?

---

### Post by kevykev on 2008-01-13
Usually the general approach in C is to prefix all functions with the name of the library being developed. For instance, if you were writing a function f() for the gtk library you would call it gtk_f(). 

However, if you want to use existing libraries with a naming conflict, you might have no other option but to edit the library code

---

### Post by LaRoza on 2008-01-13
Being careful. The lack of namespaces is not the best situation, but C doesn't have anything by itself that will cause a conflict, there are very few keywords. Just know what you are using when using libraries (the prefixes help)

---

### Post by YourSurrogateGod on 2008-01-13
> **kevykev said:**
> Usually the general approach in C is to prefix all functions with the name of the library being developed. For instance, if you were writing a function f() for the gtk library you would call it gtk_f(). 

However, if you want to use existing libraries with a naming conflict, you might have no other option but to edit the library code

Just curious, but would wrapper functions work? That would be my initial approach to such a problem or have I misunderstood something?

---

### Post by kevykev on 2008-01-13
> **YourSurrogateGod said:**
> Just curious, but would wrapper functions work? That would be my initial approach to such a problem or have I misunderstood something?

Not sure, but you might be able to create wrapper functions and compile them as a shared library and then link to that...

---

### Post by fyplinux on 2008-01-14
> **YourSurrogateGod said:**
> Just curious, but would wrapper functions work? That would be my initial approach to such a problem or have I misunderstood something?

If you want to wrap something, you should know what should be wrapped. the problem seems to be cannot find the target to be wrapped

---

