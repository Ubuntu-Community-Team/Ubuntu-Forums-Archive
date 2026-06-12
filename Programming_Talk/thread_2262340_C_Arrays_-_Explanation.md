---
title: "C Arrays - Explanation?"
date: 2015-01-24
forum: Programming Talk
---

### Post by flaymond on 2015-01-24
Hello, I got stuck in Array subject in C. I don't understand what is it(especially when use for loop with it)? Is there any simple explanation?

Example that I don't understand -

```

#include <stdio.h>
main()
{
    int n[10];
    int i;

    for (i = 0; i < 10; i++) {
        n[i] = 0;
    }                                                      
/* I don't understand why n must assign the i as array? */

    printf("%s%13d\", "Element", "Value");

    for (i = 0; i < 10; i++) {

    printf("%7d%13d\n", i, n[i]);       // Don't understand what happened when i assigned as array?
                                                  // If i is =0; then n[i] is same with n[i] =0?
    return 0;

    
```

Thanks!

---

### Post by Matthew_Harrop on 2015-01-24
You haven't declared n as an array, but as a single variable.

Try:
> 
int main()
{
int i;
int n[10]; /* The [10] is the array length. */

}


---

### Post by flaymond on 2015-01-24
Sorry, I didnt copy with right spelling.

---

### Post by Holger_Gehrke on 2015-01-24
Your example actually doesn't declare n to be an array. It should be 'int n[10];'. An array is a fixed number of variables of the same type put into one "thing". So n[0] is one integer, n[1] is another ... The count for the index (the number in brackets that tells the compiler which element of n you want to access) starts at 0, the number in brackets in the declaration is the length of the array. This is a source of much confusion and a lot of errors by beginning programmers, who expect the first element to have index 1 and the last one to have the index given in the declaration while in truth the index runs from 0 to the declared length -1 (index 0..9 means 10 integers in the example).

---

### Post by flaymond on 2015-01-24
I don't understand if[B] -

[/B]> i = 0;
                then why at the row 7, the n[i] must assign to 0?

[B]

I don't understand
[/B]

---

### Post by steeldriver on 2015-01-24
i=0 sets the value **of i**

n[i] is the i[SUP]th[/SUP] value **of n**

---

### Post by Matthew_Harrop on 2015-01-24
Do you understand it now? Or would you like me to explain it how I think of it? :)

---

### Post by The Cog on 2015-01-24
This declares i to be an integer, and n to be an array of 10 integers.  ```

    int n[10];
    int i;
```
This next bit sets all 10 integers in array n to contain the value 0. It does it by putting the values 0-9 in i (in turn), and using i to index the array (to select which member of the array you are writing the 0 to):
```

    for (i = 0; i < 10; i++) {
        n[i] = 0;

```
It is common to set all the values of an array to 0 before starting the real work. You should **never** use (read) a variable or array copntents until you have written to it, because un-initialised variables contain random values, which can cause real confusion. So initialising everything is very good practice.

---

### Post by flaymond on 2015-01-25
> This declares i to be an integer, and n to be an array of 10 integers.   	Code:
 	    int n[10];This declares i to be an integer, and n to be an array of 10 integers.   	Code:
 	    int n[10];
    int i; 

    int i; 


I can see now

> This next bit sets all 10 integers in array n to contain the value 0. It  does it by putting the values 0-9 in i (in turn), and using i to index  the array (to select which member of the array you are writing the 0  to):
 	Code:
 	    for (i = 0; i < 10; i++) {
        n[i] = 0; 

This is the one I looking for, I can understand a little bit now, but still, I don't get all of it.

> Do you understand it now? Or would you like me to explain it how I think of it? :smile:

I really need an opinion, if you willingly too. :)
I don't understand what is an array and how it's worked.

In the code I posted, I don't understand both of the printf part...

I just stuck-hard at array....

but thanks for helping guys!

---

### Post by sudodus on 2015-01-25
In mathematics there are the concepts of numbers (single numbers like -1, 2014, 3.1416 etc) and vectors and matrices.

A vector has a size and a direction. For example the wind can have the size 10 m/s (in this case a velocity to be correct) and the direction from southeast to northwest. It can be represented with an arrow (with size and direction). It can also be represented with co-ordinates (one component in the north-south direction and one component in the east-west direction). Suppose x points to the east and y points to the north. Then x is approximately -7.071 and y is approximately 7.071.

That wind vector can be represented by ```
(-7.071, 7.071)
``` And an array in C or bash can be used to represent it and use it in calculations, in this case a simple array with only two items.

An array can also represent some alternatives (text items) as in this link [http://www.linuxjournal.com/content/bash-arrays](http://www.linuxjournal.com/content/bash-arrays)

It looks a little different in C and bash (and other languages), but the concept is the same.

A matrix is a two dimensional set of numbers, not only a row or column of numbers but several rows (alias several columns)

```
1 2 5 4
7 3 4 5
6 8 1 9
```

is a matrix with three rows and four columns

it can be represented by a two-dimensional array ```
int twodim[3][4];
```

See this link [http://www.tutorialspoint.com/cprogramming/c_multi_dimensional_arrays.htm](http://www.tutorialspoint.com/cprogramming/c_multi_dimensional_arrays.htm)

---

### Post by The Cog on 2015-01-25
OK, some real basics: I googled "what is a C array", and this page came up on the top of the list. It looks like a good explanation to me: [http://www.tutorialspoint.com/cprogramming/c_arrays.htm](http://www.tutorialspoint.com/cprogramming/c_arrays.htm)

One thing it doesn't point out is that the square brackets have two different meanings depending on the context. 

When you first declare an array, the number in the square brackets is telling the compiler the size of the array - how many items long the list is. This number must be known at compile time as the compiler needs to know how much memory to allocate.

But when you use the array (read or write a value in the array), the number in the square bracket is the index number, specifying which element of the list you are reading or writing. The number can be a calculated number, as is the case in your example where you use i to take on the values 0-9 and write a 0 to each array element in turn by first setting n[0] = 0, then setting n[1] = 0 etc, until finally n[9] = 0. 

It is a horrible error to try to read past either end of the array (using a negative index number or >= the list length). A ten element array contains elements with index numbers 0-9 only. A common beginner mistake is to try to read/write element number 10.

---

### Post by flaymond on 2015-01-25
Woah! I got it now. :D

BIG THANKS to ALL of you guys! :KS:KS:KS:KS:KS:KS

---

### Post by The Cog on 2015-01-25
Excellent! Thanks for the positive feedback - that makes me feel good.

---

### Post by sudodus on 2015-01-26
> **The Cog said:**
> Excellent! Thanks for the positive feedback - that makes me feel good.
+1

---

### Post by lisati on 2015-01-26
> **sudodus said:**
> +1

+2

The languages I started with had a degree of nurse-maiding when it came to arrays, and one was often sheltered from the hazards of going past the end of the valid range of indexes.

---

