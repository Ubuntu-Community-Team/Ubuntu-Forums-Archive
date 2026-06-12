---
title: "Unit Testing with JUnit and Generic classes"
date: 2008-11-18
forum: Programming Talk
---

### Post by rekahsoft on 2008-11-18
Hi all, i am working on a class that represents a mathematical set for use with a program i am working on. The one thing i would like to get working would be JUnit testing so i could make sure all the methods of the Set class are working properly as i make changes. The issue is that Set is a generic class...so how do i test that the functions will work with all types? Logically they should because all the objects will extend java.lang.Object and use methods that are over-ridden from the class. But i was wondering if there is any special way to unit test generic classes?

Note: i did not include any code (for the Set class) because the question isn't specific to code.

---

### Post by Quikee on 2008-11-19
> **rekahsoft said:**
> Hi all, i am working on a class that represents a mathematical set for use with a program i am working on. The one thing i would like to get working would be JUnit testing so i could make sure all the methods of the Set class are working properly as i make changes. The issue is that Set is a generic class...so how do i test that the functions will work with all types? Logically they should because all the objects will extend java.lang.Object and use methods that are over-ridden from the class. But i was wondering if there is any special way to unit test generic classes?

Note: i did not include any code (for the Set class) because the question isn't specific to code.

Just choose one object as a test object or create one for the testing purpose. Generally it doesn't matter which object it is and you definitely don't want to test with every object in the system. 

It also depends on what you use from the object - for example if you use hashCode then make sure that you also check on a object which returns a constant hashCode for all objects of a particular test class.

---

