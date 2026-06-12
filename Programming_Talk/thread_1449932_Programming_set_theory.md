---
title: "Programming set theory"
date: 2010-04-08
forum: Programming Talk
---

### Post by Sugz on 2010-04-08
Hello, now i must admit, im not the most mathematically minded guy in the world, but I ave recently been diving into set theory as a means of explaining some programming methods I use, however set theory is very new to me, and im having a bit of trouble trying to express constraints on some of my sets. 

For example. 
I'm trying to express something like - ArrayList X contains any number of Y Objects. 
X cannot be empty and Object Y cannot appear in the same arrayList twice. 

Things like that, im having trouble conceptualising in terms of Set-theory.

Any help or resources pointing to help would be greatly appreciated. 
Regards!

---

### Post by Ravenshade on 2010-04-08
Try Z-notation, more than like you're going to be using dom in this case. (Been a year since I looked at Z)

---

### Post by Sporkman on 2010-04-09
> **Sugz said:**
> For example. 
I'm trying to express something like - ArrayList X contains any number of Y Objects. 
X cannot be empty and Object Y cannot appear in the same arrayList twice. 


X != {}
X is a superset of Y

The Object Y not appearing twice is implicit, as sets do not contain duplicates.

---

### Post by CptPicard on 2010-04-09
> **Sporkman said:**
> 
The Object Y not appearing twice is implicit, as sets do not contain duplicates.

But if it's an indexable list A, then one can say that for all i,j, i != j => A_i != A_j

---

### Post by nmaster on 2010-04-09
Java has a set interface: [http://java.sun.com/j2se/1.4.2/docs/api/java/util/Set.html](http://java.sun.com/j2se/1.4.2/docs/api/java/util/Set.html)

you can look at the existing implementations or make your own.

---

### Post by Sporkman on 2010-04-09
> **CptPicard said:**
> But if it's an indexable list A, then one can say that for all i,j, i != j => A_i != A_j

Only one or both of the elements in those indices are members of set Y. According to his description, it can have duplicates of elements not in Y.

...but then X would not be a "set" if there are duplicates of anything...

---

### Post by CptPicard on 2010-04-09
Then again, he is speaking of an "arraylist"... :)

But yes, I guess it can be read as in there can be duplicates of things not in Y. But I suppose the actual exercise is about defining non-duplicates in the sense I gave it.

---

### Post by Sugz on 2010-04-12
Really, thank you very much for all your help :) Sorry I was using an arrayList, in my case, it is my most used method of temporarily storing data sets. However, I will look closely at each of your methods and references, and I will be in touch. :popcorn:

---

### Post by mmix on 2010-04-12
try functional programming language like ocaml/f#, 
or proof checker like coq/metamath.

[http://en.wikipedia.org/wiki/Set_theory](http://en.wikipedia.org/wiki/Set_theory)

---

