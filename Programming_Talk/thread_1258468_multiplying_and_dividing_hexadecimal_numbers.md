---
title: "multiplying and dividing hexadecimal numbers"
date: 2009-09-05
forum: Programming Talk
---

### Post by nikhilbhardwaj on 2009-09-05
i can add and subtract(16's complement) hexadecimal numbers easily
but multiplying and dividing them is a pain
i mean you have to convert to decimal and then reconvert
is there a trick or a method by which you can directly multiply and divide hex no's with a pen and paper without conversion

---

### Post by smartbei on 2009-09-05
Why do you need to convert? It works without...
Note - all numbers are in hex.
```

 2F
*1A
---    A*F = 96

 9
 2F
*1A
---   A*2 = 14
  6

 2F
*1A
---   1*F = F   1*2 = 2
1D6

 2F
*1A
---
1D6
2F
---
4C6

```

---

### Post by stroyan on 2009-09-05
If the hex digit multiplication tables are too big for comfort, you could easily convert from hex to binary and back.  Then the multiplication and long division operations are very simple.  But you do need to do four times as many operations for the same size operands.

---

### Post by nipunreddevil on 2009-09-05
conversion to some other form(dec or binary)seems best bet to me

---

### Post by wmcbrine on 2009-09-05
If you want to do it without conversion, and without a calculator or computer, you'll have to do it the same way you presumably did with decimal, and learn the multiplication tables. Which you might have to draw up first. Personally, I recommend a calculator.

---

### Post by nikhilbhardwaj on 2009-09-05
> **nipunreddevil said:**
> conversion to some other form(dec or binary)seems best bet to me

i'll have to agree with you 
learning hex tables is too daunting for me

---

