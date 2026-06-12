---
title: "LibreOffice Calc calculation errors"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by Manas B on 2012-11-18
Hello,

I am using LibreOffice Calc for calculating numbers in recurrence relations and finding their residues through modular arithmetic. I am finding that the results produced by LibreOffice Calc are erroneous. I would like to find out what causes this error and how it can be fixed.

For forming the numbers of the recurrence relation, I manually type in two numbers to serve as the seeds. These numbers are typed into row 1 & 2, column A. The rest of these integers are calculated by using the formula A3=A1+A2 then autofilling for every subsequent row. The residue is calculated using B3=MOD(A3,360) and again autofilling the rest of the entries. Everything is fine until row 75 where I have the number 1304969544928660. The two numbers in row 73 & 74 are 498454011879264 & 806515533049393. The next number should be 1304969544928657, why does LibreOffice Calc produce 1304969544928660 instead?

Thank you,
Manas

---

### Post by cwsnyder on 2012-11-18
Because Calc uses 32-bit floating point numbers in the arithmetic for the type of calculation you are asking it to do, and you are exceeding the significant figure capability of 32 bit numbers.  I don't know of ANY spreadsheet program which will perform the type of integer arithmetic for which you are asking.  You can program it in the correct scientific programming language, but not in just a spreadsheet.

Know the capability of your tools.

---

### Post by Manas B on 2012-11-22
I understand. I was using Calc as it provides the functionality that I was looking for - Coloring Cells based upon range. I can generate the numbers seperately then perform the coloring in Calc. I am not fluent in any scientific programming language but I know some perl.

Thank you for the reply. :)

---

### Post by Impavidus on 2012-11-23
Of course you can still find the correct values for your B column in any spreadsheet program by calculating the modulo after every summation:
```

1
2
MOD(A1+A2, 360)
MOD(A2+A3, 360)
etc.
```After all, calculating the modulo and summation are commutative operations (well, not exactly, because you have to keep the last modulo). This solves the rounding problem and allows you to continue *ad infinitum*. Even a scientific programming language will break down when your numbers don't fit in a 32 bit integer, or a 64 bit integer. The best way of fixing rounding problems is usually changing the order of operations to avoid big numbers, not using higher precision numbers.

---

### Post by Manas B on 2012-11-24
> **Impavidus said:**
> Of course you can still find the correct values for your B column in any spreadsheet program by calculating the modulo after every summation:
```

1
2
MOD(A1+A2, 360)
MOD(A2+A3, 360)
etc.
```After all, calculating the modulo and summation are commutative operations (well, not exactly, because you have to keep the last modulo). This solves the rounding problem and allows you to continue *ad infinitum*. Even a scientific programming language will break down when your numbers don't fit in a 32 bit integer, or a 64 bit integer. The best way of fixing rounding problems is usually changing the order of operations to avoid big numbers, not using higher precision numbers.
That is a very good suggestion. If I only need the residues, I can just calculate those without worrying about overflowing the capacity of the computer. Thank you.

---

