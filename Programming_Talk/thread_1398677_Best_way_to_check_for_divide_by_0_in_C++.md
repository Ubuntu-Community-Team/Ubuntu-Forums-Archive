---
title: "Best way to check for divide by 0 in C++?"
date: 2010-02-04
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-02-04
If you divide by 0 in C++, the program will crash...at least in gcc.  What's the best way to check for zero before dividing?  Will this work:

double den;

if(den != 0) 

I know this probably sounds like a stupid question (and maybe it is), but I'm thinking that floating point rounding errors might come into play here.  What's the best way to check a denominator for division to avoid getting an exception?

---

### Post by NovaAesa on 2010-02-04
I would go with setting up the logic of the program such that the denominator is never actually zero. If it's user input, that would involve filtering out values that will lead to a denominator being zero. Most algorithms I have come across have divide by zero mapping directly to a case where the input is invalid.

With floating point arithmetic, when comparing two numbers it is best to do it within a certain tolerance. You can obviously change the value of e depending on what precision numbers you are using. Pseudocode:
```

global e = 0.0001;

equal?(a, b) {
  return (|a - b| < e);
}

```

---

### Post by Habbit on 2010-02-04
Actually, *floating point* division by zero does not cause a crash. IEEE754 rules specify that x divided by zero is an appropriately signed infinity. This is so because you can reach a "zero" result with operations that are not meant to produce a mathematical zero, like 1E-300*1E-200 in double precision.

Remember, it's only in integer arithmetic that division by zero is a program-killing error, and in that case a comparison like x == 0 is perfectly fine.

---

### Post by SNYP40A1 on 2010-02-05
You are right, it's only a problem when dividing by 0 using an integer.

---

### Post by Npl on 2010-02-05
> **SNYP40A1 said:**
> You are right, it's only a problem when dividing by 0 using an integer.Nope, not even then, atleast the C Standard doesnt say so.
Depends on the Compiler, Hardware and OS if the program stops or just silently continues with an undefined result.

Conversly, a floating point division **can** cause an exception, but this is defined by the standard and can even be en/disabled AFAIK. and mathematically x/0 is not infinity.. it could be +infinity, -infinity or if x = 0 quite possibly every value in between

---

### Post by Habbit on 2010-02-05
> **Npl said:**
> mathematically x/0 is not infinity.. it could be +infinity, -infinity or if x = 0 quite possibly every value in between

*Mathematically* x/0 is undefined for all x including 0. What *can* be defined is the _limit_ of the quotient f(x)/g(x) as x approaches some value that makes both f and g zero. However, since computers don't understand about such subtle differences, the IEEE754 rules are: (with exceptions disabled):
[LIST]
[*]x/0 -> Appropriately signed infinity (depends on the signs both of x and the zero, since the IEEE754 zero is signed)
[*]0/0 -> NaN
[*]Infinity * 0 -> NaN
[/LIST]

---

### Post by not_a_phd on 2010-02-05
I am a big fan of the following approach:

```

if( fabs(denom) > myEpsilon) {
   result = num/denom;
}
else {
   // Perform Fault Recovery Steps Here
}

```

I set myEpsilon to an appropriately small **const double** value consistent with the application domain. For a generic math library, I will set it to the Machine Epsilon value, which is the largest value that can be added to 1.0 with the result being identically equal to one:  ((1.0 + machEpsilon)==1.0) is **true**. However for a problem pertaining to a physical system, I generally have a feel for what is too small to be real.

---

### Post by c0mput3r_n3rD on 2010-02-06
> **SNYP40A1 said:**
> If you divide by 0 in C++, the program will crash...at least in gcc.  What's the best way to check for zero before dividing?  Will this work:

double den;

if(den != 0) 

I know this probably sounds like a stupid question (and maybe it is), but I'm thinking that floating point rounding errors might come into play here.  What's the best way to check a denominator for division to avoid getting an exception?


What you did is fine; just say   
if(dem != 0)
    /*do dividing*/
else
    /*output some sort of message*/

---

