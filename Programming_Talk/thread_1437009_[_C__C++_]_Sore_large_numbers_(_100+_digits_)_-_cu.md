---
title: "[ C / C++ ] Sore large numbers ( 100+ digits ) - custom data type ?"
date: 2010-03-23
forum: Programming Talk
---

### Post by HellBoz on 2010-03-23
Have been searching for a way to create a custom data type to store large numbers but still got nothing except 20+ <read> Google pages ..
Is it even possible ? What I should be looking for ?

---

### Post by johnl on 2010-03-23
You should be looking for libgmp, the GNU Multiple Precision Arithmatic Library. (sudo apt-get install libgmp3-dev).  There is a C++ wrapper also, I believe (libgmpxx).

Check gmplib.org for documentation and examples.

---

### Post by HellBoz on 2010-03-23
Thanks, tough I would be more interested in finding out how to write one on my own.

---

### Post by Ferrat on 2010-03-23
Well just storing them should be fairly easy, making your own class containing a bit array, storing it in hex or higher instead etc are valid possibilities, if you want to do math on it or not comes in to play as well so what are they for in the first place?

---

### Post by johnl on 2010-03-23
> **HellBoz said:**
> Thanks, tough I would be more interested in finding out how to write one on my own.

Writing one on your own can be fun.  You basically need to store an array of integers, then think about how you would do the math 'by hand' -- carrying between your 'digits' and such.

However, if you just want to use something, I wouldn't bother writing your own.  It will take you a lot longer, have more bugs, and be an order of magnitude slower than an existing implementation like GMP.

---

### Post by HellBoz on 2010-03-23
> **Ferrat said:**
> Well just storing them should be fairly easy, making your own class containing a bit array, storing it in hex or higher instead etc are valid possibilities, if you want to do math on it or not comes in to play as well so what are they for in the first place?

They are just for learning purposes. Wherever one talks about integer overflows, someone else suggests to write a custom data type. Basic arithmetic as an introduction ..

> **johnl said:**
> Writing one on your own can be fun.  You basically  need to store an array of integers, then think about how you would do  the math 'by hand' -- carrying between your 'digits' and such.

However, if you just want to use something, I wouldn't bother writing  your own.  It will take you a lot longer, have more bugs, and be an  order of magnitude slower than an existing implementation like  GMP.

As stated above, I just want to understand the procedure of creating new data types, which can hold values, not supported by the default set of <tools> available in the C library.

---

### Post by MindSz on 2010-03-23
Using an array as a base structure seems the easier way to do this. So let's say you create an array of chars:

```
strcpy(myLargeNum, "12345678987654321")
```

then you just need to realize how you convert that to an actual number.

e.g. for binary numbers:

```
1010 = 0*1 + 1*2 + 0*4 + 1*8 = 10
```

Now since these are your own numbers, you'll probably need to create our own math library.

This way also allows you to create your own base (binary, octal, deci, hexa).

fun stuff really.

---

