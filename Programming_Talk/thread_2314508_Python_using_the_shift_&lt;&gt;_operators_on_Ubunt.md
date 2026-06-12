---
title: "Python using the shift &lt;&gt; operators on Ubuntu 15.04"
date: 2016-02-21
forum: Programming Talk
---

### Post by eightbits2010 on 2016-02-21
[SIZE=2]Python 2.7.9  ,Ubuntu 15.04[/SIZE]
 
 
 [SIZE=3]I am using the assignment _“tmp=(dta>>i&1)”_ to iterate the value of dta (an int)
[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]to test a bit position (i) to select binary value (1 or 0) for that bit position. The values(s)[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]are appended to a list but are stored in a reverse sequence.[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
 [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]I have a tried other variations of the assignment but this one seems to be the only way to go.[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
 [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]QUESTION: In trying to understand  that syntax, does that mean that the value[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]                      of dta is actually shifted left and then the bit position (i) is anded (&) with that value?[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]                      Some years past I had to do something like this using a for loop in C and the shift operator[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]                      to get the 1 or 0 value. But, I was using a left shift to build up a string and did not have[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]                      to reverse the string or array.  [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
 [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]I realize that I can use Python built-in “bin(x)” to do the same thing . But I  want to understand if there is[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]a method to cycle through the data value and from the LSB to the MSB (left shift). Is this an issue with big endian/little endian? If my memory serves me, I also did not shift the data tested but instead was shifting the bit to and with the[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]data. I can not find the original code (C) as that was some time ago. It is not the end of the world, I just thought[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]I would be able to do this with no major head banging. I guess I am suffering from RAMnesia :-)[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
 [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]The above mentioned assignment syntax was from stackoverflow . And as I mentioned it works , I just want to[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]know why it is the data being shifted instead of the bit (i) ?[/SIZE]
[SIZE=3] [/SIZE][SIZE=3]
 [/SIZE]
[SIZE=3] [/SIZE][SIZE=3]The below snippet is the for loop used to extract the 1 or 0 values to a list. If the complete listing is required  [/SIZE]
[SIZE=3] [/SIZE][SIZE=2][SIZE=3]I can post that as well.[/SIZE]

[/SIZE]

 ```
[SIZE=4]for i in range(0,size):

    tmp=(dta>>i&1)    #don't have to convert to int, only 0 or 1, True or False 

    l.append(tmp)     #add  value to list

#================================= end FOR loop ==============================[/SIZE]  


```

---

### Post by Vaphell on 2016-02-22
[https://docs.python.org/2/reference/expressions.html#operator-precedence](https://docs.python.org/2/reference/expressions.html#operator-precedence)

>> is binds more strongly than &, so dta gets shifted first and then the result is binary-ANDed.


> And as I mentioned it works , I just want to
know why it is the data being shifted instead of the bit (i) ?


&1 takes only the least significant bit so you are guaranteed to get 0/1 as the result. By rightshifting the original value you are effectively dividing, pushing further digits into the relevant slot and capturing them one by one.

101110**1**01 >> 2 = 101110**1**
101110**1** & 1 = **1**

If you leftshifted the mask instead, you'd get the bit*2**position value of the matched bit instead of 0/1.

1 << 2 = 100
101110**1**01 & 100 = **1**00 = 4

---

### Post by eightbits2010 on 2016-02-22
It makes sense and I know it works that way. I always understood the the old C code and I think I had set a bit to one, and then looped through the value with the '1 '1bit shifted left through the
data value one shift at a time and then tested to see if it 'anded' with where ever it was testing in the data.  But, I am thinking, is this just something Python does differently?
None the less, your explanation makes it clear and I will 'think' on it some more. I will mark this SOLVED and thank you for the explanation.

---

### Post by Vaphell on 2016-02-23
i don't think python works differently in the domain of binary operators. I'd assume the job is farmed out to underlying C code.
Maybe in that specific case you took advantage of the truthiness of positive integers? 0 is going to be 0/false, but 2/4/8/16/... can be used as true. If you had 

```
if (x & (1 << i)) { ... }
``` it would be functionally identical to ```
if (x >> i & 1) {... }
```, which would also work in python

---

