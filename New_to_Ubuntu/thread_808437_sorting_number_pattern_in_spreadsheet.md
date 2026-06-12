---
title: "sorting number pattern in spreadsheet"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by badperson on 2008-05-26
Hi,

I'm writing a spreadsheet, and there is an "id" column that has numbers in the following format:

1.4.a
1.4.a.1
1.4.a.2
1.4.b
1.4.c


How do I tell spreadsheet to sort these values in the order they appear here? 
thanks. 
bp

---

### Post by Happy_Man on 2008-05-26
Data --> Sort should do the trick for you.

---

### Post by prshah on 2008-05-26
> **badperson said:**
> Hi,
1.4.a
1.4.a.1
1.4.a.2
1.4.b
1.4.c

How do I tell spreadsheet to sort these values in the order they appear here? 


> **Happy_Man said:**
> Data --> Sort should do the trick for you.

Interesting; Data-Sort-Ascending gives```
1.4.a
1.4.a.1
1.4.a.2
1.4.b
1.4.c
```

which is fine, but Data-Sort-Descending gives```
1.4.a
1.4.c
1.4.b
1.4.a.2
1.4.a.1

``` ...I'd say this is wrong

---

### Post by badperson on 2008-05-26
Hi,

here is a more complete sample that illustrates the sort problem. 

This is sort->ascending

1
1.1
1.2
1.3
1.4
1.5
2
3
4
1.4.a
1.4.a.1
1.4.a.2
1.4.b
1.4.c


I want all the 1.4.whatever to come after 1.4 and before 1.5.
thanks, 
bp

---

### Post by niteshifter on 2008-05-27
Hi,

Don't treat them as numbers, set the cell format for that column (or that range) to text. Your sequence as given then sorts (Data -> Sort) to:

1
1.1
1.2
1.3
1.4
1.4.a
1.4.a.1
1.4.a.2
1.4.b
1.4.c
1.5
2
3
4

The above pasted from OOo 2.3

---

