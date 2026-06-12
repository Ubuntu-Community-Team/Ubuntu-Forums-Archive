---
title: "s[i] - '0'   a C programming question"
date: 2008-06-21
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-06-21
I recently bought The C Programming Language (Second Edition).

On page 43 there is a function they wrote called [FONT="System"]atoi[/FONT]

```
int atoi(char s[])
{
   int i, n;
   
   n = 0;
   for (i = 0; s[i] >= '0' && s[i] <= '9'; ++i)
   {
      n = 10 * n + (s[i] - '0');
   }

   return n;
}
```

This is what I can't figure out: 
```
s[i] - '0'
```

I don't exactly understand the explanation behind it and have never run into anything like this before.

Could anyone make this more clear?

Thanks a lot guys!

---

### Post by mike_g on 2008-06-21
Thats converting a character to an integer value. In ASCII the character 0 is represented by the number 48. So if you minus '0' (or 48) from it you are left with the number 0.

---

### Post by CptPicard on 2008-06-21
This is because C strings are character arrays, and characters are simply one-byte... bytes. Numbers, that is, in the ASCII encoding. Therefore, '0' is actually the numerical value of the byte that represents '0' in the encoding, and numbers are encoded in ascending order from '0', so the number of '1' is then '0' + 1. So to get a numerical value of a digit of some character c, you can just do c - '0' -- you are essentially just computing how many characters there are in sequence between c and '0'.

---

### Post by oodlesOfmoodles on 2008-06-21
Ohhh.
Thanks man!
(and mike_g)

An example for those who may read this later:


The ASCII characer '0' (zero) has an ASCII value of 48.
The ASCII characer '1' has an ASCII value of 49 and the character '2' has a value of 50. (Get the picture?)

We could get the numerical value of the character '2' by subtracting its ASCII value 50 from the character '0' value of 48.

50 - 48 = 2

Likewise we could get the character '1' numerical value by subtracting its ASCII value 49 from the character '0' value of 48.

50 - 49 = 1


The ASCII character 'a' has an ASCII (decimal) value of 97.
To get its numerical value, we apply the same method of subtracting from the character '0'.

97 - 48 = 39

There you go!

---

