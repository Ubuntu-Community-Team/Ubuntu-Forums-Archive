---
title: "[Math] What does the book mean?"
date: 2012-04-21
forum: Programming Talk
---

### Post by t1497f35 on 2012-04-21
Hi,
See text in red box on screenshot, how does one determine which row is greater (i2 > i1)? By its index top down? By the sum of its numbers? In other way?

---

### Post by DaviesX on 2012-04-21
I am not quite sure about it, but I think that suppose to infer to 
Intensive row simplified echelon matrix (just translate from other language directly =,=)

echelon matrix
1. all-zero-row should be in the last row
2.the column subscript of the first non-zero element should be increasing as the row subscript is increasing, for example

2 0 2 1
0 5 2 -2
0 0 3 2
0 0 0 0

row simplified matrix
1.it is echelon matrix
2.each column should be all zero except the first non-zero element
for example, 

2 0 0 1
0 5 0 -2
0 0 3 2
0 0 0 0

Intensive row simplified echelon matrix
1.it is row simplified matrix
2.every first non-zero element should be 1
For example, 
1 0 0 1
0 1 0 -2
0 0 1 2
0 0 0 0

Hope this can help you ^_^

---

### Post by DaviesX on 2012-04-21
I believe that means the specified element of the subscript
if In < In+1 then
Jn < Jn+1

:)

---

### Post by xytron on 2012-04-22
Indeed you determine which row is greater by its index.

It's referring to the leading entries of a pair of rows, leading entries have to be a 1. 

So it says that the leading 1 of any nonzero row has to be in a column with a greater index (to the right) of the leading 1 of the previous row (the row with the lesser index).

---

### Post by t1497f35 on 2012-04-22
Thanks all

---

