---
title: "[Java]Any gotchas coming from Python?"
date: 2008-12-30
forum: Programming Talk
---

### Post by fiddler616 on 2008-12-30
Hello,
In three weeks, I'm going to start taking a Computer Science course (and I have a test to get in in two weeks(!)). I've been looking at the syllabus, and it seems pretty easy. The only problem is that it's in Java, and I think in Python.
So I'm wondering if there are any gotchas I should know about, to make life easier. (This excludes obvious syntax changes, like semicolons, braces and the ridiculous "Foo bar = new Foo(params);" way of creating objects. I'm also all right at types--remembering to declare them, converting them, using the right one, etc.) Is there anything else?

Thank you very much.

---

### Post by tinny on 2008-12-30
A few things spring to mind.

OO obsession. You really need to think in a UML sort of way. Class hierarchys, relationships, get your interfaces right etc.

Type safety. Type safety in collections can be pretty confusing ([Generics]("http://java.sun.com/j2se/1.5.0/docs/guide/language/generics.html"))

No closures :-( instead you use anonymous inner types.

No built in testing or object mocking. Instead you use a third party API like JMock or JUnit.

---

### Post by shadylookin on 2008-12-30
> **fiddler616 said:**
> Hello,
In three weeks, I'm going to start taking a Computer Science course (and I have a test to get in in two weeks(!)). I've been looking at the syllabus, and it seems pretty easy. The only problem is that it's in Java, and I think in Python.
So I'm wondering if there are any gotchas I should know about, to make life easier. (This excludes obvious syntax changes, like semicolons, braces and the ridiculous "Foo bar = new Foo(params);" way of creating objects. I'm also all right at types--remembering to declare them, converting them, using the right one, etc.) Is there anything else?

Thank you very much.

numbers can overflow ints are 32bits anything beyond that gets truncated so you can have so messed up looking numbers that are completely wrong. For instance 32^32 in python is 1461501637330902918203684832716283019655932542976
in java it's 
2147483647

---

### Post by fiddler616 on 2008-12-30
> **shadylookin said:**
> numbers can overflow ints are 32bits anything beyond that gets truncated so you can have so messed up looking numbers that are completely wrong. For instance 32^32 in python is 1461501637330902918203684832716283019655932542976
in java it's 
2147483647
I guess the solution is judicious application of longs?

---

### Post by shadylookin on 2008-12-30
> **fiddler616 said:**
> I guess the solution is judicious application of longs?

longs only hold 64 bits so the java answer would still only be 
9223372036854775807
which is significantly off. 

java has BigInteger and BigDecimal in java.Math but that's a pain to deal with unless you need it. 

Only real solution is to insure that you don't put yourself in such a situation where number overflow is possible

---

### Post by fiddler616 on 2008-12-30
> **shadylookin said:**
> longs only hold 64 bits so the java answer would still only be 
9223372036854775807
which is significantly off. 

java has BigInteger and BigDecimal in java.Math but that's a pain to deal with unless you need it. 

Only real solution is to insure that you don't put yourself in such a situation where number overflow is possible
I think this is one of those situations where if I'm smart enough to require that big of a number, I'll be smart enough to get it then. Thanks for the info though.

---

### Post by pmasiar on 2008-12-30
There is complete blog industry comparing Java and Python. Sadly, not all "experts" are equally qualified in both languages, but some are. I found author which can find good features on both sides - so he might be more even handed than most: [Python Is Not Java](http://dirtsimple.org/2004/12/python-is-not-java.html) and [Java is not Python, either...](http://dirtsimple.org/2004/12/java-is-not-python-either.html)

One thing I noticed is how painfully verbose is Java when creating non-primitive literals. But that's the pain you have to learn to endure I guess... :-(

For me, good naming convention helps me when dealing with type explosion: collection of a 'thing' is called 'things', iterator 'thingi' etc. Get used to explicit 'this', so you can name parameters in constructor as member fields. Common sense rules... but more important in verbose language, because it is harder to see the essence in all that verbiage.

---

