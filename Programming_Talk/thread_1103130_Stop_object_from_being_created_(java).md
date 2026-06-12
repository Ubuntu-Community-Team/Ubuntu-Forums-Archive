---
title: "Stop object from being created? (java)"
date: 2009-03-22
forum: Programming Talk
---

### Post by mickeelm on 2009-03-22
Is it possible for a class to stop an object of it from being created? For example, let's say I have a class called Card.java, representing a playing card in a normal 52-card deck with this constructor:

```
public Card(String suit, String value) {

//Some code here...

}
```

And that the valid values would be:

```
private final String suits[] = {"S","H","C","D"};
private final String values[] = {"A","1","2","3","4","5","6","7","8","9","T","J","Q","K"};
```

I could compare the incoming data against these and I could give the Card object some "invalid" boolean flag etc. if I got the values "X" and "24", but is there a way to just refuse the object from being created and force a try-catch (or equal) from the calling class or is it up to me to make sure that a check is made already in the calling class?

---

### Post by jpeddicord on 2009-03-22
It's been a long time since I've worked with Java, but is it possible you could throw an exception in the initialization function to cause it to exit?

---

### Post by simeon87 on 2009-03-22
You could use enums to define the valid values. The Card constructor would then become:

```

public enum CardSuit { }

public enum CardValue { }

public Card(CardSuit suit, CardValue value) {

//Some code here...

}

```

---

### Post by kjohansen on 2009-03-22
exceptions are allowed in the constructor....

---

### Post by CptPicard on 2009-03-22
Another architectural possibility that may be of interest is the usage of a factory/builder method that creates valid examples of classes, and then the class itself can be given a private constructor that is not callable from the outside.

This pattern is often used instead of throwing from constructor, as it makes sure there is no interrupted construction and thus objects in a weird half-built state left dangling somewhere. These sorts of issues seemed to be much more important in C++ but the pattern itself lives on in Java too...

---

### Post by mickeelm on 2009-03-22
Thanks all for the info! Really helpful and I'll look more into your suggestions :)

---

### Post by s.fox on 2009-03-22
Hi,

I may be missing something but I think you have too many cards or am I wrong? :D

```
private final String values[] = {"A","1","2","3","4","5","6","7","8","9","T","J","Q","K"}
```

---

### Post by Reiger on 2009-03-22
I'd definitely go for the private constructor:
(1) You can ensure that only a certain instance is created (using a custom newInstance() method, for example);
(2) It doesn't get as messy with try {} catch() {} blocks. (Expensive calls which under all circumstances should fail -given the thread title. And -given the thread title- you will probably see other programmers making the mistake of trying to construct an object... it is just wasting their time + patience ...)
(3) On the semantic level it is by far the superior way, because: if there is no constructor made public, it is clear this object should not be manually instantiated. Programmers with some experience w.r.t factory-heavy enviroments (swing, db-interfaces) will immediately recognise that there should be a static method somewhere which gives an instance or that the object exposes only static methods/members anyway.

---

### Post by kavon89 on 2009-03-22
> **mickeelm said:**
> Is it possible for a class to stop an object of it from being created?

You could delcare the class [abstract]("http://java.sun.com/docs/books/tutorial/java/IandI/abstract.html").

---

### Post by Can+~ on 2009-03-22
> **Ash R said:**
> Hi,

I may be missing something but I think you have too many cards or am I wrong? :D

```
private final String values[] = {"A","1","2","3","4","5","6","7","8","9","T","J","Q","K"}
```

I guess that "T" is 10.

---

### Post by s.fox on 2009-03-22
> **Can+~ said:**
> I guess that "T" is 10.

Why have an Ace and a 1 then?

---

### Post by CptPicard on 2009-03-22
> **kavon89 said:**
> You could delcare the class [abstract]("http://java.sun.com/docs/books/tutorial/java/IandI/abstract.html").

That would mean that there could never be concrete instantiations of it, which is not the case here...

---

### Post by mickeelm on 2009-03-22
Again, thanks a lot for all the helpful answers, its great with plenty of options, and also I'll be able to learn more about everything that you have mentioned.

Thank you!

And also, yes, "T" is ten since "10" takes up two characters :)

---

### Post by mickeelm on 2009-03-22
> **Ash R said:**
> Why have an Ace and a 1 then?

Good point :) Didn't think it through enough!

---

### Post by The Cog on 2009-03-22
I might be inclined to have a provate constructor and a factory methdod that returns a set of 52 cards. And maybe rfuses to produce any more if called again.

---

### Post by HotCupOfJava on 2009-03-22
I would tend to go with simeons87's solution - declare a new type for both the suits and values, then your Card constructor can take only those types. Problem solved, simple and easy.

---

### Post by mickeelm on 2009-03-23
> **simeon87 said:**
> You could use enums to define the valid values. The Card constructor would then become:

```

public enum CardSuit { }

public enum CardValue { }

public Card(CardSuit suit, CardValue value) {

//Some code here...

}

```

I tried this, but it seems that I can't use integers? It worked fine with Strings but such as S,H,D,C etc. but A,2,3,4...gives me an error after the comma following A. Whenever I type an integer, Eclipse (or any IDE I hope :) ) gives me an error.

I could go around this, but it seems as if only Strings are alowed as/in enums?

---

### Post by jespdj on 2009-03-23
> **mickeelm said:**
> I could go around this, but it seems as if only Strings are alowed as/in enums?
Enum constants must be valid Java variable names. You can't name a variable "2", for example, so you can't make an enum value with the name "2".

---

### Post by simeon87 on 2009-03-23
> **jespdj said:**
> Enum constants must be valid Java variable names. You can't name a variable "2", for example, so you can't make an enum value with the name "2".

You could use ACE, TWO, THREE, ..., TEN, JACK, QUEEN, KING instead (also see [Enum Types](http://java.sun.com/docs/books/tutorial/java/javaOO/enum.html), Java tutorials).

---

### Post by mickeelm on 2009-03-23
Okay, great! Thanks :)

---

