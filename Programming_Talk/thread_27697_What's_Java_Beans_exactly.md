---
title: "What's Java Beans exactly?"
date: 2005-04-17
forum: Programming Talk
---

### Post by i-tech on 2005-04-17
I just have a short look at Java Beans but I dont get the use of it? what does it provide and how does it provide?

---

### Post by bihe on 2005-04-17
he, come on ....
[http://www.google.com/search?hl=en&q=java+beans&btnG=Google-Search&meta=](http://www.google.com/search?hl=en&q=java+beans&btnG=Google-Search&meta=)

---

### Post by i-tech on 2005-04-17
very helpfull tough i never think of looking at google thanx man very brilliant!! 
> JavaBeans technology is the component architecture for the Java 2 Platform, Standard Edition (J2SE). Components (JavaBeans) are reusable software programs that you can develop and assemble easily to create sophisticated applications. JavaBeans technology is based on the [JavaBeans specification]("http://java.sun.com/products/javabeans/docs/spec.html").   
isnt every thing developed in java is reuseable? whats the difference why should i use beans?

---

### Post by psylence on 2005-04-17
It's really pretty simple...  A JavaBean is a component that conforms to the JavaBean specifications...

[http://java.sun.com/products/javabeans/docs/spec.html](http://java.sun.com/products/javabeans/docs/spec.html)

At the simplest, it has "getters" and "setters" for its attributes.  So if an object has an attribute 'name' that is a String, it will have the accessor and mutator:

public String getName();
public void setName(String name);

Beans have information that can be inspected from them via Bean APIs

[http://java.sun.com/j2se/1.3/docs/api/java/beans/package-summary.html](http://java.sun.com/j2se/1.3/docs/api/java/beans/package-summary.html)

Don't try to think too hard about it and imagine it's some amazing scheme, it's heavily hyped, and just handy, not an end in itself...

Most Swing UI widgets conform to the spec, check out their source for a feel for how they handled it...

---

