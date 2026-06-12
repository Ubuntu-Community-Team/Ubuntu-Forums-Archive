---
title: "Java Identifier Expected"
date: 2010-10-27
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-10-27
First off, yes this is homework. But don't freak out, because I just want a compiler error fixed. I have been programming for 4 years, I avoided Java for the last 3 of those to find that college uses it!!

So ...

Code (LimCapList Provided by teacher)
[PHP]public class Array12<E> implements LimCapList<E> {
    Object[] array;
    int head;
    int tail;

    public static final int DEFAULT_CAPACITY = 10;

    public Array12<E>() {
        array = new Object[DEFAULT_CAPACITY];
        head = tail = -1;
    }

    public Array12<E>(int cap) {
        array = new Object[cap];
        head = tail = -1;
    }

    ... Other Stuff ...

}
[/PHP]

Commands
[PHP]$ javac Array12.java
Array12.java:9: <identifier> expected
    public Array12<E>() {
                     ^
Array12.java:14: <identifier> expected
    public Array12<E>(int cap) {
                     ^
2 errors
[/PHP]

Don't write a class for me, just fix the error. Java and I don't work well together!

Thank you

---

### Post by andrewc6l on 2010-10-27
Constructors don't need a generic after the name. Just take out the <E> in Array12<E>() and Array12<E>(int cap).

---

### Post by Mr.Macdonald on 2010-10-27
Wow, that simple
Thanks

---

### Post by Queue29 on 2010-10-27
> **Mr.Macdonald said:**
> Wow, that simple
Thanks

Well yea, this will work, but you're teetering on the edge of one of the ugliest parts of Java. See that [FONT="Courier New"]Object[] array[/FONT]? Since that's the storage container for a class of type E, shouldn't it store only E's and not anything that inherets from Object (which is everything)?

So try changing Object[] into E[] and see what happens (particularly when you try to create a [FONT="Courier New"]new E[][/FONT] ).

---

### Post by wkhasintha on 2010-10-27
> **andrewc6l said:**
> Constructors don't need a generic after the name. Just take out the <E> in Array12<E>() and Array12<E>(int cap).

Excatly...

---

