---
title: "C++ cast not platform independent?"
date: 2010-08-20
forum: Programming Talk
---

### Post by abraxas334 on 2010-08-20
I have been running program on a 64 bit platform for a while working fine. A few days ago I had to transfer it to a 32 bit platform, which caused some strange issues. One function would return the wrong variable, even though the rest of the program was running fine.
I have located the problem, but I don't know how to solve it or why it happens in the first place and explanation would be great. Here it goes:

```

//....
float intFloatConv = 100.0;
//interaction energy is a function that will return a float which is based on data read from a file.
//in this particular example say it will return a value of -0.29 
int interactionMatrix = int(intFloatConv*interactionEnergy(seq.c_str()[r], seq.c_str()[s]));
//when I do std::cout<<intFloatConv*interactionEnergy(seq.c_str()[r], seq.c_str()[s])<<std::endl;
//I get the answer -29 which is what I want
//.....

```
on the 64 bit machine the cast with int(...) gives me a value of -29 for the interactionMatrix integer variable. If I do the same on a 32 bit machine i get a result of -28. I tried casting to a long rather than an int instead, but still the value is still -28. Why is this? How can i fix the problem. I can't change the imput file, which provides me floats and everything else in the program I coded for ints, so i don't want to make any major changes.
Anyone knows why this is and where I am going wrong?

---

### Post by Queue29 on 2010-08-20
Well first things first.. Are you sure your function interactionEnergy(...) is returning .29 and not .28 ?

---

### Post by dwhitney67 on 2010-08-20
Why don't you print out what interactionEnergy() is returning?

Also, consider declaring 'intFloatConv' as a double, and please change the variable name!

As for converting to an int, you will be truncating the floating point value.

P.S.  I hope that code example you provided is not representative of your real program.  It is very hard to read code when it lacks vertical white-space.

P.S. #2  This little program also displays 28 for the int value, because the resulting number, 28.9999999 is truncated.  I'm on a 32-bit system.
```

#include <iostream>

const double ONE_HUNDRED = 100.0;

double interactionEnergy(const char a, const char b)
{
   return 0.289999999f;
}

int main()
{
   double ie = interactionEnergy('a', 'b');
   int    im = ONE_HUNDRED * ie;

   std::cout.precision(8);
   std::cout << "ie = " << ie << "\n"
             << "im = " << im << std::endl;
}

```

---

### Post by abraxas334 on 2010-08-20
yes because even if you try and write something like this:

[PHP]int main(int argc, char** argv)
{
    float en =-0.29;
    float conv = 100.0;
    int matrix = int(conv*en); 
    std::cout<<conv*en<<std::endl; //-> -29
    std::cout<<int(conv*en)<<std::endl; //->-28
    std::cout<<matrix<<std::endl; //->-28

   return (EXIT_SUCCESS);
}[/PHP]

try a little test like this on a 32 bit latest ubuntu install and this is what you'll get. However on a 64 bit redhat the int(conv*en) will return -29!

---

### Post by abraxas334 on 2010-08-20
> **dwhitney67 said:**
> 
P.S.  I hope that code example you provided is not representative of your real program.  It is very hard to read code when it lacks vertical white-space.

 -- no this does not reflect my code i do have vertical white spaces  unfortunately the forum does not do automatic indenting etc

Yes I figured out that it is truncating it, but I assume on a 64 bit its still 28.9999.. however many significant figures there are, why does it not round down to -28?
My solution was just to declare.

```
const static float ONE_HUNDRED = 100.1
```
 is this bad?

---

### Post by dwhitney67 on 2010-08-20
> **abraxas334 said:**
> 
My solution was just to declare.

```
const static float ONE_HUNDRED = 100.1
```
 is this bad?
Yes, it is bad.  In the US, we call this a kludge.

You need to understand that a float only has so much precision; you probably will get better results using double as your data type.  Nevertheless, even doubles are prone to inexactitudes.

If you really want to yield the best possible int value, I would suggest that you consider adding +/-0.005 to the floating point value, then multiply by 100.0, and then convert to an int.  For example:
```

const double ONE_HUNDRED = 100.0;

...

int im = ONE_HUNDRED * (ie + (ie < 0 ? -0.005 : 0.005));

```

Btw, you do not need to explicitly cast to an int.  The program will take care of this during runtime.


P.S.  Try setting the precision to 8 before printing this float value; the resulting value will probably not be -29.
```

**std::cout.precision(8);**
std::cout<<conv*en<<std::endl; //-> -29

```

---

### Post by abraxas334 on 2010-08-20
> **dwhitney67 said:**
> Yes, it is bad.  In the US, we call this a kludge.

You need to understand that a float only has so much precision; you probably will get better results using double as your data type.  Nevertheless, even doubles are prone to inexactitudes.

If you really want to yield the best possible int value, I would suggest that you consider adding +/-0.005 to the floating point value, then multiply by 100.0, and then convert to an int.  For example:
```

const double ONE_HUNDRED = 100.0;

...

int im = ONE_HUNDRED * (ie + (ie < 0 ? -0.005 : 0.005));

```

Btw, you do not need to explicitly cast to an int.  The program will take care of this during runtime.

Thank you for taking the time and looking at this. Things are clearer now!

---

### Post by Npl on 2010-08-21
The reason for disparity is that gcc will use the extremely horrible x87 FPU as default if compiling 32bit code. You will get uncontrollable precision issues, only in this case it will likely use more precision.

When compiling 64bit code gcc will use SSE2 for floating point which is more consistent, if you define a float then you will only get float accuracy.

and regarding rounding, C/C++ will truncate. means (int)2.999 will result in 2, you get around that with rounding by adding 0.5 - (int)(2.999 + 0.5).

---

