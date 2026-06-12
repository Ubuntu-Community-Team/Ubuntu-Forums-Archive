---
title: "C++ help"
date: 2011-02-15
forum: Programming Talk
---

### Post by CM Xtasy on 2011-02-15
I'm working on an assignment, and I'm having trouble understanding when to use double or integers.  Here are the variable definitions:
   int a = 5;
   int b = 12;

   double x = 3.4;
   double z = 9.1;

Now I'm not going to ask you to do my homework but this is the example I'm stuck with.  What would be the difference between "static_cast<double>(b / a)" and "static_cast<double>(b) / a" 

Aren't they both expressed in decimal?  Which would make 2.4 be the answer to both.

---

### Post by sisco311 on 2011-02-15
In the first case you divide two integers then convert the result to double; and in the second one you convert an integer to double then divide it with an integer.

But, the proof of the pudding is in the eating. ;)

---

### Post by CM Xtasy on 2011-02-15
So it goes by what the last variable is?  For example a double(a) * int(b) = integer answer?

---

### Post by forrestcupp on 2011-02-15
> **sisco311 said:**
> In the first case you divide two integers then convert the result to double; and in the second one you convert an integer to double then divide it with an integer.
Which should explain to you why you don't get the same answer.

---

### Post by forrestcupp on 2011-02-15
> **CM Xtasy said:**
> So it goes by what the last variable is?  For example a double(a) * int(b) = integer answer?

If you divide two ints, you'll get an int. If you don't convert it to double until after the division takes place, you will have already lost the decimal places before it's converted.

If you convert one of the ints to double and then do the division, you can end up with decimal places. ;)

---

### Post by CM Xtasy on 2011-02-15
Okay thank you I'm starting to understand it!  

So "b / static_cast<double>(a)" would end in a decimal
and "b / static_cast<int>(a)" would end in an integer?

I'm sorry for asking so many questions, I'm more of a visual learner so it's hard just reading it and understanding... I have to see this is right and this isn't.

---

### Post by Vaphell on 2011-02-15
it's very simple - if / operator sees ints on both sides, it will produce int.

integer/integer -> integer
integer/floating_point -> floating_point
floating_point/integer -> floating_point

note that you need to be careful in each step of more complex calculations because 2 integers will irreversibly round the number and further steps may work on erroneous intermediate results.
(3/2)*2=2 - here 2 ints lost 0.5 from true value of 3/2, thus end result is wrong
(3.0/2)*2=3 - float preserved precision, end result is ok.

---

### Post by worksofcraft on 2011-02-15
To me the main distinction is between enumerable counting of things v.s. a continuous scale. IMO languages that fail to distinguish these two unique concepts and try to merge all number types into one fail in that respect.

IMO operators like == and != should be deprecated for floats and doubles and that conversion between them and integer types should always be explicit.

p.s. note that some times you will also find so called "fixed point" arithmetic and they might designate it as something like 24.8 meaning 24 bits for the integer part and 8 bits for the fraction.

---

