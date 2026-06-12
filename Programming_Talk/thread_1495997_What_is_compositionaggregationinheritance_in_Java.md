---
title: "What is composition/aggregation/inheritance in Java?"
date: 2010-05-28
forum: Programming Talk
---

### Post by s3a on 2010-05-28
Is composition the **action of referring to objects of other classes and treating them as members of a particular other class**? (In Java if this definition is not universal to all languages)

This is all due to my attempt to understand the differences between aggregation, composition and inheritance. Also, by the way, is inheritance **extending an abstract class or interface**? As for aggregation, I'm not too sure as to what it is other than it being slightly related to composition in that they both have a "has-a" relationship as opposed to the is "is-a" relationship that inheritance has.

If I'm right, it'd be great to have a confirmation on the stuff I stated otherwise, I'd appreciate it if someone could inform me of what the proper definitions are.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by shadylookin on 2010-05-28
Inheritance is creating a child from a parent class. So any time you use the extends or implements keyword you're using inheritance. You can extend an abstract class, a normal class, and you can implement an interface.

Composition I believe is when an object is part of an object but is never shared with other objects. Like a car has a steering wheel, but you can't share them between multiple cars. 

I don't really remember aggregation, but I think it was too similar to association for it to be it's own thing.

---

