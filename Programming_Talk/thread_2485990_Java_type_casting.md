---
title: "Java type casting"
date: 2023-04-16
forum: Programming Talk
---

### Post by ronakmehta on 2023-04-16
I'm attempting to clarify this so that I completely get type casting. Please correct me if I'm wrong, as I've been self-learning Java for approximately 2 months now at a very slow pace.


Assume I've developed a class called SubObject. And I am aware that all classes that lack an explicit direct superclass are believed to be subclasses of the Object class.

```
Object obj01 = new SubObject(); 
    SubObject subObj01 = (SubObject) obj01;
    System.out.println(subObj1); //prints out com.examplePackage.SubObject1234e1234;
```

So I've successfully downcast the base class's (Object) reference to its derived class (subObject). However..

```
Object obj02 = new Object();
SubObject subObj02 = (SubObject) obj02;//this throws the ClassCastException error.
```

According to my understanding of the ClassCastException mistake, it's inherited RuntimeException to catch it during compile time, to show that the function attempted to cast an object to a subclass of which it is not an instance following this [manual]("https://www.scaler.com/topics/java/type-casting-in-java/"). Because subObj2 is an instance of Object rather than SubObject, it is incompatible.


So here are my two questions: 1. Is there any flaw/error in my comprehension? 2. In what situations is downcasting used? Thank you for your assistance, everyone.

---

