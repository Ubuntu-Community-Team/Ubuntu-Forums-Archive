---
title: "Pure Virtual Function"
date: 2013-01-28
forum: Programming Talk
---

### Post by hatsoff on 2013-01-28
Hi there,
my question is can we use data members of base class in implementation of pure virtual function in drive class?
P.S
its saying give pure virtual function implementation(search function) for different users(drived classes) on a property portal where tenant buyer will search on the basis of same parameters and a owner can post advertise on the same parameters as tenant and buyer,  so i thought lets put these parameters in base class b/c its using again and again by tenant and buyer and owner(drive classes) if i put them into base class then these parameters would be available to all these drived class (reducing effort),is it legal?
or i'll write different data member for different drived classes and implement pure virtual function.

---

### Post by trent.josephsen on 2013-01-28
The definition of "pure virtual" is essentially "without any implementation", so I'm not really sure what you're asking. You can't define an implementation for a (pure) virtual function without making it *not* a pure virtual function.

On the other hand, it's usually perfectly acceptable for child classes to inherit *non*-virtual methods, so I also don't understand what should stop you from just writing a parent class with an implementation of the search method and letting the child classes inherit it.

(It might help a little if you mention what language you're using, as the various OOP languages can vary a little on the usage of certain OO terms.)

---

### Post by hatsoff on 2013-01-28
you r right i m giving only pure virtual function signature in base class and implementing it(search function) in child class but all three child classes are using same parameters(data members) for search in search method...no i want to reuse data members of base class in child class...language is c++

---

### Post by hatsoff on 2013-01-28
I think i make getter and setter function virtual....

---

### Post by dwhitney67 on 2013-01-29
> **hatsoff said:**
> I think i make getter and setter function virtual....

If all of your Sub-classes share similar data, then define these in the Base class.  Whether you choose to implement accessors (gets and sets) within the Base class is up to you.  Personally I would declare the data to be "protected".

---

### Post by muteXe on 2013-01-29
I think you're asking about abstract base classes, rather than specifics about pure virtual functions aren't you?

---

