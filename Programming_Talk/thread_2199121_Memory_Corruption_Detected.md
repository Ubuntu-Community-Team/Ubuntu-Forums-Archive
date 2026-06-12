---
title: "Memory Corruption Detected"
date: 2014-01-12
forum: Programming Talk
---

### Post by Vesnog on 2014-01-12
Greetings everyone, 

I am running a code including some routines from "Numerical Recipes" and define arrays consisting of a large number of elements by malloc. The below code compiles successfully without any error; however upon execution I ran into the problem of memory corruption detected by glibc. How can I remedy this situation it is really frustrating and I cannot see where the error resides. I would be grateful if someone can point it out. 

Thanks in advance

The error message:
```
 *** glibc detected *** ./Q3: malloc(): memory corruption (fast): 0x09ced278 ***
```
The actual code:

```
// The compilation command used is given below
// gcc Q3.c nrutil.c DFRIDR.c -lm -o Q3


#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include "nr.h"


#define LIM1 20.0
#define a -5.0
#define b 5.0
#define pre 100.0 // This defines the pre
/* This file calculates the func at given points, makes a 
 * plot. It also calculates the maximum and minimum of the func
 * at given points and its first and second numerical derivative.
*/
float func(float x)
{
    return exp(x / 2) / pow(x, 2);
}


int main(void)
{
    FILE *fp = fopen("Q3data.dat", "w+"), *fp2 = fopen("Q3results.dat", "w+");
    int i; // Declaring our loop variable
    float min, max, err, nd1, nd2, x, y;
    //These arrays are defined so that we can pass them into Numerical Recipes routines
    float * xp = malloc(((b - a) * pre + 10)* sizeof(float));
    float * yp = malloc(((b - a) * pre + 10)* sizeof(float));
    if (xp == 0 || yp == 0 )
        {
            printf("ERROR: Out of memory\n");
            return 1;
        }
    float yp1 = dfridr(func, a, 0.1, &err), ypn = dfridr(func, b, 0.1, &err);
    // Define the initial value of the func to be the minimum
    min = func(0); 
    for(i = 0; x < LIM1 ; i++)
    {    
        x = i / pre; // There is a singularity at x = 0 
        y = func(x);
        if(y < min)
            min = y;
        fprintf(fp, "%f \t %f \n", x, y);
    }
    fprintf(fp, "\n\n");
    max = 0;
    x = a;
    //for(i = 0; x < b; i++)
    //{    
        //x = a + i / pre;
        //y = func(x);
        //nd1 = dfridr(func, x, 0.1, &err); 
        //fprintf(fp, "%f \t %f \t %f \t \n", x, y, nd1);
        //if(y > max)
            //max = y;
    //}
    for(i = 0; xp[i] < b ; i++)
    {    
        xp[i] = a + i / pre;
        yp[i] = func(xp[i]);
        nd1 = dfridr(func, xp[i], 0.1, &err); 
        fprintf(fp, "%f \t %f \t %f \t \n", xp[i], yp[i], nd1);
        if(yp[i] > max)
            max = yp[i];
    }
    free((void *)xp);
    free((void *)yp);
    fprintf(fp2, "The minimum value of f(x) is %f when x is between 0 and 20. \n", min);
    fprintf(fp2, "The maximum value of f(x) is %f when x is between -5 and 5. \n", max);
    fclose(fp);
    fclose(fp2);
    return 0;
}

```

---

### Post by ofnuts on 2014-01-12
When you run this: **[FONT=lucida console]"for(i = 0; xp[i] < b ; i++)"[/FONT]**, the xp[] elements haven't been initialized yet, so **[FONT=lucida console]xp[i] < b [/FONT]**can be anything. If the **[FONT=lucida console]xp[][/FONT]** values are 0, the loop can run more times than the length of **[FONT=lucida console]xp[][/FONT]**. I would assume that it stops when it hits some non-zero value in a memory allocation control blocks, which it overwrites at the next instruction, causing the error your get. 

If "pre" is the reciprocal of a precision, the total number of elements in your array is **[FONT=lucida console]((b-a)*pre)+1[/FONT]** (not +10).

And it would be a good idea to compute that number of elements once, and use it:

1) in a print statement for you debugging purrposes
2) while allocating **[FONT=lucida console]xp[/FONT]**.and **y[FONT=lucida console]p[/FONT]**
3) as a limit in for loops over **[FONT=lucida console]xp[/FONT]**.and **y[FONT=lucida console]p[/FONT]**.

Also, you seem to have a good case of using  a:

```
struct point {
  float x;
  float y;
}
```

And use an array of structs instead of two parallel arrays that share an index.

---

