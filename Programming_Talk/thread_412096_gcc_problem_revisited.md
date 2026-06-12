---
title: "gcc problem revisited"
date: 2007-04-17
forum: Programming Talk
---

### Post by hollowhead on 2007-04-17
I've come back with my code which I'm now sure is the problem.  Prog compiles but gives a segmenataion fault on running I pasted the hex from gdb into gcalculator and converted it to decimal.  It stated this line was the problem in ttest.c printf("tvalue %f\n", &t); however the hex below is from today and the calculator would not convert it don't know why.  I'm sure I've made some really basic mistake, any help would be appreciated, my c is rusty.  Ta.  Hollowhead.

// gdb output

/*(gdb) run
Starting program: /home/nrh1/code/testt

Program received signal SIGSEGV, Segmentation fault.
0x0804967f in var ()

// function to calculate ttest ttest.c
*/
#include <stdio.h>
#include <math.h>
#include "stats.h"
#define square(x) (x*x)

int main()

{

/* declare arrays of x and y data from statistical methods in cell biology 2nd edition pg 45*/
double a[8]= {3.2,1.6,5.7,2.8,5.5,1.2,6.1,2.9};
double b[8]= {3.8,1.0,8.4,3.6,5.0,3.5,7.3,4.8};
unsigned int na=8;
unsigned int nb=8;
double* t;
double *prob;

ttest( a,  na,  b, nb, &t, &prob); // ?
printf("tvalue %f\n", &t);

printf("tvalue %f\n", &prob);
} // program closing brace

uses part of stats lib stats.c the relevant functions are shown below ftest code is nt mine but works very well I've used it in other contexts

/*
ttest assumes homogenity of variance, uses ftest probability code to calculate probability of the significance of the t statistic

*/


double var(double *data, unsigned int n)
{
unsigned int i;
double average=0.0;
double s, temp, var;

for (i=0; i<n; n++)
average=average+data[n]; // calculate average 

average=average/n;

var=temp=s=0.0; // now variance
for (i=0; i<n; n++)
{
s=data[n]-average;
temp=temp+s;
var=var+(s*s);

}
return (var-temp*temp/n)/(n-1);
} // function closing brace
/* end of function */

void ttest(double *data1, unsigned int n1, double *data2, unsigned int n2, double *tstatistic, double *tprob)
{

double nmean(unsigned int count, double *data); // function declarations within function 
double pof(double F, unsigned int df1, unsigned int df2);
double var(double *data, unsigned int n);
double svar=0.0;
double var1=0.0; 
double var2=0.0; 
double mean1=0.0; 
double mean2=0.0;
double df=0.0;
//double *tstatistic=0.0;
//double *tprob=0.0

mean1=nmean(n1, data1); //calculate means for individual data sets
mean2=nmean(n2, data2);
var1=var(data1, n1);                         //calculate variances for individual data sets
var2=var(data2, n2);
df=n1+n2-2;                                           // calculate overall df
svar=((n1-1)*var1+(n2-1)*var2)/df; // pooled variance
*tstatistic=(mean1-mean2)/sqrt(svar*(1.0/n1+1.0/n2)); // calculate t value
*tprob=pof(((*tstatistic)*(*tstatistic)), 1, df);      //probability
} // function closing brace

/* end of function */


/*FUNCTION pof: probability of F */
/*ALGORITHM Compute probability of F ratio.
   
*/

/*
   example  if F=1.432923 and df1=3 and df2=5 p=0.337564
*/
double pof(double F, unsigned int df1, unsigned int df2)
{

   int	i, j;
   int	a, b;
   double	w, y, z, d, p;

   if (F < F_EPSILON || df1 < 1 || df2 < 1)
      p=1.0;
   else
   {
      a = df1%2 ? 1 : 2;
      b = df2%2 ? 1 : 2;
      w = (F * df1) / df2;

      z = 1.0 / (1.0 + w);
      if (a == 1)
	 if (b == 1)
	 {
	    p = sqrt (w);
	    y = I_PI; /* 1 / 3.14159 */
	    d = y * z / p;
	    p = 2.0 * y * atan (p);
	 }
      else
      {
	 p = sqrt (w * z);
	 d = 0.5 * p * z / w;
      }
      else if (b == 1)
      {
	 p = sqrt (z);
	 d = 0.5 * z * p;
	 p = 1.0 - p;
      }
      else
      {
	 d = z * z;
	 p = w * z;
      }
      y = 2.0 * w / z;

      for (j = b + 2; j <= df2; j += 2)
      {
	 d *= (1.0 + a / (j - 2.0)) * z;
	 p = (a == 1 ? p + d * y / (j - 1.0) : (p + w) * z);
      }

      y = w * z;
      z = 2.0 / z;
      b = df2 - 2;
      for (i = a + 2; i <= df1; i += 2)
      {
	 j = i + b;
	 d *= y * j / (i - 2.0);
	 p -= z * d / j;
      }
/* correction for approximation errors suggested in certification */
      if (p < 0.0)
	 p = 0.0;
      else if (p > 1.0)
	 p = 1.0;
      p= (1.0-p);
      return p;
   }
   return p;
}

