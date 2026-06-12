---
title: "Java reflection: find serializable classes in package"
date: 2010-02-26
forum: Programming Talk
---

### Post by andrew222 on 2010-02-26
In Java, is there a way to find all classes within a package that are serializable and then add the Class object for these classes to a collection?

---

### Post by CptPicard on 2010-02-26
That's a very interesting question... all the solutions googling gives seem to be about reading a directory or a jar file contents which is not exactly what I guess you're after. I get the impression that the classloader just gets a requested, fully qualified class from "where-ever" on an as needed basis, and that there really is no general "package-level abstraction" for this (unless you can provide physical class locations such as directory/jar).

---

### Post by Reiger on 2010-02-26
That is pretty much my understanding too: Java's classloading mechanism is rather lazy which kind of prevents the JVM from figuring all this stuff out on its own -- it has no way of knowing until it actually has defined the classes it needs to inspect.

And in any case the class hierarchy is made extra complex by the introduction of different namespace scopes that the classloaders themselves provide; so package foo/bar under classloader A is *not* the same as foo/bar under B...

So no the only way of doing this is (a) manually reading the ZIP/JAR list-of-contents (lookup the global directory in ZIP file format) and prodding the files; (b) maintaining a custom encoding of this information, such as a class that implements an interface say:
```

SerializeCatalogue {
  Class[] getClasses();
}

```

Or of course, a simple list of class names in a plain text file. :P

---

