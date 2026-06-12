---
title: "encapsulation in java"
date: 2011-05-18
forum: Programming Talk
---

### Post by guest_user on 2011-05-18
1) if I have a private reference to an object and I provide a get method which returns it, does it break the encapsulation of the class since the client of the class can now obtain a reference to a private member object and change it? 

2) If the above answer is yes, I suppose the solution would be to clone the object when it is set and return another clone when it is get? Wouldn't that be very inefficient?

---

### Post by Some Penguin on 2011-05-18
*shrug*  If you're returning a reference to a *mutable* object, such as an ordinary Collection, then yes. 

You don't necessary have to clone the object; you can return a wrapped version of the object that simply doesn't provide any mutators, nor any way to access the underlying object.

You do want to copy it if you do NOT want to expose state changes to the user, of course.   If you use the Collections.unmodifiableFoo() wrappers, the recipient can't change the Foo, but the recipient will still see any changes in the Foo that have been made through other means.  This may or may not be what you intend.

---

