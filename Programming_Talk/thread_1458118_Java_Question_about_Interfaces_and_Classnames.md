---
title: "Java Question about Interfaces and Classnames"
date: 2010-04-19
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-19
Is there a way in Java to get the classname of all classes within a package which implement a given interface?  Furthermore, once I know the class name, is there a way to get an instance of these classes by classname?  Is it possible to declare a static method in an interface definition?  I cannot declare static in the interface definition due to error "only public and abstract are allowed".  Is there a way around that restriction?  Basically, I have a single static method that I want to implement in an interface -- that would be the only method in the interface.

---

### Post by Some Penguin on 2010-04-19
> **SNYP40A1 said:**
> Is there a way in Java to get the classname of all classes within a package which implement a given interface?

No built-in way.  It might be possible to rewrite a class loader to export this functionality, but that's really a "not really".  The JVM doesn't actually care what classes are available until somebody ask for 'em.

> Furthermore, once I know the class name, is there a way to get an instance of these classes by classname?

Get the Class object by using Class.forName(), then get the Constructor from the Class object.  Alternately, use newInstance() from the Class object, if you don't need a constructor with arguments.

>  Is it possible to declare a static method in an interface definition?

No.

>  I cannot declare static in the interface definition due to error "only public and abstract are allowed".  Is there a way around that restriction?  Basically, I have a single static method that I want to implement in an interface -- that would be the only method in the interface.

Interfaces don't take static methods, period.  At least up to Java 6; I haven't been following Java 7 development at all.

You can probably get where you're wanting to go by moving the method into a class, and having other classes invoke that method assuming that you don't want to have these classes all inherit from a particular class.

---

