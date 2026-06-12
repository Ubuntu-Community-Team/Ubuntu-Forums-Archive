---
title: "Follow-up to working with polynomials in C"
date: 2011-05-01
forum: Programming Talk
---

### Post by VonFuzzball on 2011-05-01
So, I figured out how to use Horner's rule to evaluate a polynomial in C. Well, now a follow-up question is to generalize that solution to write a program that prompts the user for a positive integer, n, and a floating-point number, x. It should evaluate the nth order polynomial:

a(sub x)x^n + a(sub x-1)x^n+1 +...+ a(sub 1)x + a(sub 0)

The problem also says that, "After reading n and x, your program should read the n + 1 coefficients a(sub i) in order from a(sub n) to a(sub 0)."

I feel silly, but I have no idea how to do this.

```
#include <stdio.h>
#include <math.h>

int main (void)
{
    double x, a, b, c, d, e, f, p, p2; 
    
printf("Enter the value of x:");
scanf("%lf", &x);

printf("Enter the value of the coefficient, a:");
scanf("%lf", &a);

printf("Enter the value of the coefficient, b:");
scanf("%lf", &b);

printf("Enter the value of the coefficient, c:");
scanf("%lf", &c);

printf("Enter the value of the coefficient, d:");
scanf("%lf", &d);

printf("Enter the value of the coefficient, e:");
scanf("%lf", &e);

printf("Enter the value of the coefficient, f:");
scanf("%lf", &f);

p = a*(pow(x,5)) + b*(pow(x,4)) + c*(pow(x,3)) + d*(pow(x,2)) + e*x + f;
printf("p = %lf", p);

    p2 = (f + x)*((e + x)*((d + x)*(c + x)*(b + x*a)));
printf("\np2 = %lf", p2);
}
```Here is my working code that it refers to at the beginning of the problem. How would I modify this to do what it says above? Any help would be appreciated.

---

### Post by Some Penguin on 2011-05-01
Read *n*, allocate an array of the appropriate size (n+1 slots), and populate it.

---

### Post by Phenax on 2011-05-01
Not totally related to your question, but just use %f for printing doubles in C. %lf for scanning is correct, though. Printing %lf wasn't defined until C99. In variable-length argument functions floats are promoted to doubles thus %f is sufficient. You could run into some problems printing a double with %lf with non-C99 compliant compilers, or compilers like MingW if you don't specifically tell it to compile with C99 mode.

---

### Post by heyandy889 on 2011-05-05
```
Script started on Thu 05 May 2011 03:41:58 PM EDT
** nate@NewBlue:~/Desktop$ gcc -Wall readcoeff.c **
** nate@NewBlue:~/Desktop$ ./a.out  **
Enter the value of n: 3 
Enter the value of the coeff[0]: 1 
Enter the value of the coeff[1]: 0 
Enter the value of the coeff[2]: -99 
Enter the value of the coeff[3]: -99 
 
my polynomial 
  1x^3 
+ 0x^2 
+ -99x^1 
+ -99x^0 
** nate@NewBlue:~/Desktop$ cat readcoeff.c **
/* 
 * ---------------------------------------------------------------------- 
 * readcoeff.c 
 * Nate Shiff 
 * May 5, 2011 
 * program reads an int n. Then, the program 
 * reads "n" integer coefficients 
 * and prints out the polynomial in the form 
 * ax^n + bx^n-1 + ... + yx^1 + zx^0 
 * ---------------------------------------------------------------------- 
 */ 
#include <stdio.h> 
#include <stdlib.h>            //for malloc() 
int main (void) 
{ 
    int     i;            //loop counter 
    int     n;            //number of terms in our polynomial 
    int     *coeff;            //pointer to an empty array of integers 
 
    printf("Enter the value of n: "); 
    scanf("%d", &n); 
    if(n<1){ 
        printf("Oops! Please enter a positive value for n.\n"); 
        return -1; 
    } 
 
    coeff=malloc(n*sizeof(int));             //request memory for "n" integers 
    if(coeff==NULL){ 
        printf("Oops! malloc() error\n"); 
        return -1; 
    } 
 
    for(i=0;i<n+1;i++){                 //loop n+1 times 
        printf("Enter the value of the coeff[%d]: ",i); 
        scanf("%d", &coeff[i]); 
    } 
 
    printf("\nmy polynomial\n"); 
    printf("  %dx^%d\n",coeff[0],n);        //print 1st term 
    for(i=1;i<n+1;i++){                //loop through other terms 
        printf("+ %dx",coeff[i]);        //print coeff 
        printf("^%d",n-i);            //print exponent 
        printf("\n"); 
    } 
    return 0; 
}//end main() 
//----------------------------------------------------------------------- 
** nate@NewBlue:~/Desktop$ exit **
exit 

Script done on Thu 05 May 2011 03:42:33 PM EDT
```

---