---

### Post by Damaniel on 2007-04-17
In this line:

[FONT="Courier New"]ttest( a, na, b, nb, &t, &prob); // ?[/FONT]

the ttest function expects the last two arguments to be pointers to double, and you're passing in the address of a pointer to double (a pointer to a pointer to a double).  You'll want to make 't' and 'prob' doubles instead of pointers to double.  

You have a similar problem with the printf calls.  Assuming you want to print out the values and not the address of the pointers, you'll want to change the calls.

When you make  't' and 'prob' type double (instead of 'double *'), the printfs will look like:
[FONT="Courier New"]printf("tvalue %f\n", t);[/FONT]
[FONT="Courier New"]printf("tvalue %f\n", prob);[/FONT]

---

### Post by dsl on 2007-04-17
Sorry I have no time nor (frankly) wish to follow your code in detail, so I limit myself to the first thing catching my eye.

ttest is declared as
```

void ttest(double *data1, unsigned int n1, double *data2, unsigned int n2, double *tstatistic, double *tprob)

```

but you call it so:
```

ttest( a, na, b, nb, &t, &prob); // ?

```

being:
```

double* t;
double *prob;

```

so really last two arguments are passed as double**, not double*.

HTH

---

### Post by hollowhead on 2007-04-18
thanks for your replies.  I don't blame you for not going through all the code but I was criticised for not posting any .....  Also you are right the error is in these lines of code.  

I'm afraid I don't completely understand your answers. I  tried what I take to be your suggestions.  First I passed the test( a, na, b, nb, &t, &prob); // ? as test( a, na, b, nb, t, prob); // ? having declared t and prob merely as doubles,  I get an incompatable type error from gcc which makes sense cause in the function ttest they are pointers since I want to return two values from the function.  Second I replaced t, and prob with **t etc and theircounterparts in the function. This compiles but gives a segmenatation fault slightly different to last time in gdb 0x08049687 in var ().  I'm really sorry to be so thick but could you guys or someone else have another go at explaining where I'm going wrong?!

Ta.

---

### Post by dsl on 2007-04-18
Everything depends on what you want to do. If you need to pass a pointer to double to the function, then declare it as a pointer to double:

```

double * my_pointer_to_double;

```

then just pass it to the function as it is: it is already a pointer to double, no need to take its address (which would be a pointer to pointer to double):

```

void my_function (double * pointer_to_double);
...
my_function (my_pointer_to_double);

```

If the pointer to double is the address of an array of doubles, the name of the array stands for the address of its first element, so you could write:

```

double my_array_of_doubles [MANY_OF_THEM];
...
my_function (my_array_of_doubles);

```

as well as:

```

my_function (&my_array_of_doubles[0]);

```

or even:

```

my_pointer_to_double = &my_array_of_doubles[0];
my_function (my_pointer_to_double);

```

Don't worry, it's like driving. Once you learn it you won't forget it any more.

HTH

---

### Post by hollowhead on 2007-04-18
Thanks I'll think about it.  Not like driving though you forget this stuff.

---

### Post by Damaniel on 2007-04-18
> **dsl said:**
> Everything depends on what you want to do. If you need to pass a pointer to double to the function, then declare it as a pointer to double:

```

double * my_pointer_to_double;

```

then just pass it to the function as it is: it is already a pointer to double, no need to take its address (which would be a pointer to pointer to double):

```

void my_function (double * pointer_to_double);
...
my_function (my_pointer_to_double);

```


In hollowhead's particular example, the function that main() calls doesn't actually do any allocation of memory with the passed in pointer, so defining a 'double *' in main and passing it to 'ttest' would cause that function to write the double to whatever the pointer currently points to (almost certainly junk).  In this case, since 't' and 'prob' have been changed to doubles,  the call to ttest() should be written as follows:

```
ttest( a, na, b, nb, &t, &prob);
```

and the calls to printf() as follows:

```
printf("tvalue %f\n", t);
printf("tvalue %f\n", prob);
```

The entire contents of main() would be:

```
int main()
{

    /* declare arrays of x and y data from statistical methods in cell biology 2nd edition pg 45*/
    double a[8]= {3.2,1.6,5.7,2.8,5.5,1.2,6.1,2.9};
    double b[8]= {3.8,1.0,8.4,3.6,5.0,3.5,7.3,4.8};
    unsigned int na=8;  
    unsigned int nb=8;
    double  t;
    double  prob;

    ttest( a, na, b, nb, &t, &prob);
    printf("tvalue %f\n", t);
    printf("tvalue %f\n", prob);

} 
```

Pointers are very tricky to fully understand, but eventually you'll just 'get' them and you'll have no problems with them.  It took me a long time to get to that point -- especially in the case of pointers to pointers! ;)

---

