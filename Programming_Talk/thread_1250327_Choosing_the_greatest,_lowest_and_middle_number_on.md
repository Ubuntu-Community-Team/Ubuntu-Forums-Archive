---
title: "Choosing the greatest, lowest and middle number only with if/else"
date: 2009-08-26
forum: Programming Talk
---

### Post by Vichfret on 2009-08-26
I made this program in C, as you may see I used a if for each case, my question is, is there a way to make this program in less lines using only if/else?

```

#include <stdio.h>
#include <stdlib.h>

main() {
    int a, b, c;

    system("clear");    // no windows allowed :P

    printf("Introduce un número: \n");    // enter a number
    scanf("%d", &a);
    printf("Introduce un número: \n");
    scanf("%d", &b);
    printf("Introduce un número: \n");
    scanf("%d", &c);

    if(a == b || a == c || b == c) {
        if(a == b && a == c && b == c)
            printf("Los tres números son iguales\n");    // the three numbers are equal
        else{
            if(a == b)
                if (a > c)
                    printf("%d es el mayor y %d es el menor\n", a, c);    // x is the greatest and y is the lowest
                else
                    printf("%d es el mayor y %d es el menor\n", c, a);
            if(a == c)
                if(a > b)
                    printf("%d es el mayor y %d es el menor\n", a, b);
                else
                    printf("%d es el mayor y %d es el menor\n", b, a);
            if(b == c)
                if(b > a)
                    printf("%d es el mayor y %d es el menor\n", b, a);
                else
                    printf("%d es el mayor y %d es el menor\n", a, b);        
            }
        }

    else {
        if(a > b && a > c) 
            if(b > c)
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", a, b, c); // the greatest number is x, the middle is y and the lowest is z
            else
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", a, c, b);
        if(b > a && b > c) 
            if(a > c)
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", b, a, c);
            else
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", b, c, a);
        if(c > a && c > b) 
            if(a > b) 
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", c, a, b);
            else
                printf("El numero mayor es %d, el de en medio es %d y el menor es %d \n", c, b, a);
        }

    return 0;
}


```

---

### Post by Mark20 on 2009-08-26
Try this link:

[http://www.neowin.net/forum/lofiversion/index.php/t399541.html]("http://www.neowin.net/forum/lofiversion/index.php/t399541.html")

---

### Post by uljanow on 2009-08-26
```
if a <= b:
	if b <= c:
		print "a, b, c"
	elif a <= c:
		print "a, c, b"
	else:
		print "c, a, b"
elif a <= c:
	print "b, a, c"
elif b <= c:
	print "b, c, a"
else:
	print "c, b, a"

```

---

### Post by Tony Flury on 2009-08-26
with conditional operators :

```

#define GetMax(a,b) ((a) > (b) ? (a) : (b))
#define GetMax3(a,b,c) (max((a), max((b),(c))))
...
...
...

max = max3(x,y,z) ; 
min = -(max3(-x,-y,-z)) : 
...
...
...

```

The notice the min uses the max Macro deliberately - it is not a typo.

if you think about two numbers - say 99 and 1000 - clearly 1000 is bigger. now if you take the negative -99 and -1000 - clearly -99 is bigger which means that 99 (positive) must be the smaller of the two original numbers. It even works if the original numbers are a mix of postive and negative numbers.

You could of course define GetMax3 and GetMax as functions. 

this wont satisfy the OP - who wanted only if/else - but that sounded like a home work problem anyway.

---

### Post by Vichfret on 2009-08-26
Nice, I only wanted to do my program different to my classmates' and I though I could do better with my logic since a if for each case doesn't sound like a good program

---

### Post by Reiger on 2009-08-26
Gah. This reminds me: given a function that chooses the largest can you use that function (and that function only apart from common numerical operations) to find the smallest?

The answer is yes. And the answer to that problem, for a 3 tuple also yields the answer to your problem. It is surprisingly elegant:

In Haskell:
```

module TupleTest where

sort3Tuple (a,b,c) = (h,m,l) -- return (highest, middle, lowest)
                   where
                   vals = [a,b,c] -- prepare values as a list
		   lMax = foldl max -- function to get the max out of a list and base-case value using a fold
		   h = lMax a vals -- get the maximum of the values in the tuple
		   inv = ((-1) *) -- inverter/negation function
		   l = inv (lMax (inv a) (map inv vals) ) -- get the minimum of the values in the tuple using the Max: this is done by negating values
                   m = (sum vals) - h - l -- get the remainder of substracting both maximum and minimum from the sum of all values in the tuple (== the remaining value not yet found)

```

---

### Post by Lux Perpetua on 2009-08-26
Yet another way: ```
int t;

if (b < a) t = a, a = b, b = t;
if (c < b) t = b, b = c, c = t;
if (b < a) t = a, a = b, b = t;

printf("%d, %d, %d\n", a, b, c);
```(untested, so bugs may reside, but hopefully the concept is clear).

---

