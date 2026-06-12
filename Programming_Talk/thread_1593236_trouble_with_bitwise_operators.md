---
title: "trouble with bitwise operators"
date: 2010-10-11
forum: Programming Talk
---

### Post by abraxas334 on 2010-10-11
Just a quick question about some code i am trying to understand.
Looks something like this:
[PHP]
...
   int myRand;
   myRand = rand(); //creates rand int between 0 and RANDMAX
   int shift = 1<<1;
   if(myRand & shift)
   {
       std::cout<<"True \n";
   }
   else
   {
      std::cout<<"False ";
   }

...
[/PHP]

so the shift variable is obviously 2. Which in binary is 10.
Why is 1717471323 & 2 true. and 833761856 & 2 false?
I just don't understand what the if statement tries to do. What makes it true and what makes it fail?
I understand that say 60 & 3 is equal to 12 but how could it result in a true or false?
Any help would be greatly appreciated.

---

### Post by Zugzwang on 2010-10-11
Ok, let's calculate:

The decimal number 1717471323 is in binary: 1100110010111101000100001011011   

The decimal number 833761856 is in binary: 110001101100100011001001000000

Now lets bit-wise "and" them with 2 (Which is 10 in binary):

```

   1100110010111101000100001011011
&                               10
----------------------------------
   0000000000000000000000000000010

```

```

   110001101100100011001001000000
&                              10
---------------------------------
   000000000000000000000000000000

```

Ok, so we get "2" in decimal as a result in the first case and "0" in the second case.

**In C and C++, an "if" always checks if the argument is unequal to 0**. As in the first instance, the argument is "2" and in the second case, it is "0", so the if-branch is taken in the first case but not in the second one.

BTW: "60 & 3" is "0" and not "12".

---

### Post by ibuclaw on 2010-10-11
The '&' operation zeros out all bits except those implicitly turned on by the right hand value.

so, to do some maths:
```

1717471323 & 2
=
01100110 01011110 10001000 01011011
00000000 00000000 00000000 00000010
=
00000000 00000000 00000000 00000010

```
1717471323 & 2 equals 2, hence true.

```

833761856 & 2
=
00110001 10110010 00110010 01000000
00000000 00000000 00000000 00000010
=
00000000 00000000 00000000 00000000

```
833761856 & 2 equals 0, hence false.

---

