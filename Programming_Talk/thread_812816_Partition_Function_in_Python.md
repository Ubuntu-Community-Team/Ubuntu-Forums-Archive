---
title: "Partition Function in Python"
date: 2008-05-30
forum: Programming Talk
---

### Post by nebu on 2008-05-30
Does python have a built in partition function like mathematicas [PartitionP[]]("http://mathworld.wolfram.com/PartitionFunctionP.html")....

i tried looking up python documentation but i cant seem to find it..... im not exactly sure im looking for the right thing.... its giving me results of how to sort arrays....

i cant even find the code on the python cookbook....

could u giv me a link to the code

---

### Post by LaRoza on 2008-05-30
> **nebu said:**
> Does python have a built in partition function like mathematicas [PartitionP[]]("http://mathworld.wolfram.com/PartitionFunctionP.html")....

i tried looking up python documentation but i cant seem to find it..... im not exactly sure im looking for the right thing.... its giving me results of how to sort arrays....

i cant even find the code on the python cookbook....

could u giv me a link to the code

Python has few built in functions. I am sure it has a module for it somewhere though.

---

### Post by WW on 2008-05-30
Google for "integer partition function in python", and feel lucky.

---

### Post by Lster on 2008-05-30
I don't know whether Python contains that function or not. However I needed another function, similar to the Mathamatica function NumberOfPartitions, for a Project Euler question a while ago. If that is what you are after, I'm sure I could find it.

---

### Post by nebu on 2008-05-30
> **Lster said:**
> I don't know whether Python contains that function or not. However I needed another function, similar to the Mathamatica function NumberOfPartitions, for a Project Euler question a while ago. If that is what you are after, I'm sure I could find it.
ya.... actually two problems..... is there a similar function in matlab or maxima.....

---

### Post by geirha on 2008-05-30
Google came up with this one for me:
[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/218332](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/218332)

```

>>> list(partitions(4))
[[1, 1, 1, 1], [1, 1, 2], [2, 2], [1, 3], [4]]

```

---

### Post by Lster on 2008-05-30
[QUOTE=nebu]ya.... actually two problems..... is there a similar function in matlab or maxima.....[/QUOTE]

I'll have to have a look for the second one. Which number is it?

Both functions (PartitionP and NumberOfPartitions) are easy to implement in Python. I found that the code for NumberOfPartitions that I previously coded is in fact written in C. I can translate it if needed... but really it just uses Euler's generating function (as shown in the link you posted).

---

### Post by Bichromat on 2008-05-30
> **nebu said:**
> ya.... actually two problems..... is there a similar function in matlab or maxima.....
maxima has "integer_partitions(n)" which gives a list of all possible partitions.

---

### Post by nebu on 2008-05-31
> **Lster said:**
> I'll have to have a look for the second one. Which number is it?

Both functions (PartitionP and NumberOfPartitions) are easy to implement in Python. I found that the code for NumberOfPartitions that I previously coded is in fact written in C. I can translate it if needed... but really it just uses Euler's generating function (as shown in the link you posted).



76 and 78....

you can use a similar approach to solve 77 too

---

