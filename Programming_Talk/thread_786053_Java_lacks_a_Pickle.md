---
title: "Java lacks a Pickle??"
date: 2008-05-07
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-05-07
I have been building a few nice recursively accessible classes (does that make sense??)

Now that they function i want to read and write them to a file!?!?!?!?!

because its recursive (an instance can contain many instances of the same class) it seems near impossible (or past my will) to develop an algorithm that could read and write to a file.

So ...



**[SIZE="2"]Does Java have a pickling class just like pythons pickle (I really hope so)?[/SIZE]**



Please no :

Why are you using Java, its slow, bad, junk, trash language, etc.

because i have heard it all before and in my experience its not true.


Thank you

---

### Post by olejorgen on 2008-05-07
[http://java.sun.com/developer/technicalArticles/Programming/serialization/](http://java.sun.com/developer/technicalArticles/Programming/serialization/)

Short story: implement java.io.Serializable

---

### Post by Quikee on 2008-05-08
> **Mr.Macdonald said:**
> ... it seems near impossible (or past my will) to develop an algorithm that could read and write to a file...


Why? Just end the recursion if you get to an object you already have "visited". The serialization would do the same however. ;)

---

### Post by Mr.Macdonald on 2008-05-08
yes but in the recursion i could have


tree1
[INDENT]1data
1data
1data
1data
tree2
[INDENT]2data
2data
tree3
[INDENT]3data
3data[/INDENT][/INDENT][/INDENT]


and i am to lazy to make something to do that (its a lot more complex) and serialization would be far easier.

---

