---
title: "help with C++"
date: 2012-09-17
forum: Programming Talk
---

### Post by Jsegovia on 2012-09-17
im writing a program that checks the Euro Article Number and so far my program will not calculate the remainder keeps tellign me im taking int from a double....can someone explain and help me with my source code?
 
char EAN [13];
int sum1, sum2, sum3, sum4, i_sum5, sum6, i_digit;
double d_sum5;
 
sum1 = (EAN[1]-48 )+(EAN[3]-48 )+(EAN[5]-48 )+(EAN[7]-48 )+(EAN[9]-48 )+(EAN[11]-48 ); 
 
sum2 = (EAN[0]-48 )+(EAN[2]-48 )+(EAN[4]-48 )+(EAN[6]-48 )+(EAN[8]-48 )+(EAN[10]-48 );
 
sum3 = (sum1*3)+sum2;
 
sum4 = sum3-1;
 
i_sum5 = static_cast<int>(d_sum5);
d_sum5 = (sum4/10)%10;
 
sum6 = 9-d_sum5; 
sum6 = i_digit;

---

### Post by Vaphell on 2012-09-17
How the algorithm goes from sum4 to X_sum5? i don't see any continuity.
Why use double at all? from what i see it's all integer arithmetic of small numbers.

---

### Post by trent.josephsen on 2012-09-17
Not a C++ guru and I know nothing about EANs, but

```
i_sum5 = static_cast<int>(d_sum5);
```

raises flags because d_sum5 hasn't been initialized yet. What do you expect this line of code to do?

Why is d_sum5 a double in the first place? (sum4/10)%10 is always an int.

And sum6 = i_digit; is again undefined because i_digit is uninitialized.

---

### Post by gnometorule on 2012-09-17
Strike
```

i_sum5 = static_cast<int>(d_sum5);
d_sum5 = (sum4/10)%10;

```Set
```

i_sum5 = (sum4/10)%10;
d_sum5 = static_cast<double>(i_sum5);

```This will get the remainder, as a double, into d_sum5. The code looks still supremely strange, e.g., for any positive integer x, and using / and % in the usual way for integer division,

[HTML]
(x/10)%10
[/HTML]creates a partioning of the positive integers into 10 equivalence classes of size 10 each, which may or may not be what you're trying to do.

---

### Post by Vaphell on 2012-09-17
i looked at wiki
ean-13 is 12+1 code, where odd positions have weight=1 and even positions have weight=3
adding up first 12 digit*weight, 13th digit should be equal x where (x+sum)%10=0

---

### Post by Jsegovia on 2012-09-17
thanks for the help i didnt need a double was just lil lost in my thought....Figured it out with the help of yalls post thanks tons.

---

