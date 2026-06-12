---
title: "Libre office calc"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by trav9595 on 2014-06-28
I am trying to do a simple sum of a row of numbers.I highlight the fields and clik the sum symbol but the sum is wrong. How do you do a simple sum in Libre Office calc.

---

### Post by Dennis N on 2014-06-28
For a column of numbers:

Put cursor in cell where sum is to appear. 
Press the sum icon. 
Use arrow key to move up to the first number, then use shift + down-arrow and select (highlight) the ones to be added, then enter.

Oops! - The above works with Gnumeric. For Calc you need to put cursor in cell where sum is to appear, press sum, then highlight the numbers to be added with the mouse, then enter.

---

### Post by claracc on 2014-06-28
Other way to perform adition:

Put the cursor in the cell you want to put the sum
write = sign
select function symbol in tools bar, select sum function
and in the window appearing you fill the name of cells you want to add: a1, b1,c1,...
click enter and you will have the operation made.

See attached image

---

### Post by Impavidus on 2014-06-28
Or just select the cell where you want the sum and type```
=sum(<first cell>:<last cell>)
```But I think OP has managed to calculate a sum, but the result is wrong. Maybe some cells have not been marked as a number but as a text string? In that case they would be ignored when calculating the sum. I think text is left-aligned, whereas numbers are right-aligned. It might be caused by something like the wrong radix character.

---

### Post by gordintoronto on 2014-06-28
Put the cursor where you want the sum, click the sum icon, press enter.

+1 for the possibility of a text string.

---

### Post by trav9595 on 2014-06-28
got it.... the problem was a positve entry in the middle I had not noticed....it messed up the total...

---

### Post by claracc on 2014-06-29
Glad you got fixed your problem.

Please, mark the thread as solved with thread tools in the right upper part of the page.

Thanks.

---

