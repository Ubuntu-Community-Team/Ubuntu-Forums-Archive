---
title: "Python help"
date: 2013-03-07
forum: Programming Talk
---

### Post by prismctg on 2013-03-07
How to input two numbers using space like [ 4<space>8] in two list type variables ?

---

### Post by Vaphell on 2013-03-07
you should be more specific
input as in user input?
is [4 8] supposed to produce separate [4] and [8] or what?

---

### Post by iMac71 on 2013-03-07
perhaps the following code is what you're looking for (I assume that you use python 2.7.3):[PHP]from string import split
list1, list2 = [[float(num)] for num in split(raw_input())]
print list1, list2[/PHP]

---

