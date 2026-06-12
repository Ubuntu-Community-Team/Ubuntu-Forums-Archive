---
title: "[SOLVED] Open Office Calc help"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-11-12
Not an Ubuntu prob but, I have a simple spreadsheet that holds the prices for all products for all suppliers, with each row containing the Item name and then prices for five suppliers. I want to add either add another column to indicate the cheapest supplier for each product, or highlight the cheapest price > 0 in the row. I am guessing that this should be fairly easy, but other than simple stuff I dont know to much on the workings of a spreadsheet, so any help welcomed.

---

### Post by rbradt on 2008-11-12
Do you know about Conditional Formatting in a spreadsheet?

---

### Post by celticbhoy on 2008-11-12
In a word - no.

But I will have a look through OoCalc help files.

---

### Post by celticbhoy on 2008-11-12
OK,

I have had a look at OoCalcs help pages and conditional formatting may work, but my problem is working out the condition. How would I write a condition that takes five numbers and selects the lowest ???

---

### Post by beercz on 2008-11-12
> **celticbhoy said:**
> OK,

I have had a look at OoCalcs help pages and conditional formatting may work, but my problem is working out the condition. How would I write a condition that takes five numbers and selects the lowest ???

Does the MIN() function help?  (See OO's help and search for the MIN function)

---

### Post by celticbhoy on 2008-11-12
I managed to sort it using SMALL, MIN would work as well but SMALL automatically discards zero's.

---

### Post by beercz on 2008-11-12
Well done!

---

