---
title: "Finding duplicates in a column in LibreOffice Calc"
date: 2014-07-11
forum: Programming Talk
---

### Post by vasa1 on 2014-07-11
Say I have a column like this in cells A2 through A10. The row header is "Flat" in cell A1:

```
Flat
05A-001
05A-002
05A-003
05A-004
05A-001
05A-102
05A-103
05A-104
05A-001
```
**05A-001** is present three times in this column. To show this, I put the following formula in cell **B2**. Cell **B1** is the row header "First Formula":

```
=COUNTIF(A$2:A$10,A2)
```
and copy it down till cell B10.

Now, all unique entries have the value of **1** in column B next to them whereas cells containing **05A-001** have the value of **3** in column B next to them.

```
Flat      First Formula
05A-001         3
05A-002         1
05A-003         1
05A-004         1
05A-001         3
05A-102         1
05A-103         1
05A-104         1
05A-001         3
05A-202         1
05A-203         1
05A-204         1
```
To make it more obvious for long lists, I place the following formula in cell C2 with cell C1 being row header "Second Formula":

```
=IF(B2=1,"","dupe")
```
and copy it down till C10.

Now, only cells with 5A-001 will have the word "dupe" in the corresponding row (in column C).

```
Flat      First Formula    Second Formula
05A-001         3              dupe
05A-002         1               
05A-003         1               
05A-004         1               
05A-001         3              dupe
05A-102         1               
05A-103         1               
05A-104         1               
05A-001         3              dupe
05A-202         1               
05A-203         1               
05A-204         1               
```

Now, I can **autofilter** using the word "dupe" in column C and will see only the rows which have "dupe" in column C.

My question is this: is it possible to have a single formula that does the job of both the above formulas? In other words, could I get the job done with just column B having the word "dupe"?

*I know I can use conditional formatting to highlight duplicates in a column.*

---

### Post by spjackson on 2014-07-11
> **vasa1 said:**
> 
My question is this: is it possible to have a single formula that does the job of both the above formulas? In other words, could I get the job done with just column B having the word "dupe"?

Yes.
```

=IF(COUNTIF(A$2:A$10,A2)=1,"","dupe")

```

---

### Post by vasa1 on 2014-07-11
> **spjackson said:**
> Yes.
```

=IF(COUNTIF(A$2:A$10,A2)=1,"","dupe")

```
Thank you :)

---

