---
title: "Libreoffice help"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by tempore on 2012-09-12
Is there a way to apply a function to an entire column?

I have a function like this:

B1=A1*.5+5

Entering 1 in A1 results in B1 having the value of 5.5. That's works fine. But I'd like the same function to work in A2 so that

B2=A2*.5=5 and
B3=A3*.5=5 

and so on so that I can enter different values in column A and have the same function applied. I can manually enter the function for each cell but this is tedious. Is there a better way?

---

### Post by Kopkins on 2012-09-13
Did this in about a minute and a half. Check my screenshot.

Enter your function into the cell you want, and then select a different cell.

Select the cell with the function again and press Ctrl+c to copy.

Press the down arrow, and Ctrl+v to paste. The program automatically adjusts the function for the change in cell location. So now you've applied a similar function to both B1 and B2. 

Kopkins

---

### Post by Vaphell on 2012-09-13
that's basic function of every spreadsheet program
when you duplicate cells it updates column and row identifiers to match the logic.
exception is when you use $ sign to lock row/column
eg. =A1+1 will be udated to A2 (if you copy vertically) or to B1 (if you copy horizontally) but when you use $A1 in your formula only '1' can be changed, 'A' stays locked no matter what, same thing with A$1 and $A$1 (single fixed cell)



aside from ctrl+c/ctrl+v, selection rectangle has that little square in bottom right corner, you can grab it and drag it to extend the formula to other cells.

```
  A       B        C
---------------------
1|1	0.5	0.25
2|2	1	0.5
3|3	1.5	0.75
4|4	2	1
```
it takes 20 seconds. Enter 1 in a1, enter =a1+1 in a2, grab the bottom-right square and extend to cells below. Enter =a1*0.5 in b1, extend to cells below. Enter =b1*0.5, extend to cells below. Done.

---

