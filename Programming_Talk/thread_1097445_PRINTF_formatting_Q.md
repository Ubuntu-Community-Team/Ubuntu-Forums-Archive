---
title: "PRINTF formatting Q:"
date: 2009-03-16
forum: Programming Talk
---

### Post by Krupski on 2009-03-16
Hi all,

I just ran into something that *I* think is strange... maybe someone could shed some light on what's going on.

If I do something like this:

```

    double n = 1e-9; // note: small number
    printf("The number is %f\n", n);

```

...it outputs "The number is 0.000000" which is WRONG!

Now, if I force the matter like this:

```

    double n = 1e-9;
    printf("The number is %.20f\n", n);

```

...then it prints the proper number (albeit with lots of trailing zeros).

If I print a large POSITIVE number, the output grows accordingly without any changes to the format string. For example:

```

    double n = 1e12; // note: large number
    printf("The number is %f\n", n);

```

...properly prints "The number is 1000000000000.000000".

Is this normal? Why does the %f format "arbitrarily" choose to output 6 digits after the decimal point, yet "grow" as needed to display digits before the decimal point?


Thanks!

-- Roger

---

### Post by croto on 2009-03-16
The %f format defaults to 6 decimal places if precision is not specified. You may use the %g specifier, which chooses between %f or %e as appropriate. Check the man page (man 3 printf) or this webpage for reference [http://www.pixelbeat.org/programming/gcc/format_specs.html]("http://www.pixelbeat.org/programming/gcc/format_specs.html")

---

### Post by croto on 2009-03-16
It may look strange that the default behavior isn't printing "all" decimal places. The problem is that the meaning of "all" decimal places is not well defined. In particular, the issue is that the float and double types are stored in "binary floating point" representation [http://en.wikipedia.org/wiki/IEEE_754-2008]("http://en.wikipedia.org/wiki/IEEE_754-2008"). In this representation, most numbers that have a "small" decimal representation cannot be exactly represented. For example, run the following code:
```

#include <stdio.h>

int main(){
  printf("1.3=%.60f\n",1.3);
  printf("0.3=%.60f\n",0.3);
  return 0;
}

```

The end result is that it is not really clear when to "stop" printing decimal places (and that problem does not occur with the integer part). Then, the standard does not attempt to guess how many decimal places you want at all.

---

### Post by sujoy on 2009-03-16
and quite obviously it had to chose to limit the places after decimal, otherwise if you tried to print PI or any recurring number, the universe would explode ;)

---

### Post by Sockerdrickan on 2009-03-16
double is lf I believe

---

### Post by Krupski on 2009-03-16
Thank you all for the info!

I never thought about what would happen if "printf" automatically printed all of the numbers past the decimal point... and the number was an irrational number (like PI) !!!

It all makes sense now. Thanks again!

-- Roger

---

### Post by Krupski on 2009-03-16
> **Tux0r said:**
> double is lf I believe
"Lf" I think (large L).

---

### Post by Sockerdrickan on 2009-03-16
no

---

### Post by dwhitney67 on 2009-03-16
> **Tux0r said:**
> double is lf I believe

+1.

A double is a long float.

---

