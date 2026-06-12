---
title: "can you prototype a class/struct in c++?"
date: 2006-11-30
forum: Programming Talk
---

### Post by Choad on 2006-11-30
basically, i am getting errors and its easy to see why, because in my definition of a struct, i refer to a class that is as-yet undefined. so im thinking i must be able to prototype these things somehow? i googled to no avail...

---

### Post by Zdravko on 2006-11-30
Just write:
> 
class A;
struct B;
//use A and B's names generally


---

### Post by hod139 on 2006-11-30
It is called a forward declaration (so now you have some keywords to throw at google).

---

### Post by Tomosaur on 2006-11-30
This is why you go from the ground up :P

But yes, you should just able to declare the class/struct without actually implementing it.

---

### Post by Choad on 2006-11-30
> **Tomosaur said:**
> This is why you go from the ground up :P

But yes, you should just able to declare the class/struct without actually implementing it.
yeah but i have cyclic dependencies :p

thanks guys :D

---

