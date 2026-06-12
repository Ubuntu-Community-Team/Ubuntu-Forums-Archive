---
title: "[ C ] &lt;unsigned short int&gt; and negative numbers."
date: 2010-02-13
forum: Programming Talk
---

### Post by SemiBuz on 2010-02-13
```
unsigned short int number; /* 0 .. 31,767 */

```Just wondering, why does it accept negative numbers ? I can assign any negative number and print it out with no warnings or whatsoever.
I thought it should reject it, at least with an overflow .. ?

---

### Post by dwhitney67 on 2010-02-13
I'm not sure what you are asking.

An unsigned short can store values from 0 to 65535 (2^16 - 1).

If you assign it a negative value, say -1, the compiler will not complain.  Sorry if this upsets you.

When you attempt to print the value, the result will be a positive number, because the print-streamer is interpreting the value as an unsigned value.

Try this code:
```

#include <stdio.h>

int main()
{
   unsigned short value;

   for (int i = 5; i > -5; --i)
   {
      value = i;

      printf("value = %u\n", value);
   }

   return 0;
}

```

P.S.  The reason why a negative number is interpreted as a positive value is because when the most-significant-bit is set (as is with a negative number), that value is not interpreted as a sign-bit with unsigned values.  It only has context with a signed value.

---

### Post by CptPicard on 2010-02-13
I was assuming what you said would happen -- that with a negative number put into an unsigned int, you'd get the bits interpreted as unsigned, but... uh...

```

int main(int argc, char **argv) {
  unsigned int x = -5;
  printf("%i\n", x);
}

```

```

picard@bridge:~$ ./uinttest
-5

```

Hmmm. :confused: I wonder if the compiler is trying to be smart here...

---

### Post by dwhitney67 on 2010-02-13
I repeated my test program, using the %i and %d.  The result were the same.

However, when I switched to using an 'unsigned int', then I yielded the same results observed by CptPicard when using the %d or %i formatters.  Bizarre, but I won't lose sleep over it.

---

### Post by CptPicard on 2010-02-13
Ah, of course, the format specifiers do casting. %i interprets as signed, regardless of the datatype declaration. You can, after all, use %f on an int and so on... :)

---

### Post by SemiBuz on 2010-02-13
So basically, if I have an [COLOR=RoyalBlue]unsigned int[/COLOR] and I use [COLOR=SeaGreen]%d[/COLOR], it becomes ( temporary ) [COLOR=RoyalBlue]signed double[/COLOR] ?

---

### Post by dwhitney67 on 2010-02-13
> **SemiBuz said:**
> So basically, if I have an [COLOR=RoyalBlue]unsigned int[/COLOR] and I use [COLOR=SeaGreen]%d[/COLOR], it becomes ( temporary ) [COLOR=RoyalBlue]signed double[/COLOR] ?

Please read the contents at this site.  I think you are misunderstanding what the %d implies.

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

---

### Post by LKjell on 2010-02-13
You have to use %u to get what you want.

---

### Post by SemiBuz on 2010-02-13
> **dwhitney67 said:**
> Please read the contents at this site.  I think you are misunderstanding what the %d implies.

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

I thought I understand but after reading that it's just some kind of formatting ( cplusplus.com reference ), well .. how it's possible to format a negative number to be positive ? :-s

> **LKjell said:**
> You have to use %u to get what you want.

Figured it out already ( *dwhitney67's* post ) - thanks for the clarification tough.

---

### Post by MadCow108 on 2010-02-13
the format specifier just defines how the printf function interprets the data saved in the variables. Standard C has no possibility to determine the type by itself in this context (unlike C++ or C with gnu extensions)
%d and %i is a signed integer so it casts whatever you give to the function as argument to this type, no matter what it really is.
you can do this yourself too:
```

long long a = 554642324533536LL;
double d = *(double*)&a;
printf("%f %f\n", a, d); // same result (although it gives warning when compiled with gcc and appropriate flags

```
this takes the address of a, interprets it as a pointer to double, the * dereferences it as a double. The result will not be the value of a because double uses a different memory layout than integers (sign, mantissa, exponent).

signed and unsigned integers also differ in memory, the signed integers use one of their bits to define the sign. The unsigned uses all bits for the number itself.

---

### Post by CptPicard on 2010-02-13
> **SemiBuz said:**
> I thought I understand but after reading that it's just some kind of formatting ( cplusplus.com reference ), well .. how it's possible to format a negative number to be positive ? :-s

It's just bits in memory, and depending on what kind of a formatting option you give it, it reads the bits "as if" they were representing the kind of thing you're formatting into. That is why, for example, even if the compiler will enforce something as unsigned in computations, if you've given the variable some bits that represent a negative signed number "if interpreted as such", printf will do so if you tell it to.

---

### Post by LKjell on 2010-02-13
The real difference if I remember is what you get when you do a right bit shifting. With sign type you get ones but with unsign you get zeros. But of course there are no standard. So to make sure what you get when you do a bit shift to the right is to mask it.

---

