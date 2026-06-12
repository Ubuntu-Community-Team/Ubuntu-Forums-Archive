---
title: "Java dynamically load classes"
date: 2011-05-18
forum: Programming Talk
---

### Post by Stormcurse on 2011-05-18
Hey, so I have a question that the title basically states:  How can one dynamically load a java .class file?  More specifically, I have the code to dynamically load a class, the problem is that the class file needs to be made with the correct package declaration and also with the part about the super-class it extends.  However, I cannot figure out how to get the .java to compile without initially having references to the superclass it extends, and i am unsure what the package declaration should be.

I am trying to figure this out for modding purposes.

Each dynamically loaded class will be a subclass of an over-arching class.  I can effectively find and load classes using the class loader, I just cannot figure out how to compile them.  The only solution I have come up with so far is to actually dynamically edit the .class to add the package name and the superclass after it has compiled, but I really don't want to do that.

Help would be appreciated.

Cheers,
Stormcurse

---

### Post by Some Penguin on 2011-05-18
Provide and expose an interface, since one can implement any number of interfaces and interfaces are in no way restrictive of how they organize their package hierarchy.  Then have them specify the class as a fully-qualified name.

---

### Post by Stormcurse on 2011-05-19
I don't think I was very clear...

I like the idea of making an interface, and I will probably change the abstract super-class to an interface.  However, there is no way for the class to reference that interface, because it will be part of a compiled jar.  Also, I am not sure what to actually call the package for the .class file... I suppose it should be the directories in relation to where the jar is going to be run.

I hope it makes more sense now...

---

### Post by Some Penguin on 2011-05-19
> **Stormcurse said:**
> I don't think I was very clear...

However, there is no way for the class to reference that interface, because it will be part of a compiled jar.

That's a non-sequitor; .jar goes in classpath.  It's now accessible.   Import it.  Done.

---

